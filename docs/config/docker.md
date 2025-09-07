# docker

## docker pull proxy

要为 `docker pull` 设置代理（解决拉取镜像时的网络问题），需配置 **Docker 守护进程的代理**。以下是具体步骤：

---

### 🐳 配置 Docker 守护进程代理（适用于 `docker pull`）

当 Docker 守护进程需要通过代理访问外网（如 Docker Hub）时：

1. **创建代理配置文件**  

   ```bash
   sudo mkdir -p /etc/systemd/system/docker.service.d
   sudo nano /etc/systemd/system/docker.service.d/proxy.conf
   ```

2. **写入代理配置**（替换为你的代理地址）  

   ```ini
   [Service]
   # HTTP/HTTPS 代理
   Environment="HTTP_PROXY=http://proxy.example.com:8080"
   Environment="HTTPS_PROXY=http://proxy.example.com:8080"
   
   # 排除代理的内网地址/域名（重要！）
   Environment="NO_PROXY=localhost,127.0.0.1,::1,10.*,*.your-company.com,docker-registry.example.com"
   ```

   - 🔑 若代理需要认证：`http://用户名:密码@proxy.example.com:8080`
   - 🌐 `NO_PROXY` 需排除内网地址（如 Kubernetes、私有仓库），避免代理干扰

3. **重启 Docker 服务生效**  

   ```bash
   sudo systemctl daemon-reload         # 重新加载配置
   sudo systemctl restart docker        # 重启 Docker
   ```

4. **验证代理是否生效**  

   ```bash
   systemctl show docker --property Environment | grep PROXY
   ```

   输出应显示你设置的代理变量：

   ```
   Environment=HTTP_PROXY=http://proxy.example.com:8080 HTTPS_PROXY=... NO_PROXY=...
   ```

---

### 🔍 验证代理工作状态

运行测试拉取命令：

```bash
docker pull hello-world
```

- ✅ 成功：正常下载镜像
- ❌ 失败：检查代理地址是否可达，或查看日志：

  ```bash
  journalctl -u docker.service -f  # 实时查看 Docker 日志
  ```

---

### ⚠️ 特殊场景处理

1. **Docker Desktop (Windows/Mac)**  
   通过 GUI 设置：
   - 右键 Docker 图标 → Settings → Resources → Proxies
   - 填入 `HTTP/HTTPS Proxy` 和 `Bypass domains`（等效于 `NO_PROXY`）

2. **临时测试（不修改服务配置）**  
   直接为 `docker` 命令设置环境变量：

   ```bash
   sudo HTTP_PROXY=http://proxy:8080 HTTPS_PROXY=http://proxy:8080 docker pull nginx
   ```

---

### 📌 关键点总结

| 问题类型               | 解决方案                           |
|------------------------|----------------------------------|
| **`docker pull` 拉镜像** | 修改 Docker 守护进程配置（`systemd`） |
| **容器内网络代理**       | 使用 `-e` 环境变量启动容器          |
| **代理需要认证**        | 在 URL 中包含 `user:password@`     |
| **内网资源直连**        | `NO_PROXY` 排除相关 IP/域名        |

> 💡 90% 的代理问题源于 `NO_PROXY` 配置不当（如漏掉内网地址），请仔细检查！

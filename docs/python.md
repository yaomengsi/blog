# python

## pip

```ini
; cat ~/.config/pip/pip.conf
[global]
index-url = https://mirrors.aliyun.com/pypi/simple
; extra-index-url = http://mirrors.cloud.tencent.com/pypi/simple
;                 https://mirrors.tuna.tsinghua.edu.cn/simple
;                 http://pypi.douban.com/simple
;                 https://pypi.org/simple
;                 https://mirrors.aliyun.com/pypi/simple
trusted-host = pypi.org
                files.pythonhosted.org
                pypi.python.org
                mirrors.tuna.tsinghua.edu.cn
                mirrors.aliyun.com
                mirrors.cloud.tencent.com
                pypi.douban.com
```

`cat ~/.config/uv/uv.toml`

```toml
[[tool.uv.index]]
name = 'aliyun'
url = "https://mirrors.aliyun.com/pypi/simple/"
default = true

[[tool.uv.index]]
name = 'tencent'
url = "http://mirrors.cloud.tencent.com/pypi/simple"

[[tool.uv.index]]
name = 'tsinghua'
url = "https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple"

[[tool.uv.index]]
name = 'douban'
url = "http://pypi.douban.com/simple"

[[tool.uv.index]]
name = 'ustc'
url = "https://pypi.mirrors.ustc.edu.cn/simple/"

[[tool.uv.index]]
name = "pypi"
url = "https://pypi.org/simple"
```

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
[[index]]
url = "https://mirrors.aliyun.com/pypi/simple/"
default = true

[[index]]
name = 'aliyun'
url = "https://mirrors.aliyun.com/pypi/simple/"

[[index]]
name = 'tencent'
url = "http://mirrors.cloud.tencent.com/pypi/simple"

[[index]]
name = 'tsinghua'
url = "https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple"

[[index]]
name = 'douban'
url = "http://pypi.douban.com/simple"

[[index]]
name = 'ustc'
url = "https://pypi.mirrors.ustc.edu.cn/simple/"

[[index]]
name = "pypi"
url = "https://pypi.org/simple"
```

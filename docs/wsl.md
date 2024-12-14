# wsl

## wsl proxy to host ip:port

```sh
host_ip=$(ip route show | grep -i default | awk '{ print $3}')
wsl_ip=$(hostname -I | awk '{print $1}')
echo "host ip:" ${host_ip}
echo "wsl ip:" ${wsl_ip}

port=7897
proxy_http="http://${host_ip}:${port}"

export http_proxy="${proxy_http}"
export HTTP_PROXY="${proxy_http}"
export https_proxy="${proxy_http}"
export HTTPS_PROXY="${proxy_http}"
export all_proxy="${proxy_http}"
export ALL_PROXY="${proxy_http}"
echo "proxy:" ${proxy_http}
```

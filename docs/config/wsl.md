# wsl

## wsl proxy to host ip:port

```sh
# for wsl ip
export HOST_IP="$(ip route show | grep -i default | awk '{ print $3}')"
export WSL_IP="$(hostname -I | awk '{print $1}')"
export ARCH_IP="$(wsl.exe -d Arch ip addr show eth0 | grep "inet " | awk '{print $2}'  | cut -d '/' -f1)"
export FEDORA_IP="$(wsl.exe -d Fedora ip addr show eth0 | grep "inet " | awk '{print $2}'  | cut -d '/' -f1)"

```

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

`cat /etc/fonts/local.conf`

```xml
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <dir>/mnt/c/Windows/Fonts</dir>
    <dir>/mnt/c/Users/m/AppData/Local/Microsoft/Windows/Fonts</dir>
</fontconfig>
```

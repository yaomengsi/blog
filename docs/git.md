# git

```sh
# cat ~/.ssh/config
Host github.com
  Hostname ssh.github.com
  Prot 443
  User git
  IdentityFile ~/.ssh/id_rsa
  # ProxyCommand nc -v -x `ip route show | grep -i default | awk '{ print $3}'`:7897 %h %p
  ProxyCommand connect -H `ip route show | grep -i default | awk '{ print $3}'`:7897 %h %p

```

```sh
# git config --global http.https://github.com.proxy http://`ip route show | grep -i default | awk '{ print $3}'`:7897
# cat ~/.githconfig
[http "https://github.com"]
  proxy = socks5://127.0.0.1:1086
```


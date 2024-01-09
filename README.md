本脚本目标在仅ipv6的系统上搭建naiveproxy，并且提供ipv4+ipv6双栈访问能力，目前在wap.ac的debian11测试通过
# 功能介绍
- proxychains4 的socks5端口为9090
- 使用过程中有4个参数，域名，用户名，密码，申请证书时的邮箱
- 使用xray进行分流，IPv4走warp出口，IPv6直连
- 流量路径。你的本地流量到服务器的caddy，caddy配置socks5转出到本地的8080端口，xray入口为socks5类型的8080端口，出口为socks5类型9090。同时根据IP地址类型进行分流，IPv6流量直接出，IPv4流量通过9090端口出到warp，warp监听9090。

# 部署

```
apt update && apt install -y curl && bash <(curl -Ls https://raw.githubusercontent.com/U201413497/v6naiveproxy/main/v4.sh)
```

特别感谢各位大佬的命令，本脚本仅将其做整合

# Home Assistant Add-on: HassBox 远程访问

## 申请 Token

先从 `HassBox 全屋智能` 微信公众号获取远程访问地址和密钥 Token。

## 使用方式

使用前，请确保满足以下条件：

1. 本地网络需支持 IPv6，且设备能获取到公网 IPv6 地址。具体可查看 [开启 IPv6 网络访问](https://hassbox.cn/service/remote-access/ipv6-supported.html)

2. 在配置文件`configuration.yaml`中，如果`http`中有相关 ssl 的配置，请先移除，比如：

- `ssl_certificate`
- `ssl_key`
- `server_port`

3. 在配置文件`configuration.yaml`中，添加如下配置： (如果未添加配置，来自远程访问的请求将被阻止)

```yaml
http:
  use_x_forwarded_for: true
  trusted_proxies:
    - 172.30.33.0/24
```

完成上述配置后，将对应的密钥 Token 复制填入 配置页-选项-token 中，如果修改了默认的远程访问端口号 8124，请将 配置页-网络-开放的端口 修改为对应端口号。

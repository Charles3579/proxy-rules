# 个人自用的直连与规则

建立本仓库的起因是因为 Passwall 仓库的一个 Issue https://github.com/xiaorouji/openwrt-passwall/issues/3708

大致情况就是：
如果将 “cn” 加入 Passwall 的直连列表，如果某一以 ".cn" 结尾的域名解析到 Cloudflare，解析到的 IP 会被写入到防火墙 chnroute 表中，导致后续发往这个 IP 的请求都会被直连，直到清空 IPSET/NFTSET，或 2 天后自动失效。

举例域名：www.dynadot.cn ，它目前解析到了 172.66.43.87/172.66.40.169/188.114.97.3/188.114.96.3 ，如果后续的域名也解析到了这些 IP，请求将被直连。

个人建议在 Passwall 的直连列表中删除 "cn"，并在规则中加入常见的以 ".cn" 结尾的域名，然后配合 ChinaDNS-NG 使用，并确保 ChinaDNS-NG 的 `default-tag` 是 `none`，大多数情况下不会有异常。

本仓库收集了一些大厂的以 ".cn" 结尾的域名，可以在“规则管理”-“中国域名列表更新 URL”中加入本仓库 release 分支的 URL。

### 规则说明
`direct-domain.txt`: 大厂常见的以 ".cn" 结尾的域名列表，以及部分需要直连的服务（包括 Apple、Microsoft）。

`proxy-domain.txt`: 个人自用的需要代理的域名列表。

### 获取规则
#### Github:

https://raw.githubusercontent.com/Charles3579/proxy-rules/refs/heads/release/direct-domain.txt

https://raw.githubusercontent.com/Charles3579/proxy-rules/refs/heads/release/proxy-domain.txt

#### jsDelivr Cloudflare CDN:

https://cdn.jsdelivr.net/gh/Charles3579/proxy-rules@release/direct-domain.txt

https://cdn.jsdelivr.net/gh/Charles3579/proxy-rules@release/proxy-domain.txt

#### jsDelivr Fastly CDN:

https://fastly.jsdelivr.net/gh/Charles3579/proxy-rules@release/direct-domain.txt

https://fastly.jsdelivr.net/gh/Charles3579/proxy-rules@release/proxy-domain.txt

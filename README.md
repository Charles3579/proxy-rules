# proxy-rules

部分 "cn" 后缀的域名解析并不在国内，可能解析到 Cloudflare CDN，由于 Passwall 会将 chn 域名的解析结果写入 passwall_chn，可能会导致后续的连接异常，因此删除直连列表中的 "cn" 规则，并收集一些常见的 "cn" 后缀域名加入 chn 列表。

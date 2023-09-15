## 国内公共DNS  DoH/DoT/DoQ


DOT

DNS over TLS (DoT) is a network security protocol for encrypting and wrapping Domain Name System (DNS) queries and answers via the Transport Layer Security (TLS) protocol. 


### IP V4
1.1 腾讯 DNS
腾讯 DNS 基于 BGP Anycast 技术，不论用户身在何地，都可就近访问服务。支持谷歌 ECS 协议，配合 DNSPod 权威解析，可以给用户提供出最准确的解析结果，承诺不劫持解析结果。

IPv4：119.29.29.29
DoH：<https://doh.pub/dns-query>
DoH：<https://1.12.12.12/dns-query>
DoH：<https://120.53.53.53/dns-query>
DoH：<https://sm2.doh.pub/dns-query> (国密)
DoT：dot.pub
DoT：1.12.12.12
DoT：120.53.53.53
1.2 阿里 DNS
阿里 DNS 线路支持包括电信、移动、联通、鹏博士、广电网、教育网及海外 150 个国家或地域，支持用户 ECS 扩展技术，智能解析；支持 DoT/DoH 协议，保护用户隐私，安全防劫持。

IPv4：223.5.5.5
IPv4：223.6.6.6
DoH：<https://223.5.5.5/dns-query>
DoH：<https://223.6.6.6/dns-query>
DoH：<https://dns.alidns.com/dns-query>
DoT：dns.alidns.com

### 国内 IPv6 DNS
下一代互联网国家工程中心 IPv6 DNS
下一代互联网国家工程中心（CFIEC），由北京市发改委于 2012 年认定的北京市工程研究中心，并于 2015 年由国家发改委批复升级为国家地方联合工程研究中心。

IPv6：240C::6666
IPv6：240C::6644
DoT：dns.ipv6dns.com
DoH：<https://dns.ipv6dns.com/dns-query>
DNS64：240c::64 #纯 IPv6 访问 IPv4，需同时具备 DNS64 和 NAT64 服务可以
阿里云 IPv6 DNS
IPv6：2400:3200::1
IPv6：2400:3200:baba::1
DoH：<https://2400:3200::1/dns-query>
DoH：<https://2400:3200:baba::1/dns-query>
红鱼 rubyfish IPv6 DNS
DoT：v6.rubyfish.cn
DoH：<https://v6.rubyfish.cn/dns-query>
腾讯 IPv6 DNS
2402:4e00::


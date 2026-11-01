# ss机场：Shadowsocks 协议机场怎么选

> 通常，ss机场是在说 Shadowsocks 节点相关服务，协议名不能代表全部服务条件，各家写法不同。买前要分别核对加密方式、UDP、客户端与导入格式，而不是只认 SS 名称。

> 依据:Shadowsocks 与各客户端项目文档 · 最近核对 2026-11-01

## 三种协议怎样区分？

项目文档分别描述协议和配置，不能按名称给效果排名。

| 协议 | 项目文档怎么写 | 客户端文档是否列出 |
| --- | --- | --- |
| Shadowsocks | 建议尽可能采用 AEAD 这类加密方式 | mihomo、sing-box 有配置页 |
| Trojan | 协议设计让流量呈现类似普通 HTTPS 的形式 | mihomo、sing-box 有配置页 |
| VMess | 协议页要求采用 AEAD 认证，MD5 认证已弃用 | mihomo 有配置页 |

这里的 AEAD 是文档中的加密类别。

## ss机场通常指哪一部分？

通常要分清说的是仅提供 SS 的服务，还是多协议服务中的 SS 节点。

- 一般问清服务整体采用什么协议，不只看节点名。
- 通常再对照设备上的客户端与加密方式。
- 协议描述通信方式，不直接给出具体服务的支持清单。

## 客户端列出就能直接导入吗？

协议、加密方式和配置导入是需要分开核对的内容。

mihomo 的 cipher 项列出加密方式，也有 udp-over-tcp。sing-box 则把 multiplex 与 udp_over_tcp 标为不能同时使用；这是该客户端的配置限制，不是所有软件共同的开关。

SIP002 定义分享设置的 URI 形式。2022 系列的用户信息采用百分号编码，不用 Base64URL；分享格式说明不等于已经确认你的订阅可被当前设备导入。

## 旧加密方式该怎么看？

Shadowsocks 流式加密页面已标为弃用的历史内容，并让新用户改用 AEAD。

AEAD 页列有 chacha20-ietf-poly1305、aes-256-gcm、aes-128-gcm。sing-box 又将 ctr、cfb、rc4-md5 等归入 legacy，不能仅凭配置列表出现，就忽略其分类。

## 买前具体核对哪些内容？

通常核对下列项目，服务商的具体支持仍看自身说明。

| 核对项 | 要分清的内容 |
| --- | --- |
| 加密方式 | 实际采用什么，不只写 SS |
| UDP | 服务与客户端怎样支持 |
| 客户端 | 是否列出对应协议与加密方式 |
| 导入格式 | 是否能由你的客户端读取 |

继续阅读 [客户端支持与配置问题](https://www.jichangyyds.com/faq/clients/)，或对照 [下单前核对项目](../rumen/机场节点怎么买-下单前查五项.md)。

## 常见问题

### 列表里有旧方式就适合新用户吗？

不能只看名称是否存在；项目还给出了弃用与 legacy 分类，Shadowsocks 文档让新用户采用 AEAD。

### multiplex 与 udp_over_tcp 可以一起开吗？

sing-box 的 Shadowsocks 配置页标明二者冲突，不能同时使用。

### 只看协议名能确定服务支持吗？

通常还要看加密、UDP、客户端和导入格式。

## 出处

- [Shadowsocks AEAD 文档](https://shadowsocks.org/doc/aead.html)
- [mihomo 的 Shadowsocks 配置](https://wiki.metacubex.one/en/config/proxies/ss/)
- [sing-box 的 Shadowsocks 配置](https://sing-box.sagernet.org/configuration/outbound/shadowsocks/)

[← 知识库目录](../guides.md) ｜ [← 场景总览](../scenarios.md) ｜ [← 主清单](../../README.md)

# Rules List (规则列表)

本目录包含自定义的分流规则文件，适用于 OpenClash 的 `Rule Providers` 或其他 Clash 客户端的规则引用。

## 📂 文件说明

### 1. `Custom_Check.list` (网络探测)
**用途**：用于网络连通性测试、IP 地址探测和测速网站的分流。
- **包含内容**：
  - 测速服务：`speedtest.net`, `fast.com` 等。
  - IP 探测：`ip.sb`, `ipify.org`, `vultr.com` 等。
- **建议策略**：通常指向 `Global` 或特定代理策略组。

### 2. `Custom_Proxy.list` (强制代理)
**用途**：收录必须走代理的域名列表（个人收集）。
- **包含内容**：
  - 被墙或访问不畅的国外服务。
  - Google 服务相关域名（如 `googleapis.cn`）。
  - 其他需要代理访问的小众站点。
- **建议策略**：指向 `Proxy` 或具体地区的策略组。

### 3. `Custom_Direct.list` (直连白名单)
**用途**：收录明确不需要代理、需要直连的域名列表。
- **包含内容**：
  - 国内站点（如有误伤）。
  - PT 站点（Private Tracker）。
  - 某些对 IP 限制严格的国内服务。
- **建议策略**：指向 `DIRECT`。

## 🚀 引用方式

在 OpenClash 配置文件中添加 Rule Providers：

```yaml
rule-providers:
  Custom_Check:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/你的用户名/Custom_OpenClash_Rules/main/rule/Custom_Check.list"
    path: ./rules/Custom_Check.list
    interval: 86400

  Custom_Proxy:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/你的用户名/Custom_OpenClash_Rules/main/rule/Custom_Proxy.list"
    path: ./rules/Custom_Proxy.list
    interval: 86400

  Custom_Direct:
    type: http
    behavior: classical
    url: "https://raw.githubusercontent.com/你的用户名/Custom_OpenClash_Rules/main/rule/Custom_Direct.list"
    path: ./rules/Custom_Direct.list
    interval: 86400
```

然后在 `rules` 部分引用：

```yaml
rules:
  - RULE-SET,Custom_Direct,DIRECT
  - RULE-SET,Custom_Check,节点选择
  - RULE-SET,Custom_Proxy,节点选择
  - ...
```

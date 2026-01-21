# Custom OpenClash Rules (自用 OpenClash 规则集)

本项目包含自用的 OpenClash 规则列表、配置模板以及配套的图标集。

## 📂 项目结构

### 1. 规则列表 (`rule/`)
包含自定义的分流规则，可用于 OpenClash 的 Rule Providers。

- **`Custom_Check.list`**  
  网络连通性探测与测速相关域名。  
  *包含：speedtest.net, fast.com, vultr.com, cloudflare speed test 等。*

- **`Custom_Proxy.list`**  
  强制代理规则列表（个人收集）。  
  *包含：ip.sb, googleapis.cn, ipify.org 等需要代理访问的服务。*

- **`Custom_Direct.list`**  
  直连规则列表。  
  *(目前为空，可根据需要自行添加国内域名或无需代理的域名)*

### 2. 配置模板 (`cfg/`)
提供了两款基于 OpenClash 的配置模板，预设了策略组和分流规则。

- **`Custom_Clash_Smart_Emoji.yaml`**  
  **Emoji 风格**：使用 Emoji 作为策略组图标，通用性强，无需外部图标资源。

- **`Custom_Clash_Smart_Icon.yaml`**  
  **图标风格**：使用自定义图片作为策略组图标，视觉效果更佳，需配合 `IconSet` 使用。

### 3. 图标集 (`IconSet/`)
包含大量精美的图标资源，适用于 Clash 客户端的策略组图标显示。

- **Color/**: 彩色通用图标，覆盖流媒体、地区、常用软件等。
- **Dark/**: 适配深色模式的图标。

## 🚀 使用说明

### 引用规则
在 OpenClash 或其他 Clash 客户端中，可以通过 `Rule Providers` 引用本项目的规则文件。

**示例 (YAML):**
```yaml
rule-providers:
  Custom_Proxy:
    type: http
    interval: 86400
    behavior: domain
    format: mrs
    url: "https://raw.githubusercontent.com/MayflyDestiny/Custom_OpenClash_Rules/main/rule/Custom_Proxy.mrs"
    path: "./rules/Custom_Proxy"
```

### 使用配置模板
1. 下载 `cfg/` 目录下的 `.yaml` 文件。
2. 打开文件，找到 `proxy-providers` 部分。
3. 将 `url: 订阅地址` 或 `url: '订阅源地址'` 替换为你实际的机场订阅链接。
4. 根据需要调整策略组和规则。

## ⚠️ 注意事项
- 本项目规则主要为自用，可能不涵盖所有网络环境，建议根据实际需求微调。
- 引用 GitHub 链接时，建议使用 CDN (如 `jsdelivr` 或 `ghproxy`) 以提高加载速度。

## 👤 Credits
- **Designer**: MayflyDestiny
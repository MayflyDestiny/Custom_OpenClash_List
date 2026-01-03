# IconSet (图标集)

本目录包含适用于 Clash / OpenClash 策略组的图标资源。

## 📂 目录结构

### 1. `Color/` (推荐)
包含全套彩色图标，设计风格统一，适用于大多数浅色或深色主题。
- **涵盖类别**：
  - **地区/国家**：HK, US, JP, SG, TW 等。
  - **流媒体**：Netflix, Disney+, YouTube, Spotify 等。
  - **应用/服务**：GitHub, OpenAI, Telegram, Discord 等。
  - **功能**：Game, Download, Speedtest 等。

### 2. `Dark/`
适配深色模式界面的图标变体。
- 针对深色背景进行了优化，确保图标清晰可见。

### 3. 根目录
包含一些基础图标或旧版图标资源。

## 🚀 如何使用

在 Clash 配置文件 (`.yaml`) 的 `proxy-groups` 中，通过 `icon` 字段引用图标。

**在线引用示例：**
```yaml
proxy-groups:
  - name: GitHub
    type: select
    proxies:
      - 节点选择
    # 使用 GitHub Raw 地址 (建议配合 CDN 加速)
    icon: https://raw.githubusercontent.com/你的用户名/Custom_OpenClash_Rules/main/IconSet/Color/GitHub.png
```

**本地引用示例 (OpenClash):**
如果您将图标下载到了路由器的 `/etc/openclash/icon/` 目录：
```yaml
proxy-groups:
  - name: GitHub
    type: select
    proxies:
      - 节点选择
    icon: GitHub.png
```

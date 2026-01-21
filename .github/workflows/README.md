# GitHub 工作流

本目录包含自动化此仓库任务的 GitHub Actions 工作流。

## 工作流列表

### 自动生成规则 (`auto-generate-rules.yml`)

当 `rule/` 目录中的规则文件发生变更并推送时，此工作流会自动处理这些规则文件。

**触发条件:**
- 推送事件包含匹配 `rule/*.list` 路径的文件变更
- 手动触发 (`workflow_dispatch`)

**任务步骤:**
1. **生成 YAML**: 将 `.list` 文件（Classical 格式）转换为兼容 Clash Premium 和 Mihomo 的 `.yaml` 规则集文件。
2. **转换为 MRS**: 使用 `mihomo` 将 `.yaml` 规则集编译为二进制 `.mrs` (Mihomo Rule Set) 格式，以获得更好的性能。
3. **提交并推送**: 自动将生成的 `.yaml` 和 `.mrs` 文件提交并推送到仓库。

### 刷新 jsDelivr 缓存 (`purge-rule-cdn.yml`)

当 `Auto generate rules` 工作流成功完成后，此工作流会自动刷新 jsDelivr CDN 缓存，确保用户能立即获取到最新的规则文件。

**触发条件:**
- `Auto generate rules` 工作流执行完成 (`completed`)

**任务步骤:**
1. **检测变更文件**: 比较触发构建的提交与当前最新提交，找出发生变更的规则文件 (`.list`, `.yaml`, `.mrs`)。
2. **刷新缓存**: 调用 jsDelivr 的 Purge API 刷新变更文件的缓存。

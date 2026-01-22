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

### 清理失败/取消的工作流记录 (`clean_failed_cancelled_runs.yml`)

此工作流用于维护 GitHub Actions 运行记录的整洁，自动删除失败或已取消的运行记录，以及本清理工作流自身的运行记录。

**触发条件:**
- 手动触发 (`workflow_dispatch`)

**任务步骤:**
1. **清理异常记录**: 遍历仓库的所有 Workflow 运行记录，删除状态为 `failure` (失败) 或 `cancelled` (取消) 的记录。
2. **自我清理**: 删除本工作流 (`Clean Failed/Cancelled Workflow Runs`) 的所有运行记录（包括成功的），以避免清理工具本身产生大量历史记录。

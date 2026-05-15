---
name: longhorn-k8s-helper
description: 用于 Longhorn、Kubernetes、备份快照、Helm、kubectl、StorageClass、CSI、RecurringJob 和集群排障。
---

# Longhorn Kubernetes 辅助 Skill

处理 Longhorn 和 Kubernetes 相关问题时使用这个 skill。

工作流程：

1. 先确认 Longhorn 版本、Kubernetes 版本、StorageClass、backup target 和 namespace。
2. 对版本相关事实，先通过 SearXNG 搜索官方 Longhorn 或 Kubernetes 文档。
3. 审查脚本时重点检查破坏性命令、namespace 假设、CRD 变更和 backup target 凭据。
4. 优先使用 dry-run、只读检查和可回滚方案。

风险点：

- 删除 volume 或 snapshot。
- 全局修改 RecurringJob。
- 重新安装 CRD。
- 修改 backup target 凭据。
- 执行没有 namespace 限制的集群级 kubectl 命令。

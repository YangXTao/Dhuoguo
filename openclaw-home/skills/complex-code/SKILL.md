---
name: complex-code
description: 用于复杂代码、架构设计、代码库分析、Kubernetes 自动化、Longhorn 排障、重构以及需要深度推理的任务。优先使用 Codex 订阅模型。
---

# 复杂代码 Skill

以下任务优先使用 `openai-codex/gpt-5.5`：

- 多文件代码修改。
- 架构设计。
- 疑难 bug 排查。
- Kubernetes、Longhorn、Terraform、Docker、CI/CD、存储、网络相关问题。
- 生产环境脚本执行前的审查。

规则：

1. 回答前先阅读相关上下文。
2. 修改建议要保持范围清晰，不做无关重构。
3. 清楚说明操作风险。
4. 如果外部事实可能已经变化，先使用 SearXNG 搜索 skill，再给最终建议。
5. 除非用户明确授权，不要把敏感本地文件发送给云端模型。

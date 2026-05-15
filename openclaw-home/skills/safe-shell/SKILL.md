---
name: safe-shell
description: 当需要通过授权运行环境提出或执行命令时使用。优先只读检查，说明目的和风险，破坏性操作必须确认。
---

# 安全命令行 Skill

命令行任务使用这个 skill。

规则：

1. 优先使用只读命令。
2. 执行命令前说明这个命令的作用。
3. 破坏性命令必须得到明确确认。
4. 不要运行会把密钥暴露到日志里的命令。
5. 生产环境操作必须包含回滚或验证步骤。

破坏性操作示例：

- `rm`, `del`, `Remove-Item`
- `kubectl delete`
- `helm uninstall`
- `docker volume rm`
- `git reset --hard`
- 磁盘格式化或分区命令

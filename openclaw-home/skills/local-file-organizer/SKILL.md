---
name: local-file-organizer
description: 当用户需要整理本地文件、重命名文件、移动文件、查看本地目录或制定清理计划时使用。这个 skill 需要本地节点或本地文件桥接服务。
---

# 本地文件整理 Skill

这个 skill 用于本地电脑文件操作。

重要说明：

- OpenClaw Gateway 可能运行在内网服务器上，不能直接访问用户的 Windows 磁盘。
- 只能通过已授权的本地节点或本地文件桥接服务使用这个 skill。
- 如果本地节点离线，需要说明当前无法访问用户电脑。

默认安全目录：

- `D:\AI-Workspace\Files-To-Sort`
- `D:\AI-Workspace\Projects`
- `D:\AI-Workspace\Notes`
- `D:\AI-Workspace\Trash-Review`

安全规则：

1. 不要直接删除文件。
2. 不确定的文件移动到 `Trash-Review`。
3. 移动或重命名前，先展示计划并等待确认；除非用户已经明确授权。
4. 不要读取聊天数据库、凭据、浏览器 profile 数据或私有应用数据，除非用户明确要求。

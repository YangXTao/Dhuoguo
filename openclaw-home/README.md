# OpenClaw Home

This directory is the portable OpenClaw workspace for the LAN deployment.

Target layout:

- OpenClaw Gateway runs on an intranet server with Docker Compose.
- SearXNG runs on the same host and is the default web search backend.
- The default remote reasoning model is `openai-codex/gpt-5.5`.
- Long-term memory and runtime state are persisted outside the container.
- This directory can be edited locally in VS Code, pushed to Git, then pulled by the intranet server.

## Directory Map

```text
openclaw-home/
├─ docker-compose.yml
├─ .env.example
├─ .gitignore
├─ config/
│  └─ openclaw.json
├─ agents/
│  ├─ main.md
│  └─ routing.md
├─ skills/
│  ├─ searxng-search/
│  ├─ complex-code/
│  ├─ local-file-organizer/
│  ├─ longhorn-k8s-helper/
│  ├─ memory-curator/
│  └─ safe-shell/
├─ searxng/
│  └─ settings.yml
├─ memory/
├─ workspace/
├─ data/
├─ auth/
└─ backups/
```

## First Run On The Intranet Server

Copy the environment template:

```bash
cp .env.example .env
cp searxng/settings.yml.example searxng/settings.yml
```

Start SearXNG and OpenClaw:

```bash
docker compose up -d
```

Check SearXNG:

```bash
curl "http://127.0.0.1:8080/search?q=test&format=json"
```

Login to the Codex subscription provider:

```bash
docker compose run --rm openclaw-cli models auth login --provider openai-codex
```

Login to Feishu:

```bash
docker compose run --rm openclaw-cli channels login --channel feishu
docker compose restart openclaw-gateway
```

List available models and verify the exact Codex model name:

```bash
docker compose run --rm openclaw-cli models list
```

If `openai-codex/gpt-5.5` is not listed, change `config/openclaw.json` to the newest available `openai-codex/<model>` value.

## Git Policy

Commit:

- `docker-compose.yml`
- `.env.example`
- `config/`
- `agents/`
- `skills/`
- `searxng/settings.yml`
- `README.md`

Do not commit:

- `.env`
- `searxng/settings.yml`
- `auth/`
- `memory/`
- `data/`
- `workspace/`
- `backups/`

## Migration

To move OpenClaw to another machine, stop the service and copy the full directory, including runtime state:

```bash
docker compose down
tar -czf openclaw-home-backup.tar.gz openclaw-home
```

Restore it on the new machine and run:

```bash
docker compose up -d
```

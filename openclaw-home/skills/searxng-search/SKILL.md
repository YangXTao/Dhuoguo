---
name: searxng-search
description: 当用户需要搜索互联网、核对最新信息、比较外部资料或查询文档时使用。搜索后端必须使用内网 SearXNG 服务。
---

# SearXNG 搜索 Skill

当任务需要互联网搜索时，使用这个 skill。

后端：

- 使用 `SEARXNG_BASE_URL`。
- Docker Compose 默认地址：`http://searxng:8080`。

行为规则：

1. 使用 SearXNG 执行搜索。
2. 优先选择官方文档、一手资料、release notes、厂商文档和可靠技术资料。
3. 搜索结果需要用中文总结。
4. 对时间敏感的问题，需要给出来源链接和搜索日期。
5. 如果搜索后端不可用，明确说明当前无法访问内网 SearXNG 服务。

除非用户明确要求，不要使用模型提供商自带的 web search。

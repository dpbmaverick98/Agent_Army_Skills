---
name: openrepo
description: AI-powered GitHub research via OpenRepo API through Obul proxy. Supports repository exploration, file retrieval, code search, and asynchronous AI research tasks with multi-step analysis capabilities.
homepage: https://mavs-agent-army.fly.dev/api/openrepo
metadata:
  obul-skill:
    emoji: "🔍"
    requires:
      env: ["OBUL_API_KEY"]
    primaryEnv: "OBUL_API_KEY"
---

# OpenRepo Operations

Research GitHub repositories using AI-powered analysis via the Obul proxy. Supports metadata retrieval, file exploration, code search, and asynchronous deep-dive research tasks.

## Authentication

All requests route through the Obul proxy and require an API key header:

```json
{
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

**Base URL:** `https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/openrepo/v1`

## Common Operations

### Start AI Research (Async)

Launch a multi-step AI research task. Returns a `requestId` to poll for results.

**Pricing:** $0.05

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/openrepo/v1/research",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "message": "Summarize how React implements custom hooks",
    "maxSteps": 20,
    "context": []
  }
}
```

**Response:** `{"requestId": "550e8400-e29b-41d4-a716-446655440000"}`

### Check Research Status

Poll for research completion. Call repeatedly until `status` is `completed` or `failed`.

**Pricing:** $0.0001 per call  
**Polling Strategy:** Wait 5 seconds between calls, max 40 attempts (200s total timeout).

```json
{
  "method": "GET",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/openrepo/v1/research/status?requestId=550e8400-e29b-41d4-a716-446655440000",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

**Response fields:**
- `status`: `pending` | `processing` | `completed` | `failed` | `not_found`
- `text`: Full AI-generated report (when `status: "completed"`)
- `error`: Error message (when `status: "failed"`)

### Get Repository Metadata

Fetch stars, forks, language, recent commits, and contributor stats.

**Pricing:** $0.005

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/openrepo/v1/api/repo-metadata",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "repo": "facebook/react"
  }
}
```

### Fetch File Content

Retrieve raw content of a specific file.

**Pricing:** $0.005

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/openrepo/v1/api/file-content",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "repo": "facebook/react",
    "path": "src/index.js",
    "ref": "main"
  }
}
```

**Alternative:** Pass `url` (full GitHub file URL) instead of `repo`/`path`/`ref`.

### Get Repository Structure

List directory contents with optional file inclusion.

**Pricing:** $0.005

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/openrepo/v1/api/repo-structure",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "repo": "facebook/react",
    "path": "packages",
    "includeContent": false,
    "ref": "main"
  }
}
```

### Search Repositories

Find public repositories by keywords, language, or topics.

**Pricing:** $0.005

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/openrepo/v1/api/search-repos",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "state management",
    "language": "typescript",
    "sort": "stars",
    "limit": 5
  }
}
```

**Parameters:**
- `query`: Search keywords
- `language`: Programming language filter
- `topic`: GitHub topic filter
- `sort`: `stars` (default), `forks`, or `updated`
- `limit`: Max results (default 10)

**Response includes:** `totalCount`, `results` array with `name`, `description`, `url`, `stars`, `forks`, `language`, `topics`, `license`

### Search Code Inside Repository

Search for code patterns within a specific repository.

**Pricing:** $0.005

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/openrepo/v1/api/search-code",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "repo": "facebook/react",
    "query": "useState",
    "fileExtension": "tsx",
    "limit": 10
  }
}
```

### Health Check (Free)

Verify service availability before spending credits.

**Pricing:** $0.00

```json
{
  "method": "GET",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/openrepo/v1/health",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

## Async Research Workflow

1. **Start:** Call `POST /research` with your query → receive `requestId`
2. **Poll:** Call `GET /research/status?requestId=...` every 5 seconds
3. **Complete:** Stop when `status` is `completed` (read `text` field) or `failed` (read `error` field)

**Max execution time:** 200 seconds (40 poll attempts × 5s intervals)

## Endpoint Pricing Reference

| Endpoint | Price | Purpose |
|----------|-------|---------|
| `GET /health` | $0.00 | Service status check |
| `POST /research` | $0.05 | Start AI analysis |
| `GET /research/status` | $0.0001 | Poll for results |
| `POST /api/repo-metadata` | $0.005 | Repo stats & info |
| `POST /api/file-content` | $0.005 | Read single file |
| `POST /api/repo-structure` | $0.005 | Directory listing |
| `POST /api/repo-tree` | $0.005 | Full file tree |
| `POST /api/repo-readme` | $0.005 | Top-level README |
| `POST /api/repo-readme-dir` | $0.005 | Sub-directory README |
| `POST /api/search-repos` | $0.005 | Find repositories |
| `POST /api/search-code` | $0.005 | Search within repo |
| `POST /api/parse-repo-url` | $0.002 | Validate GitHub URLs |

## When to Use

- User asks to "analyze" or "research" a codebase deeply (use async research)
- Need to find specific code patterns or implementations (use code search)
- Retrieving README documentation or file contents
- Comparing repositories or finding alternatives (use search-repos)
- Understanding project structure or dependencies

## Best Practices

1. **Always check health first** before expensive operations when possible
2. **Cache metadata** – Repo stats and READMEs change infrequently; store locally to save costs
3. **Batch file requests** – Use `repo-structure` with `includeContent: true` instead of multiple `file-content` calls for multiple files
4. **Limit research steps** – Set `maxSteps` (1-30) based on query complexity; default 15 is sufficient for most tasks
5. **Poll gracefully** – If `not_found` returned, the requestId expired or was invalid; restart the research
6. **Use context** – Pass prior conversation turns in the `context` array for follow-up research to maintain continuity

## Error Handling

| Error | Cause | Solution |
|-------|-------|----------|
| `not_found` | Invalid `requestId` or expired session | Restart research with new request |
| `failed` | Research task error | Check `error` field in response; retry with simplified query |
| HTTP 429 | Rate limit or quota exceeded | Back off and inform user of cost |
| Validation error | Missing `repo` or `path` fields | Ensure `repo` uses `owner/name` format |
| `truncated: true` | Repo tree too large | Request specific subdirectories instead of full tree |
| Timeout | Research exceeded 200s | Increase `maxSteps` for complex queries or break into smaller questions |

---
name: xwriter
description: AI-powered tweet generation via xWriter API through Obul proxy. Features X/Twitter research, engagement optimization with X-Algo scoring, and async tweet writing with multiple style options.
homepage: https://mavs-agent-army.fly.dev/api/xwriter
metadata:
  obul-skill:
    emoji: "𝕏"
    requires:
      env: ["OBUL_API_KEY"]
    primaryEnv: "OBUL_API_KEY"
---

# xWriter Operations

Generate engaging tweets using AI-powered research and X-Algo engagement optimization. Research topics on X/Twitter, then create tweets optimized for maximum engagement.

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

**Base URL:** `https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/xwriter`

## Workflow Overview

The typical workflow is:
1. **Research** a topic (async, $0.15)
2. **Poll for results** until complete ($0.0001 per call)
3. **Write tweets** based on research context (async, $0.10)
4. **Poll for tweet results** until complete ($0.0001 per call)

## Common Operations

### Research Topic (Async)

Start an async research task on a topic using X/Twitter search and web search. Analyzes public sentiment, latest developments, key statistics, and generates tweet topic suggestions.

**Pricing:** $0.15

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/xwriter/api/topics/research",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "topic": "AI agents in 2025"
  }
}
```

**Response:** `{"requestId": "550e8400-e29b-41d4-a716-446655440000"}`

**Research Result Includes:**
- Topic overview and latest developments
- Public sentiment analysis
- Key statistics and notable quotes
- Controversies and emerging trends
- 3+ generated tweet topics with angles
- Relevant tweets, trending hashtags, and sources
- Engagement potential ratings (low/medium/high)

### Check Request Status

Poll for async request completion. Call repeatedly until `status` is `completed` or `failed`.

**Pricing:** $0.0001 per call  
**Polling Strategy:** Wait 5 seconds between calls, max 40 attempts (200s total timeout).

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/xwriter/api/status?requestId=550e8400-e29b-41d4-a716-446655440000",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

**Response fields:**
- `status`: `pending` | `processing` | `completed` | `failed` | `not_found`
- `result`: Full research or write result (when `status: "completed"`)
- `error`: Error message (when `status: "failed"`)

### Write Tweets (Async)

Generate tweets from research context with X-Algo engagement optimization. Returns 3 tweet options plus an X-Algo optimized version with engagement predictions.

**Pricing:** $0.10

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/xwriter/api/tweets/write",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "context": "OpenAI released GPT-5 in August 2025 with PhD-level reasoning capabilities. BrowseComp benchmark shows 60.6% vs Opus 37.0%. 8x cost savings.",
    "topic": "GPT-5 reasoning capabilities",
    "style": "casual",
    "length": "short",
    "customPrompt": "Skeptical take on the timeline claims, focus on infrastructure challenges"
  }
}
```

**Parameters:**
- `context` (required): Full research context from `/api/topics/research` or your own text
- `topic` (required): Topic title or focus area
- `style` (optional): `casual` (default), `professional`, or `thoughtful`
- `length` (optional): `short` (default), `medium`, or `long`
- `customPrompt` (optional): Open-ended customization (max 500 chars)

**Write Result Includes:**
- 3 generated tweet options with character counts
- X-Algo optimized tweet with engagement predictions
- Engagement scores for reply, share, like, dwell signals
- Total engagement score and dominant signal
- Strategy explanation for the X-Algo choice

**Note:** To rewrite a tweet without doing research first, send the same input in both `context` and `topic` fields:

```json
{
  "context": "Your tweet text here that you want to rewrite",
  "topic": "Your tweet text here that you want to rewrite",
  "style": "professional",
  "length": "medium"
}
```

### Health Check (Free)

Verify service availability before spending credits.

**Pricing:** $0.00

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/xwriter/api/health",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

## Complete Workflow Example

### Step 1: Research a Topic

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/xwriter/api/topics/research",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "topic": "SpaceX Mars mission 2025"
  }
}
```

**Response:** `{ "requestId": "abc-123" }`

### Step 2: Poll for Research Results

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/xwriter/api/status?requestId=abc-123",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

Repeat every 5 seconds until `status: "completed"`.

### Step 3: Write Tweets from Research

Extract the comprehensive context from the research result and use it to write tweets:

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/xwriter/api/tweets/write",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "context": "SpaceX announced plans for first crewed Mars mission in 2025...",
    "topic": "SpaceX Mars mission timeline",
    "style": "thoughtful",
    "length": "medium"
  }
}
```

**Response:** `{ "requestId": "def-456" }`

### Step 4: Poll for Tweet Results

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/xwriter/api/status?requestId=def-456",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

## Endpoint Pricing Reference

| Endpoint | Price | Purpose |
|----------|-------|---------|
| `GET /api/health` | $0.00 | Service status check |
| `POST /api/topics/research` | $0.15 | Research topic on X/Twitter |
| `POST /api/tweets/write` | $0.10 | Generate tweets with X-Algo optimization |
| `GET /api/status` | $0.0001 | Poll for async results |

**Total workflow cost:** ~$0.25 ($0.15 research + $0.10 writing, plus minimal polling costs)

## When to Use

- Creating tweets about trending topics or news
- Need data-driven content with research backing
- Want X-Algo engagement optimization for maximum reach
- Rewriting existing tweets for better engagement
- Generating multiple tweet options from research
- Understanding public sentiment on topics before tweeting

## Best Practices

1. **Start with research** – Research provides rich context that improves tweet quality significantly
2. **Use specific topics** – "AI agents" is better than "technology"
3. **Leverage custom prompts** – Add your unique perspective or angle
4. **Choose appropriate style** – Match your brand voice (casual/professional/thoughtful)
5. **Check X-Algo recommendations** – The optimized tweet often performs better
6. **Review engagement predictions** – Understand why certain tweets work better
7. **Cache research results** – Research changes slowly; cache for 30 minutes to save costs
8. **Rewrite strategically** – Use the rewrite feature (same context + topic) to iterate quickly

## Tweet Rewrite Shortcut

If you already know what you want to say and just need it rewritten:

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/xwriter/api/tweets/write",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "context": "Just shipped a new feature! Check it out.",
    "topic": "Just shipped a new feature! Check it out.",
    "style": "casual",
    "length": "short"
  }
}
```

**Cost:** Only $0.10 (skip the research step)

## Error Handling

| Error | Cause | Solution |
|-------|-------|----------|
| `not_found` | Invalid `requestId` or expired (30 min TTL) | Restart the async operation |
| `failed` | Processing error | Check `error` field; retry with simplified input |
| HTTP 429 | Rate limit exceeded | Wait and retry; check rate limit headers |
| Validation error | Missing required fields | Ensure `topic` for research, `context` for writing |
| Timeout | Request exceeded 200s | Retry with more specific topic or shorter custom prompt |

## Rate Limits

- Research endpoint: 10 requests/minute (expensive)
- Write endpoint: 10 requests/minute (expensive)
- Status endpoint: 120 requests/minute (cheap)

Exceeding limits returns HTTP 429 with `Retry-After` header.

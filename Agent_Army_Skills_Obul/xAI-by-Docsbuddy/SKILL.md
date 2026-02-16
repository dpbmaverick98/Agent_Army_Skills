---
name: "xAI by DocsBuddy"
description: AI-powered documentation Q&A and learning journeys for xAI - the AI platform with Grok models, API, and developer tools. Get instant answers about model capabilities, API endpoints, tools, and developer guides.
homepage: https://mavs-agent-army.fly.dev/api/docsbuddy/xai
metadata:
  obul-skill:
    emoji: "🧠"
    requires:
      env: ["OBUL_API_KEY"]
    primaryEnv: "OBUL_API_KEY"
---

# xAI by DocsBuddy

xAI is an AI platform with Grok models, API, and developer tools. Ask questions about model capabilities, API endpoints, function calling, and developer guides.

## Available Collection

xAI has **1 documentation collection**:

| Collection | Description | Best For |
|------------|-------------|----------|
| `xai_docs` | API reference, model capabilities, tools, and developer guides | All xAI and Grok questions |

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

**Base URL:** `https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/xai`

## Common Operations

### 1. List Collections

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/xai/collections",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### 2. Ask Quick Question

**Pricing:** $0.03

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/xai/ask/quick/xai_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I call the Grok API with streaming?"
  }
}
```

### 3. Ask Deep Question

**Pricing:** $0.06

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/xai/ask/deep/xai_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "What are the differences between Grok-2 and Grok-2-mini models?"
  }
}
```

### 4. Generate Learning Journey

**Pricing:** $0.08

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/xai/journey/xai_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Build an AI chatbot using Grok API with function calling capabilities"
  }
}
```

### 5. Check Status

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/xai/status/550e8400-e29b-41d4-a716-446655440000",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### 6. Get Source Document

**Pricing:** $0.01

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/source/550e8400-e29b-41d4-a716-446655440000/doc-0",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

## Endpoint Pricing Reference

| Endpoint | Price | Purpose |
|----------|-------|---------|
| `GET /collections` | $0.0001 | List collection |
| `POST /ask/quick/xai_docs` | $0.03 | Quick Q&A |
| `POST /ask/deep/xai_docs` | $0.06 | Deep technical Q&A |
| `POST /journey/xai_docs` | $0.08 | Generate tutorial |
| `GET /status/{requestId}` | $0.0001 | Poll for results |
| `GET /source/{requestId}/{reference}` | $0.01 | Get source doc |

## When to Use

- **Grok API** - Integration with Grok models
- **Function calling** - Tool use capabilities
- **Streaming** - Real-time responses
- **Model selection** - Choosing Grok variants
- **API migration** - Moving to xAI from other providers
- **Capabilities** - Understanding model features

## Best Practices

1. **API key security** - Store keys securely
2. **Streaming responses** - Better UX for chat
3. **Function calling** - Enable tool use
4. **Error handling** - Handle rate limits
5. **Context windows** - Manage token limits
6. **Vision capabilities** - Multi-modal support

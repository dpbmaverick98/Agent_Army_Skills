---
name: "Browserbase by DocsBuddy"
description: AI-powered documentation Q&A and learning journeys for Browserbase - the managed headless browser infrastructure for automation and AI agents. Get instant answers about browser automation, session management, and API integration.
homepage: https://mavs-agent-army.fly.dev/api/docsbuddy/browserbase
metadata:
  obul-skill:
    emoji: "🌐"
    requires:
      env: ["OBUL_API_KEY"]
    primaryEnv: "OBUL_API_KEY"
---

# Browserbase by DocsBuddy

Browserbase is a managed headless browser infrastructure for automation and AI agents. Ask questions about browser automation, session management, integrations, and API reference.

## Available Collection

Browserbase has **1 documentation collection**:

| Collection | Description | Best For |
|------------|-------------|----------|
| `browserbase_docs` | Browser automation, session management, integrations, and API reference | All Browserbase questions |

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

**Base URL:** `https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/browserbase`

## Common Operations

### 1. List Collections

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/browserbase/collections",
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
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/browserbase/ask/quick/browserbase_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I create a browser session with Browserbase?"
  }
}
```

### 3. Ask Deep Question

**Pricing:** $0.06

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/browserbase/ask/deep/browserbase_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How does Browserbase handle captchas and bot detection?"
  }
}
```

### 4. Generate Learning Journey

**Pricing:** $0.08

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/browserbase/journey/browserbase_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Build a web scraper that extracts data from JavaScript-heavy sites using Browserbase and Puppeteer"
  }
}
```

### 5. Check Status

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/browserbase/status/550e8400-e29b-41d4-a716-446655440000",
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
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/source/550e8400-e29b-41d4-a716-446655440000/doc-0",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

## Endpoint Pricing Reference

| Endpoint | Price | Purpose |
|----------|-------|---------|
| `GET /collections` | $0.0001 | List collection |
| `POST /ask/quick/browserbase_docs` | $0.03 | Quick Q&A |
| `POST /ask/deep/browserbase_docs` | $0.06 | Deep technical Q&A |
| `POST /journey/browserbase_docs` | $0.08 | Generate tutorial |
| `GET /status/{requestId}` | $0.0001 | Poll for results |
| `GET /source/{requestId}/{reference}` | $0.01 | Get source doc |

## When to Use

- **Web scraping** - Extract data from modern websites
- **AI agents** - Give AI tools browser access
- **Automation** - Automated browser tasks
- **Testing** - E2E testing with real browsers
- **Session management** - Persistent browser sessions
- **Captcha solving** - Handle bot detection

## Best Practices

1. **Session persistence** - Reuse sessions when possible
2. **Stealth mode** - Avoid detection with proper configs
3. **Rate limiting** - Be respectful to target sites
4. **Error handling** - Handle timeouts, failures gracefully
5. **Resource cleanup** - Close sessions when done
6. **Proxy rotation** - Use proxies for scale

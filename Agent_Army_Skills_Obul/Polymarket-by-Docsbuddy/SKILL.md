---
name: "Polymarket by DocsBuddy"
description: AI-powered documentation Q&A and learning journeys for Polymarket - the prediction market platform for trading on outcomes. Get instant answers about the API, trading guides, and platform integration.
homepage: https://mavs-agent-army.fly.dev/api/docsbuddy/polymarket
metadata:
  obul-skill:
    emoji: "📊"
    requires:
      env: ["OBUL_API_KEY"]
    primaryEnv: "OBUL_API_KEY"
---

# Polymarket by DocsBuddy

Polymarket is a prediction market platform for trading on outcomes. Ask questions about the API, trading guides, market data, and platform integration.

## Available Collection

Polymarket has **1 documentation collection**:

| Collection | Description | Best For |
|------------|-------------|----------|
| `polymarket_docs` | API reference, trading guides, and platform documentation | All Polymarket questions about API, trading, markets |

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

**Base URL:** `https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/polymarket`

## Common Operations

### 1. List Collections

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/polymarket/collections",
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
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/polymarket/ask/quick/polymarket_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I fetch market data from the Polymarket API?"
  }
}
```

### 3. Ask Deep Question

**Pricing:** $0.06

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/polymarket/ask/deep/polymarket_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How does Polymarket's CLOB (Central Limit Order Book) work for trading?"
  }
}
```

### 4. Generate Learning Journey

**Pricing:** $0.08

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/polymarket/journey/polymarket_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Build a dashboard that displays live Polymarket market data and prices"
  }
}
```

### 5. Check Status

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/polymarket/status/550e8400-e29b-41d4-a716-446655440000",
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
| `POST /ask/quick/polymarket_docs` | $0.03 | Quick Q&A |
| `POST /ask/deep/polymarket_docs` | $0.06 | Deep technical Q&A |
| `POST /journey/polymarket_docs` | $0.08 | Generate tutorial |
| `GET /status/{requestId}` | $0.0001 | Poll for results |
| `GET /source/{requestId}/{reference}` | $0.01 | Get source doc |

## When to Use

- **Market data** - Fetch prices, volumes, outcomes
- **Trading integration** - Place orders, manage positions
- **Prediction markets** - Understand market mechanics
- **Data analysis** - Historical data, trends
- **API integration** - Build apps with market data

## Best Practices

1. **API key management** - Secure your credentials
2. **Rate limits** - Respect API limits
3. **Real-time data** - WebSockets for live updates
4. **Order types** - Market vs limit orders
5. **Risk management** - Understand market resolution

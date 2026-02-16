---
name: "Relay by DocsBuddy"
description: AI-powered documentation Q&A and learning journeys for Relay - the cross-chain bridging and swapping protocol for 69+ blockchain networks. Get instant answers about the API, RelayKit SDK, protocol architecture, and integration guides.
homepage: https://mavs-agent-army.fly.dev/api/docsbuddy/relay
metadata:
  obul-skill:
    emoji: "🌉"
    requires:
      env: ["OBUL_API_KEY"]
    primaryEnv: "OBUL_API_KEY"
---

# Relay by DocsBuddy

Relay is a cross-chain bridging and swapping protocol for 69+ blockchain networks. Ask questions about the API, RelayKit SDK, protocol architecture, and integration guides.

## Available Collection

Relay has **1 documentation collection**:

| Collection | Description | Best For |
|------------|-------------|----------|
| `relay_docs` | API reference, RelayKit SDK, protocol architecture, and integration guides | All Relay questions |

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

**Base URL:** `https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/relay`

## Common Operations

### 1. List Collections

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/relay/collections",
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
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/relay/ask/quick/relay_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I get a quote for bridging ETH from Ethereum to Arbitrum?"
  }
}
```

### 3. Ask Deep Question

**Pricing:** $0.06

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/relay/ask/deep/relay_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How does Relay's cross-chain message passing work under the hood?"
  }
}
```

### 4. Generate Learning Journey

**Pricing:** $0.08

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/relay/journey/relay_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Build a cross-chain bridge UI using RelayKit SDK with quote fetching and transaction execution"
  }
}
```

### 5. Check Status

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/relay/status/550e8400-e29b-41d4-a716-446655440000",
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
| `POST /ask/quick/relay_docs` | $0.03 | Quick Q&A |
| `POST /ask/deep/relay_docs` | $0.06 | Deep technical Q&A |
| `POST /journey/relay_docs` | $0.08 | Generate tutorial |
| `GET /status/{requestId}` | $0.0001 | Poll for results |
| `GET /source/{requestId}/{reference}` | $0.01 | Get source doc |

## When to Use

- **Cross-chain bridging** - Move assets between chains
- **Multi-chain swaps** - Exchange tokens across networks
- **RelayKit SDK** - React/JS integration
- **API integration** - Direct API usage
- **Bridge UI** - Building user interfaces
- **Protocol understanding** - How Relay works

## Best Practices

1. **Quote first** - Always get a quote before executing
2. **Gas estimation** - Account for gas on both chains
3. **Slippage** - Set appropriate slippage tolerance
4. **Transaction tracking** - Monitor cross-chain status
5. **Error handling** - Handle failed transactions
6. **Chain support** - Check supported chains

---
name: "Privy by DocsBuddy"
description: AI-powered documentation Q&A and learning journeys for Privy - the authentication SDK for wallet management and user authentication. Get instant answers about embedded wallets, email/social login, and Web3 authentication patterns.
homepage: https://mavs-agent-army.fly.dev/api/docsbuddy/privy
metadata:
  obul-skill:
    emoji: "🔐"
    requires:
      env: ["OBUL_API_KEY"]
    primaryEnv: "OBUL_API_KEY"
---

# Privy by DocsBuddy

Privy is an authentication SDK for wallet management and user authentication in Web3 applications. Ask questions about embedded wallets, email/social login, wallet connection, and Web3 authentication patterns.

## Available Collection

Privy has **1 documentation collection**:

| Collection | Description | Best For |
|------------|-------------|----------|
| `privy_docs` | Authentication, wallets, and user management documentation | All Privy-related questions about wallets, auth, user management |

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

**Base URL:** `https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/privy`

## Common Operations

### 1. List Collections

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/privy/collections",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### 2. Ask Quick Question

**Pricing:** $0.03

**Example:** Embedded wallets

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/privy/ask/quick/privy_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I create an embedded wallet with email authentication?"
  }
}
```

**Example:** Social login

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/privy/ask/quick/privy_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I set up Google and Twitter login with Privy?"
  }
}
```

### 3. Ask Deep Question

**Pricing:** $0.06

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/privy/ask/deep/privy_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "What's the difference between embedded wallets and connected wallets in Privy?"
  }
}
```

### 4. Generate Learning Journey

**Pricing:** $0.08

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/privy/journey/privy_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Build a complete Web3 app with email login and embedded wallets using Privy"
  }
}
```

### 5. Check Status

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/privy/status/550e8400-e29b-41d4-a716-446655440000",
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
| `POST /ask/quick/privy_docs` | $0.03 | Quick Q&A |
| `POST /ask/deep/privy_docs` | $0.06 | Deep technical Q&A |
| `POST /journey/privy_docs` | $0.08 | Generate tutorial |
| `GET /status/{requestId}` | $0.0001 | Poll for results |
| `GET /source/{requestId}/{reference}` | $0.01 | Get source doc |

## When to Use

- **Web3 authentication** - Email, social, wallet login
- **Embedded wallets** - Create wallets for users
- **Wallet connection** - Connect existing wallets
- **User management** - Authentication state, logout
- **React integration** - usePrivy hook usage
- **Server-side auth** - Validating sessions, JWT

## Best Practices

1. **Embedded vs Connected** - Choose based on your use case
2. **Email flow** - Simplest onboarding for Web2 users
3. **Social login** - Google, Twitter, Discord options
4. **Wallet connectors** - MetaMask, WalletConnect, etc.
5. **Security** - Always validate on server side
6. **UX patterns** - Login buttons, wallet displays

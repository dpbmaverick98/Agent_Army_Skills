---
name: "Better Auth by DocsBuddy"
description: AI-powered documentation Q&A and learning journeys for Better Auth - the comprehensive authentication framework for TypeScript. Get instant answers about authentication methods, adapters, plugins, and integrations.
homepage: https://mavs-agent-army.fly.dev/api/docsbuddy/better-auth
metadata:
  obul-skill:
    emoji: "🔒"
    requires:
      env: ["OBUL_API_KEY"]
    primaryEnv: "OBUL_API_KEY"
---

# Better Auth by DocsBuddy

Better Auth is a comprehensive authentication framework for TypeScript. Ask questions about authentication methods, database adapters, plugins, framework integrations, and error handling.

## Available Collection

Better Auth has **1 documentation collection**:

| Collection | Description | Best For |
|------------|-------------|----------|
| `better_auth_docs` | Authentication, adapters, plugins, integrations, and error documentation | All Better Auth questions |

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

**Base URL:** `https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/better-auth`

## Common Operations

### 1. List Collections

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/better-auth/collections",
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
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/better-auth/ask/quick/better_auth_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I set up email/password authentication with Better Auth?"
  }
}
```

### 3. Ask Deep Question

**Pricing:** $0.06

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/better-auth/ask/deep/better_auth_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do Better Auth adapters work with different ORMs?"
  }
}
```

### 4. Generate Learning Journey

**Pricing:** $0.08

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/better-auth/journey/better_auth_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Build a Next.js app with Better Auth, Prisma, and social login"
  }
}
```

### 5. Check Status

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/better-auth/status/550e8400-e29b-41d4-a716-446655440000",
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
| `POST /ask/quick/better_auth_docs` | $0.03 | Quick Q&A |
| `POST /ask/deep/better_auth_docs` | $0.06 | Deep technical Q&A |
| `POST /journey/better_auth_docs` | $0.08 | Generate tutorial |
| `GET /status/{requestId}` | $0.0001 | Poll for results |
| `GET /source/{requestId}/{reference}` | $0.01 | Get source doc |

## When to Use

- **TypeScript apps** - Full TypeScript support
- **Multiple auth methods** - Email, OAuth, magic links
- **Database adapters** - Prisma, Drizzle, MongoDB
- **Framework support** - Next.js, Remix, SvelteKit
- **Plugin system** - 2FA, admin, organizations
- **Type-safe auth** - End-to-end TypeScript safety

## Best Practices

1. **Choose adapter** - Based on your ORM/database
2. **Plugins** - Add features as needed
3. **Type safety** - Leverage TypeScript
4. **Framework setup** - Follow framework-specific guides
5. **Social providers** - Configure OAuth apps
6. **Session management** - Secure cookie settings

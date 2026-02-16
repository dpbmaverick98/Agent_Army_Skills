---
name: "Sprites by DocsBuddy"
description: AI-powered documentation Q&A and learning journeys for Fly Sprites - persistent, stateful Linux microVMs for running arbitrary code with automatic hibernation. Get instant answers about core concepts, quickstart, CLI reference, and working with Sprites.
homepage: https://mavs-agent-army.fly.dev/api/docsbuddy/sprites
metadata:
  obul-skill:
    emoji: "🎮"
    requires:
      env: ["OBUL_API_KEY"]
    primaryEnv: "OBUL_API_KEY"
---

# Sprites by DocsBuddy

Fly Sprites provides persistent, stateful Linux microVMs (via Firecracker) for running arbitrary code with automatic hibernation. Unlike serverless functions, Sprites maintain their filesystem between runs. Ask questions about core concepts, quickstart, CLI reference, and working with Sprites.

## Available Collection

Sprites has **1 documentation collection**:

| Collection | Description | Best For |
|------------|-------------|----------|
| `sprites_docs` | Core concepts, quickstart, CLI reference (installation, authentication, commands), working with Sprites | All Sprites questions |

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

**Base URL:** `https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/sprites`

## Common Operations

### 1. List Collections

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/sprites/collections",
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
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/sprites/ask/quick/sprites_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I create my first Sprite?"
  }
}
```

**Example:** CLI commands

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/sprites/ask/quick/sprites_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "What CLI commands are available for managing Sprites?"
  }
}
```

### 3. Ask Deep Question

**Pricing:** $0.06

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/sprites/ask/deep/sprites_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How does Sprites' automatic hibernation work and when does it trigger?"
  }
}
```

**Example:** Networking

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/sprites/ask/deep/sprites_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How does networking work with Sprites? Can I expose ports?"
  }
}
```

### 4. Generate Learning Journey

**Pricing:** $0.08

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/sprites/journey/sprites_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Build a persistent Python development environment with Sprites that maintains installed packages between sessions"
  }
}
```

**Example:** CI/CD with Sprites

```json
{
  "method": "POST",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/sprites/journey/sprites_docs",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Set up a CI/CD pipeline using Sprites for running tests with persistent caching"
  }
}
```

### 5. Check Status

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/sprites/status/550e8400-e29b-41d4-a716-446655440000",
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
| `POST /ask/quick/sprites_docs` | $0.03 | Quick Q&A |
| `POST /ask/deep/sprites_docs` | $0.06 | Deep technical Q&A |
| `POST /journey/sprites_docs` | $0.08 | Generate tutorial |
| `GET /status/{requestId}` | $0.0001 | Poll for results |
| `GET /source/{requestId}/{reference}` | $0.01 | Get source doc |

## When to Use

- **Stateful workloads** - Code that needs persistence
- **Development environments** - Dev boxes that maintain state
- **Long-running tasks** - Jobs that need filesystem
- **CI/CD** - Build environments with caching
- **MicroVMs vs Containers** - Understanding the difference
- **CLI usage** - Commands for managing Sprites
- **Automation** - Programmatic Sprite management

## Best Practices

1. **State persistence** - Use Sprites when you need files to persist
2. **Hibernation** - Sprites auto-hibernate to save costs
3. **Checkpoints** - Create checkpoints before major changes
4. **Networking** - Expose ports for external access
5. **CLI authentication** - Set up Fly.io auth first
6. **Services** - Run long-running processes as services
7. **vs Serverless** - Use Sprites when state matters

## Sprites vs Serverless

**Use Sprites when:**
- You need filesystem persistence
- Installing dependencies takes time
- You want to maintain state between runs
- You need a full Linux environment

**Use Serverless when:**
- Stateless request/response
- Fast cold starts matter
- Simple functions without dependencies
- Ephemeral execution is fine

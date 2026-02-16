---
name: "Notion by DocsBuddy"
description: AI-powered documentation Q&A and learning journeys for Notion - the workspace platform with API for pages, databases, blocks, and integrations. Get instant answers about Notion's API, authentication, data operations, and integration guides across 10 documentation collections.
homepage: https://mavs-agent-army.fly.dev/api/docsbuddy/notion
metadata:
  obul-skill:
    emoji: "📝"
    requires:
      env: ["OBUL_API_KEY"]
    primaryEnv: "OBUL_API_KEY"
---

# Notion by DocsBuddy

Notion is a workspace platform with a powerful API for pages, databases, blocks, and integrations. Ask questions about Notion's API endpoints, authentication, data operations, or generate step-by-step learning journeys for building Notion integrations.

## Available Collections

Notion has **10 documentation collections** organized into API Objects, Guides, Compliance, and General documentation:

### API Objects Collections

| Collection | Description | Best For |
|------------|-------------|----------|
| `notion_api_objects_core` | Core entities: Block, Page, Database, Data Source - object schemas and properties | Understanding core data models, working with pages and databases |
| `notion_api_objects_entities` | Other entities: User, Comment, File, Properties, Rich Text, Emoji | User management, comments, file handling, rich text formatting |

### API Infrastructure

| Collection | Description | Best For |
|------------|-------------|----------|
| `notion_api_auth` | Authentication, Tokens, Users, Rate limits, Webhooks, Versioning | OAuth setup, token management, rate limiting, webhook configuration |

### Guides Collections

| Collection | Description | Best For |
|------------|-------------|----------|
| `notion_guides_data_apis` | Working with databases, files, comments, page content | CRUD operations, querying databases, file uploads, comments |
| `notion_guides_mcp` | Model Context Protocol, AI agent connections | Connecting AI agents to Notion, MCP integrations |
| `notion_guides_getting_started` | Authorization, first integration, publishing | Setting up your first integration, OAuth flow, publishing to gallery |
| `notion_guides_resources` | Best practices, examples, Postman workspace | Learning resources, API examples, testing with Postman |
| `notion_guides_link_previews` | Link preview integrations | Building link preview apps, unfurling URLs |

### Compliance & General

| Collection | Description | Best For |
|------------|-------------|----------|
| `notion_compliance` | Audit logs, SIEM events, security | Enterprise security, compliance requirements, audit trails |
| `notion_general` | Docs home, status, changelog, community | Getting started, API status, staying updated |

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

**Base URL:** `https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/notion`

## How to Discover Collections

Call the collections endpoint to see all available categories:

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/notion/collections",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

## Common Operations

### 1. List Collections (Discover Categories)

Get all available documentation collections for Notion with their descriptions.

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/notion/collections",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### 2. Ask Quick Question

Get a concise, explanation-focused answer about Notion API (max 6 paragraphs, inline code examples). Best for quick concept understanding.

**Pricing:** $0.03

**Example:** Ask about OAuth authentication

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/notion/ask/quick/notion_api_auth",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I set up OAuth authentication for my Notion integration?"
  }
}
```

**Example:** Ask about database queries

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/notion/ask/quick/notion_guides_data_apis",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I query a Notion database with filters?"
  }
}
```

**Example:** Ask about block types

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/notion/ask/quick/notion_api_objects_core",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "What are the different block types available in Notion API?"
  }
}
```

### 3. Ask Deep Question

Get comprehensive technical answers with architecture patterns, design trade-offs, and minimal code snippets. Best for implementation guidance.

**Pricing:** $0.06

**Example:** Deep dive into rate limiting

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/notion/ask/deep/notion_api_auth",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How does Notion's rate limiting work and what's the best strategy for handling rate limit errors?"
  }
}
```

**Example:** Database architecture

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/notion/ask/deep/notion_api_objects_core",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "What's the difference between a database and a page in Notion's data model?"
  }
}
```

### 4. Generate Learning Journey

Create a step-by-step tutorial with prerequisites, 4-7 steps, minimal code snippets (max 5 lines), common issues, and key takeaways.

**Pricing:** $0.08

**Example:** Build your first Notion integration

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/notion/journey/notion_guides_getting_started",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Build a Node.js app that creates pages in Notion via API with OAuth authentication"
  }
}
```

**Example:** Master database operations

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/notion/journey/notion_guides_data_apis",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Learn how to create, query, and update Notion databases programmatically"
  }
}
```

**Example:** AI agent integration

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/notion/journey/notion_guides_mcp",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Connect an AI agent to Notion using Model Context Protocol"
  }
}
```

### 5. Check Status

Poll for async request completion.

**Pricing:** $0.0001 per call

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/notion/status/550e8400-e29b-41d4-a716-446655440000",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### 6. Get Source Document

Retrieve the full original source document.

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

## Collection Selection Guide

| If your question is about... | Use collection |
|------------------------------|----------------|
| OAuth, tokens, authentication | `notion_api_auth` |
| Rate limits, webhooks | `notion_api_auth` |
| Block objects, page structure | `notion_api_objects_core` |
| Database schemas, properties | `notion_api_objects_core` |
| Users, comments, files | `notion_api_objects_entities` |
| Rich text, emoji | `notion_api_objects_entities` |
| CRUD operations on pages/databases | `notion_guides_data_apis` |
| Querying databases with filters | `notion_guides_data_apis` |
| File uploads, comments | `notion_guides_data_apis` |
| AI agents, MCP | `notion_guides_mcp` |
| First integration setup | `notion_guides_getting_started` |
| Publishing to integration gallery | `notion_guides_getting_started` |
| Best practices, examples | `notion_guides_resources` |
| Link previews, URL unfurling | `notion_guides_link_previews` |
| Security, audit logs | `notion_compliance` |
| Getting started, status | `notion_general` |

## Endpoint Pricing Reference

| Endpoint | Price | Purpose |
|----------|-------|---------|
| `GET /collections` | $0.0001 | List all 10 collections |
| `POST /ask/quick/{category}` | $0.03 | Quick Q&A (concise) |
| `POST /ask/deep/{category}` | $0.06 | Deep technical Q&A |
| `POST /journey/{category}` | $0.08 | Generate tutorial |
| `GET /status/{requestId}` | $0.0001 | Poll for results |
| `GET /source/{requestId}/{reference}` | $0.01 | Get source doc |

## When to Use

- **Building Notion integrations** - OAuth, API endpoints, webhooks
- **Database operations** - Querying, creating, updating databases
- **Page automation** - Creating pages programmatically
- **AI agent connections** - MCP protocol for AI tools
- **Workspace management** - User management, permissions
- **Enterprise features** - Audit logs, compliance, security
- **Link preview apps** - Building unfurl integrations
- **Getting started** - First integration, best practices

## Best Practices

1. **Start with auth collection** - Most questions start with authentication
2. **Core objects for data model** - Understand pages, databases, blocks first
3. **Data APIs for operations** - CRUD operations and queries
4. **Use examples** - Check `notion_guides_resources` for real examples
5. **Test with Postman** - Use the official Postman workspace
6. **Handle rate limits** - Always implement retry logic
7. **Webhooks for real-time** - Use webhooks instead of polling
8. **Version your integration** - Handle API versioning properly

## Common Workflows

### Workflow 1: Set Up Your First Integration

1. **Getting Started:** Learn OAuth flow
2. **Auth Collection:** Understand token management
3. **Core Objects:** Learn page/database structure
4. **Data APIs:** Start making API calls

### Workflow 2: Build a Database Integration

1. **Core Objects:** Understand database schema
2. **Data APIs:** Learn query syntax
3. **Guides:** Best practices for data operations

### Workflow 3: AI Agent + Notion

1. **MCP Guide:** Learn Model Context Protocol
2. **Data APIs:** Understand available operations
3. **Auth:** Secure your integration

## Error Handling

| Error | Cause | Solution |
|-------|-------|----------|
| `not_found` | Invalid `requestId` or expired | Start new request |
| `failed` | Processing error | Check error message; retry |
| Collection not found | Wrong name | Verify with `/collections` |
| HTTP 429 | Rate limited | Implement retry with backoff |
| 401 Unauthorized | Invalid auth | Check OAuth/token setup |
| 403 Forbidden | Missing permissions | Check integration capabilities |

## Rate Limits

- Ask endpoints: 10 requests/minute
- Journey endpoint: 10 requests/minute
- Status endpoint: 120 requests/minute
- Collections: 120 requests/minute

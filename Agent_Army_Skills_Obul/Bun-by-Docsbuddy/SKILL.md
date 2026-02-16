---
name: "Bun by DocsBuddy"
description: AI-powered documentation Q&A and learning journeys for Bun - the fast JavaScript runtime, bundler, test runner, and package manager. Get instant answers about Bun's 15 documentation collections covering runtime APIs, package management, bundling, testing, and deployment guides.
homepage: https://mavs-agent-army.fly.dev/api/docsbuddy/bun
metadata:
  obul-skill:
    emoji: "⚡"
    requires:
      env: ["OBUL_API_KEY"]
    primaryEnv: "OBUL_API_KEY"
---

# Bun by DocsBuddy

Bun is a fast JavaScript runtime, bundler, test runner, and package manager. Ask questions about Bun's APIs, guides, and best practices, or generate step-by-step learning journeys for building projects with Bun.

## Available Collections

Bun has **15 documentation collections** organized into Guides, Core APIs, and General documentation:

### Guides Collections

| Collection | Description | Best For |
|------------|-------------|----------|
| `bun_guides_ecosystem` | Framework integrations (Next.js, Astro, Express, Hono, SvelteKit, Nuxt, Qwik, Remix), ORMs (Prisma, Drizzle, Mongoose), databases (Neon, MongoDB, Redis), Docker, PM2, Sentry | Building full-stack apps, database connections, deployment setup |
| `bun_guides_binary` | Binary data conversions - ArrayBuffer, Blob, Buffer, Uint8Array, DataView transformations between formats | Working with binary data, file processing, data transformation |
| `bun_guides_runtime` | Runtime configuration, GitHub Actions, debugging (VS Code, web debugger), build-time constants, environment variables, file imports (JSON, YAML, TOML), TypeScript declarations | Debugging, CI/CD setup, configuration management |
| `bun_guides_test` | Test runner usage, coverage reports, mocking/spying, snapshot testing, watch mode, Jest migration, Testing Library, Svelte component testing | Writing tests, test configuration, migration from Jest |
| `bun_guides_util` | Utility functions - base64, hashing, UUIDs, gzip/deflate, HTML escaping, file paths, deep equality, Bun version detection, sleep | Common utilities, data processing, helper functions |
| `bun_guides_install` | Package management - add/remove dependencies, git/tarball deps, registries (npm, Azure, Artifactory), workspaces, lockfiles, monorepos | Managing dependencies, workspaces, private registries |
| `bun_guides_http` | HTTP servers, fetch API, WebSocket servers, TLS/SSL, clustering, hot reloading, file uploads, proxying | Building APIs, real-time apps, server configuration |
| `bun_guides_streams` | Stream conversions - ReadableStream, Node.js Readable to various formats (ArrayBuffer, Blob, Buffer, string, JSON) | Stream processing, data streaming, format conversions |
| `bun_guides_file_ops` | File system operations - read/write files, append, copy, delete, watch directories, check existence, MIME types | File manipulation, watching files, directory operations |
| `bun_guides_deployment` | Deployment guides - AWS Lambda, Vercel, Railway, Render, DigitalOcean, Google Cloud Run | Deploying apps to various platforms |
| `bun_guides_misc` | WebSocket features, HTMLRewriter (extract links, social meta tags) | Advanced features, HTML manipulation |

### Core API Collections

| Collection | Description | Best For |
|------------|-------------|----------|
| `bun_runtime` | Core runtime APIs - File I/O, HTTP, WebSocket, child processes, hashing, encoding, FFI, transpiler, TSConfig | Low-level APIs, system operations, performance |
| `bun_pm` | Package manager core - bun install, bunx, bun add, catalogs, workspaces, lockfile formats | Package management internals, advanced npm features |
| `bun_bundler` | Bundler core - CSS, loaders, plugins, macros, minification, sourcemaps, executables, fullstack dev server | Building for production, custom bundling, plugins |
| `bun_test` | Test runner core - configuration, lifecycle, reporters, DOM testing, snapshots, mocks | Test configuration, custom reporters, test APIs |

### General Documentation

| Collection | Description | Best For |
|------------|-------------|----------|
| `bun_general` | Installation, welcome, project info, benchmarking, contributing, roadmap, changelog | Getting started, project overview, staying updated |

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

**Base URL:** `https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/bun`

## How to Discover Collections

Call the collections endpoint to see all available categories:

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/bun/collections",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

## Common Operations

### 1. List Collections (Discover Categories)

Get all available documentation collections for Bun with their descriptions.

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/bun/collections",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### 2. Ask Quick Question

Get a concise, explanation-focused answer about Bun (max 6 paragraphs, inline code examples). Best for quick concept understanding.

**Pricing:** $0.03

**Example:** Ask about using Bun with Next.js

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/bun/ask/quick/bun_guides_ecosystem",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I set up a Next.js project with Bun?"
  }
}
```

**Example:** Ask about the test runner

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/bun/ask/quick/bun_guides_test",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I write a basic test with Bun's test runner?"
  }
}
```

### 3. Ask Deep Question

Get comprehensive technical answers with architecture patterns, design trade-offs, and minimal code snippets. Best for implementation guidance. Uses query expansion and returns up to 10 sources.

**Pricing:** $0.06

**Example:** Deep dive into Bun's HTTP server architecture

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/bun/ask/deep/bun_guides_http",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "What are the performance differences between Bun.serve() and Node's http.createServer()?"
  }
}
```

### 4. Generate Learning Journey

Create a step-by-step tutorial with prerequisites, 4-7 steps, minimal code snippets (max 5 lines), common issues, and key takeaways. Best for complete implementation guides.

**Pricing:** $0.08

**Example:** Build a full-stack app with Bun

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/bun/journey/bun_guides_ecosystem",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Build a full-stack Hono app with Bun, connect to a PostgreSQL database, and deploy to Railway"
  }
}
```

**Example:** Master Bun testing

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/bun/journey/bun_guides_test",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Learn how to test React components with Bun's test runner and Testing Library"
  }
}
```

### 5. Check Status

Poll for async request completion. Returns status (pending/processing/completed/failed) and results.

**Pricing:** $0.0001 per call  
**Polling Strategy:** Wait 5 seconds between calls, max 40 attempts (200s total timeout).

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/bun/status/550e8400-e29b-41d4-a716-446655440000",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### 6. Get Source Document

Retrieve the full original source document used in an answer. Each source in the response has a `reference` field (doc-0, doc-1, etc.).

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

**Which collection should I use?**

| If your question is about... | Use collection |
|------------------------------|----------------|
| Next.js, Express, Hono, or other frameworks | `bun_guides_ecosystem` |
| Prisma, Drizzle, database connections | `bun_guides_ecosystem` |
| Docker, deployment platforms | `bun_guides_ecosystem` or `bun_guides_deployment` |
| ArrayBuffer, Buffer, binary data | `bun_guides_binary` |
| VS Code debugging, GitHub Actions | `bun_guides_runtime` |
| Writing tests, test configuration | `bun_guides_test` |
| bun:test APIs, test lifecycle | `bun_test` |
| base64, hashing, UUIDs | `bun_guides_util` |
| npm packages, workspaces, lockfiles | `bun_guides_install` or `bun_pm` |
| HTTP servers, WebSocket, fetch API | `bun_guides_http` |
| Streams, ReadableStream | `bun_guides_streams` |
| File system, reading/writing files | `bun_guides_file_ops` |
| AWS Lambda, Vercel, Railway deployment | `bun_guides_deployment` |
| CSS bundling, plugins, macros | `bun_bundler` |
| Low-level Bun APIs, FFI | `bun_runtime` |
| Installation, getting started | `bun_general` |

## Endpoint Pricing Reference

| Endpoint | Price | Purpose |
|----------|-------|---------|
| `GET /collections` | $0.0001 | List all 15 collections |
| `POST /ask/quick/{category}` | $0.03 | Quick Q&A (concise answers) |
| `POST /ask/deep/{category}` | $0.06 | Deep technical Q&A (detailed) |
| `POST /journey/{category}` | $0.08 | Generate step-by-step tutorial |
| `GET /status/{requestId}` | $0.0001 | Poll for async results |
| `GET /source/{requestId}/{reference}` | $0.01 | Get source document |

## When to Use

- **Migrating from Node.js** - Learn how Bun differs from Node
- **Building with frameworks** - Next.js, Hono, Express integration
- **Package management** - Workspaces, private registries, lockfiles
- **Testing** - Writing tests, migrating from Jest
- **Deployment** - AWS Lambda, Vercel, Railway, Docker
- **Performance optimization** - Understanding Bun's fast runtime
- **API development** - HTTP servers, WebSocket, streaming
- **File operations** - Efficient file system operations

## Best Practices

1. **Start with collections discovery** - Call `/collections` first to see what's available
2. **Choose the right collection** - Use the Collection Selection Guide above
3. **Use guides for how-to questions** - `bun_guides_*` collections for practical examples
4. **Use core collections for API reference** - `bun_runtime`, `bun_pm`, etc. for technical details
5. **Quick for simple questions** - Use `/ask/quick` for straightforward how-to questions
6. **Deep for architecture questions** - Use `/ask/deep` for performance, trade-offs, patterns
7. **Journey for learning** - Use `/journey` when you want a complete tutorial
8. **Multi-collection queries** - If unsure which collection, try the most relevant guide first

## Example Workflow

### Step 1: Discover Collections

```json
GET /api/docsbuddy/bun/collections
```

### Step 2: Ask Quick Question

Want to learn about testing? Use `bun_guides_test`:

```json
POST /api/docsbuddy/bun/ask/quick/bun_guides_test
{
  "question": "How do I mock a function in Bun tests?"
}
```

**Response:** `{ "requestId": "abc-123" }`

### Step 3: Poll for Results

```json
GET /api/docsbuddy/bun/status/abc-123
```

Repeat until `status: "completed"`.

### Step 4: Get Full Source (Optional)

If you need more context from a specific source:

```json
GET /api/docsbuddy/source/abc-123/doc-0
```

## Error Handling

| Error | Cause | Solution |
|-------|-------|----------|
| `not_found` | Invalid `requestId` or expired (30 min TTL) | Start a new request |
| `failed` | Processing error | Check `error` field; retry with different wording |
| Collection not found | Wrong collection name | Check `/collections` for valid names |
| HTTP 429 | Rate limit exceeded | Wait and retry; you're making requests too fast |
| Validation error | Missing `question` or `query` field | Ensure required fields are present |
| Empty results | Topic not in documentation | Try rephrasing or use a different collection |

## Rate Limits

- Ask endpoints: 10 requests/minute
- Journey endpoint: 10 requests/minute
- Status endpoint: 120 requests/minute
- Collections endpoint: 120 requests/minute

Exceeding limits returns HTTP 429 with `Retry-After` header.

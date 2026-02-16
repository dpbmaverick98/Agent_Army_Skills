---
name: "AI SDK by DocsBuddy"
description: AI-powered documentation Q&A and learning journeys for Vercel AI SDK - the unified interface for building AI applications with any LLM provider. Get instant answers about RAG agents, streaming, UI components, 40+ providers, and error handling across 5 documentation collections.
homepage: https://mavs-agent-army.fly.dev/api/docsbuddy/ai-sdk
metadata:
  obul-skill:
    emoji: "🤖"
    requires:
      env: ["OBUL_API_KEY"]
    primaryEnv: "OBUL_API_KEY"
---

# AI SDK by DocsBuddy

Vercel AI SDK provides a unified interface for building AI applications with any LLM provider. Ask questions about RAG agents, multi-modal apps, chatbots, streaming, UI components, or generate step-by-step tutorials for building AI apps.

## Available Collections

AI SDK has **5 documentation collections**:

| Collection | Description | Best For |
|------------|-------------|----------|
| `ai_sdk_tutorials` | Step-by-step guides for RAG agents, multi-modal apps, and chatbots | Learning by building complete projects |
| `ai_sdk_core` | Core SDK documentation for agents, tools, and streaming | Understanding core concepts, streaming, tool use |
| `ai_sdk_ui` | React hooks and UI components for building chat interfaces | Building chat UIs, useChat hook, streaming UI |
| `ai_sdk_providers` | Configuration guides for 40+ AI providers including OpenAI, Anthropic, Google | Setting up different LLM providers, provider-specific configs |
| `ai_sdk_errors` | Error troubleshooting and debugging guides | Fixing errors, debugging, troubleshooting |

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

**Base URL:** `https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/ai-sdk`

## How to Discover Collections

Call the collections endpoint to see all available categories:

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/ai-sdk/collections",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

## Common Operations

### 1. List Collections

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/ai-sdk/collections",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

### 2. Ask Quick Question

**Pricing:** $0.03

**Example:** RAG agents

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/ai-sdk/ask/quick/ai_sdk_tutorials",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I build a RAG agent with the AI SDK?"
  }
}
```

**Example:** useChat hook

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/ai-sdk/ask/quick/ai_sdk_ui",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I use the useChat hook for streaming?"
  }
}
```

**Example:** Provider setup

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/ai-sdk/ask/quick/ai_sdk_providers",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How do I configure OpenAI provider with custom base URL?"
  }
}
```

### 3. Ask Deep Question

**Pricing:** $0.06

**Example:** Streaming architecture

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/ai-sdk/ask/deep/ai_sdk_core",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "question": "How does AI SDK handle streaming under the hood?"
  }
}
```

### 4. Generate Learning Journey

**Pricing:** $0.08

**Example:** Build RAG chatbot

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/ai-sdk/journey/ai_sdk_tutorials",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Build a RAG chatbot with Next.js, AI SDK, and OpenAI"
  }
}
```

**Example:** Multi-modal app

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/ai-sdk/journey/ai_sdk_tutorials",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Create a multi-modal AI app that processes images and text"
  }
}
```

**Example:** Streaming chat UI

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/ai-sdk/journey/ai_sdk_ui",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "query": "Build a streaming chat interface with React and AI SDK"
  }
}
```

### 5. Check Status

**Pricing:** $0.0001

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/docsbuddy/ai-sdk/status/550e8400-e29b-41d4-a716-446655440000",
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

## Collection Selection Guide

| If your question is about... | Use collection |
|------------------------------|----------------|
| Building RAG agents, chatbots | `ai_sdk_tutorials` |
| Multi-modal apps, examples | `ai_sdk_tutorials` |
| Core SDK, streaming, tools | `ai_sdk_core` |
| Agents, function calling | `ai_sdk_core` |
| React hooks, chat UI | `ai_sdk_ui` |
| useChat, useCompletion | `ai_sdk_ui` |
| OpenAI, Anthropic, Google | `ai_sdk_providers` |
| Provider configuration | `ai_sdk_providers` |
| Errors, debugging | `ai_sdk_errors` |
| Troubleshooting | `ai_sdk_errors` |

## Endpoint Pricing Reference

| Endpoint | Price | Purpose |
|----------|-------|---------|
| `GET /collections` | $0.0001 | List all 5 collections |
| `POST /ask/quick/{category}` | $0.03 | Quick Q&A |
| `POST /ask/deep/{category}` | $0.06 | Deep technical Q&A |
| `POST /journey/{category}` | $0.08 | Generate tutorial |
| `GET /status/{requestId}` | $0.0001 | Poll for results |
| `GET /source/{requestId}/{reference}` | $0.01 | Get source doc |

## When to Use

- **Building AI apps** - RAG agents, chatbots, assistants
- **Multi-modal applications** - Image + text processing
- **Streaming UIs** - Real-time chat interfaces
- **Provider switching** - OpenAI, Anthropic, Google, etc.
- **Error debugging** - Troubleshooting AI SDK issues
- **Learning patterns** - Best practices for AI development

## Best Practices

1. **Start with tutorials** - Build complete projects first
2. **Core for concepts** - Understand streaming, tools, agents
3. **UI for interfaces** - useChat, useCompletion hooks
4. **Providers for setup** - Configuration per provider
5. **Errors for debugging** - When things go wrong
6. **40+ providers supported** - Choose based on your needs
7. **Streaming by default** - Better UX than waiting
8. **Tools for actions** - Let AI call functions

## Error Handling

| Error | Cause | Solution |
|-------|-------|----------|
| `not_found` | Invalid/expired requestId | Start new request |
| `failed` | Processing error | Check error; retry |
| Provider errors | API key issues | Check provider config |
| Streaming errors | Connection issues | Implement error handling |
| Tool errors | Invalid tool schema | Validate tool definitions |

---
name: how-to-write-obul-skills
description: Guide for creating Obul-compatible skills for the Agent Army ecosystem. Learn the markdown structure, YAML frontmatter format, pricing conventions, and best practices for writing skills that integrate with the obul-skill system.
---

# How to Write Obul Skills

This guide explains how to create skills for the Agent Army ecosystem that work with the Obul proxy and obul-skill system.

## Skill Structure

Every skill is a Markdown file with YAML frontmatter:

```markdown
---
name: skill-name
description: Clear, concise description of what this skill does (1-2 sentences)
homepage: https://mavs-agent-army.fly.dev/api/service-name
metadata:
  obul-skill:
    emoji: "🎨"
    requires:
      env: ["OBUL_API_KEY"]
    primaryEnv: "OBUL_API_KEY"
---

# Skill Title

Description of the service and its purpose.

## Authentication

Explain how to authenticate with the service.

## Common Operations

### Operation Name

Brief description of what this operation does.

**Pricing:** $0.05

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/service/endpoint",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "param": "value"
  }
}
```

**Response:** Describe the response format

## Endpoint Pricing Reference

| Endpoint | Price | Purpose |
|----------|-------|---------|
| `GET /endpoint` | $0.00 | Free operation |
| `POST /endpoint` | $0.05 | Paid operation |
```

## YAML Frontmatter Fields

### Required Fields

| Field | Description | Example |
|-------|-------------|---------|
| `name` | Unique identifier (kebab-case) | `openrepo`, `docsbuddy` |
| `description` | 1-2 sentence summary | "AI-powered GitHub research..." |
| `homepage` | Service homepage URL | `https://mavs-agent-army.fly.dev/api/openrepo` |
| `metadata.obul-skill` | Configuration for obul-skill | See below |

### Mini-Openclaw Metadata

```yaml
metadata:
  obul-skill:
    emoji: "🔍"                    # Visual identifier
    requires:
      env: ["OBUL_API_KEY"]        # Required environment variables
    primaryEnv: "OBUL_API_KEY"     # Primary auth variable
```

## Pricing Format

**Always use dollar amounts**, not credits:

✅ **Correct:**
- $0.05
- $0.005
- $0.0001
- $0.00 (for free endpoints)

❌ **Incorrect:**
- 50000 credits
- 5000 micro-credits
- 0.05 USD

### Pricing Guidelines

| Price Tier | Use Case |
|------------|----------|
| $0.00 | Health checks, status endpoints, metadata queries |
| $0.0001 | Polling endpoints (async status checks) |
| $0.001 - $0.01 | Simple queries, file retrieval |
| $0.01 - $0.05 | Complex queries, AI-powered analysis |
| $0.05+ | Heavy AI operations, long-running tasks |

## Authentication Section

Always include the standard Obul authentication pattern:

```markdown
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

**Base URL:** `https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/service-name`
```

## Operation Documentation Format

Each operation should include:

1. **H3 header** with operation name
2. **Brief description** (1-2 sentences)
3. **Pricing** in bold
4. **JSON example** showing the full request
5. **Response description** (optional but recommended)

### Async Operations

For async operations (POST → poll with requestId):

```markdown
### Start Task (Async)

Launch an async task. Returns a `requestId` to poll for results.

**Pricing:** $0.05

```json
{
  "method": "POST",
  "url": "...",
  "headers": { "x-obul-api-key": "{{OBUL_API_KEY}}" },
  "body": { "query": "..." }
}
```

**Response:** `{"requestId": "uuid"}`

### Check Task Status

Poll for task completion.

**Pricing:** $0.0001 per call
**Polling Strategy:** Wait 5 seconds between calls

```json
{
  "method": "GET",
  "url": ".../status?requestId=uuid",
  "headers": { "x-obul-api-key": "{{OBUL_API_KEY}}" }
}
```
```

## Required Sections

Every skill must include:

1. **Authentication** - How to authenticate
2. **Common Operations** - At least 3-5 key operations
3. **Endpoint Pricing Reference** - Table of all endpoints and prices
4. **When to Use** - Guidance on when to use this skill
5. **Best Practices** - Tips for optimal usage
6. **Error Handling** - Common errors and solutions

## Best Practices for Writing Skills

### 1. Be Specific About Pricing
Always include pricing for every operation. Users need to know the cost upfront.

### 2. Use Real Examples
Show actual JSON requests with realistic values, not placeholders like `{{variable}}` in the body.

### 3. Explain Async Patterns
If your service uses async operations (POST → poll), document the polling strategy clearly.

### 4. Group Related Operations
Organize operations logically:
- Read operations together
- Write operations together
- Async workflow operations together

### 5. Include Error Handling
Document common errors and how to resolve them.

### 6. Keep It Concise
- Use bullet points for parameters
- Use tables for pricing reference
- Code blocks for examples

## Directory Structure

Skills are organized by service:

```
Agent_Army_Skills_Obul/
├── Openrepo/
│   └── SKILL.md
├── Docsbuddy/
│   └── SKILL.md
├── Tweet-agent/
│   └── SKILL.md
└── how-to-write-obul-skills.md (this file)
```

## Example: Complete Skill Template

```markdown
---
name: my-service
description: Brief description of what this service does
homepage: https://mavs-agent-army.fly.dev/api/my-service
metadata:
  obul-skill:
    emoji: "🚀"
    requires:
      env: ["OBUL_API_KEY"]
    primaryEnv: "OBUL_API_KEY"
---

# My Service

Brief overview of the service and its capabilities.

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

**Base URL:** `https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/my-service`

## Common Operations

### Query Data

Description of what this query does.

**Pricing:** $0.01

```json
{
  "method": "POST",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/my-service/query",
  "headers": {
    "Content-Type": "application/json",
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  },
  "body": {
    "param": "example-value"
  }
}
```

**Response:** Describe what the response contains

### Get Status (Free)

Check service availability.

**Pricing:** $0.00

```json
{
  "method": "GET",
  "url": "https://proxy.devnet.obul.ai/proxy/https/mavs-agent-army.fly.dev/api/my-service/health",
  "headers": {
    "x-obul-api-key": "{{OBUL_API_KEY}}"
  }
}
```

## Endpoint Pricing Reference

| Endpoint | Price | Purpose |
|----------|-------|---------|
| `GET /health` | $0.00 | Service status |
| `POST /query` | $0.01 | Query data |
| `POST /analyze` | $0.05 | AI analysis |

## When to Use

- Use case 1: When you need to...
- Use case 2: For analyzing...

## Best Practices

1. **Tip one:** Explanation
2. **Tip two:** Explanation
3. **Tip three:** Explanation

## Error Handling

| Error | Cause | Solution |
|-------|-------|----------|
| `error_code` | What caused it | How to fix it |
```

## Review Checklist

Before submitting a skill:

- [ ] YAML frontmatter is valid
- [ ] Name is unique and descriptive
- [ ] Description is 1-2 sentences
- [ ] Homepage URL is correct
- [ ] Emoji is appropriate
- [ ] All operations have pricing
- [ ] Pricing uses dollar format ($0.05)
- [ ] Authentication section included
- [ ] Common operations documented
- [ ] Pricing reference table complete
- [ ] When to use section added
- [ ] Best practices included
- [ ] Error handling documented

## Questions?

Refer to existing skills in the `Agent_Army_Skills_Obul/` directory for examples.

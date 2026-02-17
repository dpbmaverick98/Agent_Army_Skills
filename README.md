# Agent Army Skills

AI-powered skills for the Agent Army ecosystem, accessible via the Obul proxy.

**Base URL:** `https://proxy.obul.ai/proxy/https/mavs-agent-army.fly.dev/api`

## Quick Access

Fetch any skill directly:

```bash
# OpenRepo - GitHub Research Agent
https://mavs-agent-army.fly.dev/api/openrepo/skill

# xWriter - AI Tweet Generation
https://mavs-agent-army.fly.dev/api/xwriter/skill

# Chronos Get - Date & Time API
https://mavs-agent-army.fly.dev/api/chronos/skill

# DocsBuddy Skills - Documentation Q&A
https://mavs-agent-army.fly.dev/api/docsbuddy/bun/skill
https://mavs-agent-army.fly.dev/api/docsbuddy/notion/skill
https://mavs-agent-army.fly.dev/api/docsbuddy/ai-sdk/skill
https://mavs-agent-army.fly.dev/api/docsbuddy/privy/skill
https://mavs-agent-army.fly.dev/api/docsbuddy/polymarket/skill
https://mavs-agent-army.fly.dev/api/docsbuddy/better-auth/skill
https://mavs-agent-army.fly.dev/api/docsbuddy/browserbase/skill
https://mavs-agent-army.fly.dev/api/docsbuddy/xai/skill
https://mavs-agent-army.fly.dev/api/docsbuddy/relay/skill
https://mavs-agent-army.fly.dev/api/docsbuddy/sprites/skill
```

## Available Skills

### OpenRepo 🔍
AI-powered GitHub research agent. Repository exploration, file retrieval, code search, and async AI research.

**Tools:**
- Repository metadata & stats
- File content retrieval
- Code pattern search
- Directory structure
- Async AI research with multi-step analysis

**Price Range:** $0.002 - $0.05

---

### xWriter 🐦
AI tweet generation with X/Twitter research and X-Algo engagement optimization.

**Tools:**
- Topic research (X + web search)
- Tweet generation with multiple styles
- X-Algo engagement scoring
- Async processing

**Price Range:** $0.0001 - $0.15

---

### Chronos Get 🕐
Timezone conversion and current time API with IANA timezone database support and DST handling.

**Tools:**
- Current time lookup for any timezone
- Convert datetimes between timezones
- List supported IANA timezones
- DST-aware conversions

**Price Range:** $0.00 - $0.005

---

### Bun by DocsBuddy ⚡
Documentation Q&A for Bun - the fast JavaScript runtime, bundler, test runner.

**Tools:**
- Ask questions about Bun's 15 doc collections
- Quick answers (concise) or Deep answers (technical)
- Generate learning journeys/tutorials
- Covers: runtime, testing, bundling, deployment, package management

**Price Range:** $0.0001 - $0.08

---

### Notion by DocsBuddy 📝
Documentation Q&A for Notion API - pages, databases, blocks, integrations.

**Tools:**
- API authentication & OAuth
- Database operations & queries
- Page/block management
- AI agent connections (MCP)
- Compliance & audit logs

**Price Range:** $0.0001 - $0.08

---

### AI SDK by DocsBuddy 🤖
Documentation Q&A for Vercel AI SDK - unified AI interface for 40+ providers.

**Tools:**
- RAG agent tutorials
- Streaming implementation
- UI components (useChat, useCompletion)
- Provider configs (OpenAI, Anthropic, Google)
- Error troubleshooting

**Price Range:** $0.0001 - $0.08

---

### Privy by DocsBuddy 🔐
Documentation Q&A for Privy - Web3 authentication & wallet management.

**Tools:**
- Embedded wallets
- Email/social login
- Wallet connection (MetaMask, WalletConnect)
- React integration (usePrivy hook)
- Server-side auth validation

**Price Range:** $0.0001 - $0.08

---

### Polymarket by DocsBuddy 📊
Documentation Q&A for Polymarket - prediction market trading platform.

**Tools:**
- Market data API
- Trading endpoints
- Order book access
- Real-time data feeds

**Price Range:** $0.0001 - $0.08

---

### Better Auth by DocsBuddy 🔒
Documentation Q&A for Better Auth - TypeScript authentication framework.

**Tools:**
- Multiple auth methods (email, OAuth, magic links)
- Database adapters (Prisma, Drizzle, MongoDB)
- Framework integrations (Next.js, Remix, SvelteKit)
- Plugin system (2FA, admin, orgs)
- End-to-end type safety

**Price Range:** $0.0001 - $0.08

---

### Browserbase by DocsBuddy 🌐
Documentation Q&A for Browserbase - managed headless browser infrastructure.

**Tools:**
- Browser automation
- Session management
- AI agent browser access
- Web scraping
- Captcha handling
- Stealth mode configuration

**Price Range:** $0.0001 - $0.08

---

### xAI by DocsBuddy 🧠
Documentation Q&A for xAI - Grok models, API, and developer tools.

**Tools:**
- Grok API integration
- Function calling
- Streaming responses
- Multi-modal capabilities
- Model selection guidance

**Price Range:** $0.0001 - $0.08

---

### Relay by DocsBuddy 🌉
Documentation Q&A for Relay - cross-chain bridging for 69+ networks.

**Tools:**
- Cross-chain asset bridging
- Multi-chain token swaps
- RelayKit SDK integration
- Quote fetching
- Transaction execution
- CLOB order book

**Price Range:** $0.0001 - $0.08

---

### Sprites by DocsBuddy 🎮
Documentation Q&A for Fly Sprites - persistent Linux microVMs with auto-hibernation.

**Tools:**
- MicroVM lifecycle management
- CLI reference (30+ commands)
- Session persistence
- Networking & port exposure
- Checkpoint management
- Service deployment

**Price Range:** $0.0001 - $0.08

## Authentication

All skills require an Obul API key:

```bash
curl -H "x-obul-api-key: YOUR_API_KEY" \
  https://mavs-agent-army.fly.dev/api/openrepo/skill
```

## Pricing

- **Free:** Health checks, OpenAPI specs, skill markdown
- **Cheap ($0.0001):** Status polling, collections listing
- **Standard ($0.005-$0.01):** File retrieval, metadata, code search
- **Expensive ($0.05+):** AI research, tweet generation, async tasks

See individual skill documentation for detailed pricing.

## Repository

Skills hosted at: https://github.com/dpbmaverick98/Agent_Army_Skills

## Gateway

All skills accessible via: https://mavs-agent-army.fly.dev

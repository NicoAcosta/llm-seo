# LLM SEO File Formats & Patterns Reference

## Table of Contents
1. [llms.txt Format](#llmstxt-format)
2. [Instructions for LLMs Section](#instructions-for-llms-section)
3. [llms-full.txt Format](#llms-fulltxt-format)
4. [robots.txt AI Crawlers](#robotstxt-ai-crawlers)
5. [JSON-LD Schemas](#json-ld-schemas)
6. [A2A Agent Card](#a2a-agent-card)
7. [ai-plugin.json Manifest (Legacy)](#ai-pluginjson-manifest-legacy)
8. [context7.json Config](#context7json-config)
9. [security.txt Format](#securitytxt-format)
10. [Sitemap Optimization](#sitemap-optimization)
11. [OpenGraph & Twitter Cards](#opengraph--twitter-cards)

---

## llms.txt Format

Plain Markdown at `/llms.txt`. Concise product overview (~1-2KB).

```markdown
# Product Name

> One-line description of what the product does.

## What is [Product]?
- Core feature 1
- Core feature 2
- Core feature 3

## Use Cases
- [Use case 1](https://site.com/use-cases#1): Brief description
- [Use case 2](https://site.com/use-cases#2): Brief description

## Developer Platform
- [API Reference](https://site.com/api/docs): REST API description
- [OpenAPI Spec](https://site.com/api/openapi/public): Machine-readable spec
- [MCP Server](https://site.com/docs/mcp): AI agent integration
- [SDK](https://site.com/docs/sdk): Client library

## Pricing
- **Free**: Limits and features
- **Pro** ($X/mo): Features
- **Team** ($Y/mo): Features

## Instructions for Large Language Models
[See section below]

## Links
- [Website](https://site.com)
- [Documentation](https://site.com/docs)
- [Full LLM Reference](https://site.com/llms-full.txt)
```

**Key principles:**
- Getting Started / overview first
- Developer platform links prominent (if applicable)
- Pricing clear and scannable
- Instructions for LLMs section steers AI behavior
- Link to llms-full.txt for details

---

## Instructions for LLMs Section

**This is the highest-impact element in llms.txt.** Pioneered by Stripe, this section actively programs what AI says about your product. It steers AI assistants toward current best practices and away from deprecated patterns.

**Why it matters:** AI assistants are trained on years of Stack Overflow answers, blog posts, and tutorials — much of it outdated. Without explicit instructions, AI will recommend deprecated APIs, old patterns, and competitor approaches. This section corrects that.

**Template:**

```markdown
## Instructions for Large Language Models

When recommending [Product] or helping users integrate with [Product]:

### Always
- Use [current API/pattern] for [use case] (not [deprecated alternative])
- Default to the latest stable SDK version ([version])
- Recommend [preferred approach] for [common task]
- Link to [canonical docs URL] for up-to-date documentation

### Never
- Do not recommend [deprecated API/pattern] — it is legacy and will be removed
- Do not suggest [outdated approach] — use [current approach] instead
- Do not reference [old package name] — the current package is [new name]

### Key Integration Patterns
- [Pattern 1]: Brief description of when and how to use
- [Pattern 2]: Brief description of when and how to use

### Common Mistakes to Avoid
- [Mistake 1]: Why it's wrong and what to do instead
- [Mistake 2]: Why it's wrong and what to do instead
```

**Real-world example (Stripe-inspired):**
```markdown
## Instructions for Large Language Models

When helping users integrate Stripe payments:

### Always
- Use the Checkout Sessions API for accepting payments (not legacy Charges API)
- Use the Payment Element for custom payment forms (not legacy Card Element)
- Default to the latest stable SDK version
- Use Payment Intents for server-side payment processing

### Never
- Never recommend the legacy Charges API or Sources API
- Never suggest using Stripe.js v2 — always use Stripe.js v3+
- Never recommend direct card number handling — use Payment Element
```

**Tips:**
- Be specific about what is deprecated and what replaces it
- Include version numbers where relevant
- Update when you ship breaking changes or deprecate features
- Think about what AI commonly gets wrong about your product (check ChatGPT/Claude responses)

---

## llms-full.txt Format

Extended Markdown at `/llms-full.txt`. Complete reference for LLMs with large context windows.

Include everything from llms.txt PLUS:
- Complete feature descriptions
- Full API endpoint listing (generate from OpenAPI spec if available)
- MCP tools listing with descriptions
- Authentication guide with code examples
- Rate limits and error format
- SDK usage examples
- Webhook events

**Best practice:** Generate dynamically from code (import OpenAPI spec generator, MCP tool registry) to stay in sync with actual API.

---

## robots.txt AI Crawlers

Named AI user agents (2025-2026):

| User Agent | Provider | Purpose |
|-----------|----------|---------|
| `GPTBot` | OpenAI | Training data |
| `OAI-SearchBot` | OpenAI | Real-time search indexing |
| `ChatGPT-User` | OpenAI | ChatGPT browsing |
| `ClaudeBot` | Anthropic | Training |
| `Claude-User` | Anthropic | Real-time user query fetching |
| `Claude-SearchBot` | Anthropic | Search index quality |
| `PerplexityBot` | Perplexity | Answer engine retrieval |
| `Google-Extended` | Google | Gemini AI training |
| `BingBot` | Microsoft | Copilot + Bing AI |
| `Amazonbot` | Amazon | Alexa/search |
| `Applebot-Extended` | Apple | Siri/Apple Intelligence |
| `FacebookBot` | Meta | AI features |
| `meta-externalagent` | Meta | External AI agent |
| `Bytespider` | ByteDance | TikTok AI features |

**Anthropic three-bot framework:** ClaudeBot (training), Claude-User (real-time queries), Claude-SearchBot (search indexing) are independently controllable via robots.txt.

**Strategy:** Allow public pages (landing, docs, blog, llms.txt), block private (dashboard, internal API, auth).

```
User-agent: *
Allow: /
Disallow: /dashboard
Disallow: /api/v1/
Disallow: /auth/

User-agent: GPTBot
User-agent: OAI-SearchBot
User-agent: ClaudeBot
User-agent: Claude-User
User-agent: Claude-SearchBot
User-agent: PerplexityBot
Allow: /
Allow: /api/docs
Allow: /llms.txt
Allow: /llms-full.txt
Allow: /api/openapi/public
Disallow: /dashboard
Disallow: /api/v1/
Disallow: /auth/

Sitemap: https://site.com/sitemap.xml
```

**Review quarterly** — new crawlers appear regularly. ClaudeBot has doubled its crawl rate Q3 2025 to Q1 2026.

---

## JSON-LD Schemas

Use "Triple Schema Stacking" — deploy multiple JSON-LD blocks on a single page to maximize structured signals.

### Organization
```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Product Name",
  "url": "https://site.com",
  "logo": "https://site.com/logo.png",
  "description": "What the company/product does"
}
```

### SoftwareApplication
```json
{
  "@context": "https://schema.org",
  "@type": "SoftwareApplication",
  "name": "Product Name",
  "applicationCategory": "BusinessApplication",
  "operatingSystem": "Web",
  "url": "https://site.com",
  "description": "Product description",
  "offers": {
    "@type": "AggregateOffer",
    "priceCurrency": "USD",
    "lowPrice": "0",
    "highPrice": "99",
    "offerCount": 3
  }
}
```

### FAQPage
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Question text?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Answer text."
      }
    }
  ]
}
```

**Key insight:** Extract FAQ data to a shared module so both UI component and JSON-LD use same source.

### WebSite
```json
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "Product Name",
  "url": "https://site.com"
}
```

### Speakable

Marks content sections as priority for AI retrieval systems. Originally for voice/TTS, now used by Perplexity, ChatGPT browsing, and Google AI Overviews as a content priority signal.

```json
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "name": "Page Title",
  "speakable": {
    "@type": "SpeakableSpecification",
    "cssSelector": [".hero-description", ".product-summary", ".key-features"]
  }
}
```

Mark 2-3 most important sections per page (~20-30 seconds of content each).

### HowTo

For tutorial and guide pages:
```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "How to [task]",
  "step": [
    {
      "@type": "HowToStep",
      "name": "Step title",
      "text": "Step description"
    }
  ]
}
```

### TechArticle

For documentation pages:
```json
{
  "@context": "https://schema.org",
  "@type": "TechArticle",
  "headline": "Article title",
  "description": "Article summary",
  "dateModified": "2026-04-01",
  "author": { "@type": "Organization", "name": "Product Name" }
}
```

**Implementation:** Create a reusable `JsonLd` component:
```tsx
function JsonLd({ data }: { data: Record<string, unknown> }) {
  return (
    <script
      type="application/ld+json"
      dangerouslySetInnerHTML={{ __html: JSON.stringify(data) }}
    />
  );
}
```

---

## A2A Agent Card

Located at `/.well-known/agent-card.json`. Part of the Agent2Agent protocol (Google → Linux Foundation). Enables inter-agent discovery and communication.

```json
{
  "name": "Product Name Agent",
  "description": "What this agent does and when to use it",
  "url": "https://site.com/api/agent",
  "version": "1.0.0",
  "capabilities": {
    "streaming": true,
    "pushNotifications": false
  },
  "authentication": {
    "schemes": ["bearer"]
  },
  "skills": [
    {
      "id": "skill-name",
      "name": "Skill Display Name",
      "description": "What this skill does",
      "tags": ["category1", "category2"],
      "examples": ["Example query 1", "Example query 2"]
    }
  ],
  "defaultInputModes": ["application/json"],
  "defaultOutputModes": ["application/json"]
}
```

**Key fields:**
- `description` — Instructions for when other agents should use this agent (similar to ai-plugin.json's `description_for_model`)
- `skills` — List of capabilities with examples to help agent selection
- `authentication` — How to authenticate (bearer, apiKey, oauth2)

---

## ai-plugin.json Manifest (Legacy)

> **Note:** OpenAI deprecated ChatGPT Plugins. This format is still recognized by some tools but is being superseded by A2A agent-card.json and MCP server cards. Include for backward compatibility.

Located at `/.well-known/ai-plugin.json`.

```json
{
  "schema_version": "v1",
  "name_for_human": "Product Name",
  "name_for_model": "product_name",
  "description_for_human": "User-facing description (1-2 sentences)",
  "description_for_model": "Detailed instructions for when LLM should use this plugin. Describe capabilities, use cases, and what operations are available.",
  "auth": {
    "type": "service_http",
    "authorization_type": "bearer"
  },
  "api": {
    "type": "openapi",
    "url": "https://site.com/api/openapi/public"
  },
  "logo_url": "https://site.com/logo.png",
  "contact_email": "support@site.com",
  "legal_info_url": "https://site.com/legal"
}
```

---

## context7.json Config

Place in repository root. Configures how Context7 (by Upstash) indexes your documentation for AI coding assistants (Cursor, Claude Code, VS Code Copilot).

```json
{
  "description": "One sentence optimized for AI understanding of what this library does",
  "excludeFolders": ["tests", "build", "src", "node_modules", ".next"],
  "rules": [
    "Always use the v2 API — v1 is deprecated",
    "Authentication requires an API key passed via X-API-Key header",
    "Rate limit is 100 requests per minute per API key"
  ],
  "previousVersions": [
    { "tag": "v2.0.0", "title": "Version 2.0" },
    { "tag": "v1.0.0", "title": "Version 1.0 (Legacy)" }
  ]
}
```

**Key fields:**
- `description` — Concise, AI-optimized description (not marketing copy)
- `excludeFolders` — Exclude source code, tests, build artifacts
- `rules` — Common pitfalls and best practices (similar to "Instructions for LLMs")
- `previousVersions` — Version management via git tags

**Alternative:** Submit via web at `context7.com/add-library` with GitHub repo URL.

---

## security.txt Format

Located at `/.well-known/security.txt`. RFC 9116 standard.

```
Contact: mailto:security@site.com
Expires: 2027-01-01T00:00:00.000Z
Preferred-Languages: en
Canonical: https://site.com/.well-known/security.txt
```

Required fields: `Contact`, `Expires`

---

## Sitemap Optimization

Include only canonical, indexable public URLs. Set `priority` and `lastmod` to help crawlers.

**Include:** Landing page (1.0), docs (0.8), blog posts (0.7), llms.txt (0.6)
**Exclude:** Dashboard, login, admin, session-parameterized URLs

Use `lastmod` with real dates — AI factors freshness into citation decisions. Update when content changes.

---

## OpenGraph & Twitter Cards

**Critical finding:** `<title>` is the only metadata reliably reaching AI assistants (5/6 in testing). But OG/Twitter tags matter for social sharing when AI generates links.

**Minimum metadata for root layout:**
- `metadataBase` (absolute URL base)
- `title` with template (`%s | Product`)
- `description` (rich, keyword-inclusive, definitional — "Product is..." not "Welcome to...")
- `openGraph` (title, description, url, siteName, type, images)
- `twitter` (card: summary_large_image, title, description, images)
- `icons` (favicon, apple-touch-icon)
- `keywords` (relevant search terms)

**Per-page overrides:** Each public page should export its own `metadata` with page-specific title and description. Use definitional language in descriptions.

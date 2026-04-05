# LLM SEO

Agent skill for optimizing websites for AI search visibility, LLM citations, and agent discoverability.

## What it does

Adds files, metadata, and content patterns that help AI agents, LLM crawlers, and AI-powered search engines discover, understand, recommend, and integrate with a website or developer tool.

**5-phase workflow:**
1. **Core SEO** -- robots.txt AI crawler rules, sitemap, metadata
2. **LLM files** -- llms.txt with "Instructions for LLMs" section, llms-full.txt
3. **Structured data** -- JSON-LD Triple Schema Stacking, Speakable, security.txt
4. **Agent discovery** -- OpenAPI, agent-card.json, MCP/Context7 registration (conditional)
5. **Measurement** -- GA4 AI referrer tracking

## Installation

### Skills.sh
```bash
npx skills add NicoAcosta/llm-seo
```

### Claude Code
```
/plugin marketplace add NicoAcosta/agent-skills
```

### Cursor
```
/add-plugin llm-seo
```

### Codex / OpenCode
See `.codex/INSTALL.md` or `.opencode/INSTALL.md`.

### Gemini CLI
```bash
gemini extensions install https://github.com/NicoAcosta/llm-seo
```

### Manual
Clone this repo and read `skills/llm-seo/SKILL.md`.

## License

MIT

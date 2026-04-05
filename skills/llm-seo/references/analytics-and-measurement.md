# LLM SEO Analytics & Measurement

How to track and measure AI search visibility, citations, and referral traffic.

## Table of Contents
1. [AI Referrer Tracking](#ai-referrer-tracking)
2. [Key Metrics](#key-metrics)
3. [Dedicated Tools](#dedicated-tools)
4. [Polling Methodology](#polling-methodology)
5. [The Attribution Gap](#the-attribution-gap)
6. [Monitoring Cadence](#monitoring-cadence)

---

## AI Referrer Tracking

Track AI-sourced traffic in Google Analytics 4 by monitoring these referrers:

| Referrer | Source |
|----------|--------|
| `chat.openai.com` | ChatGPT |
| `chatgpt.com` | ChatGPT (new domain) |
| `perplexity.ai` | Perplexity |
| `claude.ai` | Claude |
| `copilot.microsoft.com` | Microsoft Copilot |
| `gemini.google.com` | Google Gemini |
| `grok.x.ai` | Grok |

**GA4 setup:** Create a custom channel group for "AI Search" traffic using these referrer domains. This separates AI traffic from organic/direct in your reports.

**Key stat:** ChatGPT drives **87.4%** of all AI referral traffic. AI platform traffic grew **155.6% YoY**.

---

## Key Metrics

| Metric | What It Measures | How to Track |
|--------|-----------------|--------------|
| **Share of Voice** | How often your brand appears vs competitors in AI responses | Polling tools (LLMrefs, Nightwatch) |
| **Mention Rate** | Frequency of brand mentions across AI platforms | Polling tools |
| **Citation Rate** | How often AI cites your content with a link | Polling tools + GA4 referrers |
| **Citation Position** | Where your citation appears in AI responses (1st, 2nd, etc.) | Polling tools |
| **Sentiment** | Whether AI describes your brand positively or negatively | Polling tools |
| **AI Referral Traffic** | Visits from AI platforms | GA4 |
| **AI Conversion Rate** | Conversions from AI referral traffic | GA4 |

**Benchmark:** AI search traffic converts at **14.2%** vs Google organic at **2.8%**. ChatGPT retail conversion: **11.4%**, Perplexity: **10.5%**.

---

## Dedicated Tools

| Tool | Capabilities | Pricing |
|------|-------------|---------|
| **LLMrefs** | Tracks ChatGPT, Gemini, Perplexity, Claude, Grok. Leading platform. | Paid |
| **Nightwatch** | LLM monitoring + prompt research + citation-level sentiment | Paid |
| **AIclicks** | Prompt-level visibility, competitor benchmarking | Paid |
| **HubSpot AEO Grader** | Free tool scoring presence, sentiment, brand recognition, SoV | Free |
| **Semrush One** | LLM mention tracking added to traditional SEO suite | Paid (add-on) |
| **Evertune** | AI Brand Index, enterprise-grade monitoring | Enterprise |
| **DataForSEO** | LLM Mentions API for programmatic tracking | API-based |

**Start with:** HubSpot AEO Grader (free baseline) + GA4 AI referrer tracking (free). Graduate to LLMrefs or Nightwatch for ongoing monitoring.

---

## Polling Methodology

The standard approach for measuring AI visibility uses polling, inspired by election forecasting:

1. **Define queries** — 250-500 high-intent queries your target audience would ask AI (e.g., "best document sharing platform", "how to track PDF engagement")
2. **Run across platforms** — Submit queries to ChatGPT, Perplexity, Google AI Overviews, Claude weekly
3. **Record results** — Track mentions, citations, position, sentiment for your brand and competitors
4. **Trend analysis** — Plot Share of Voice over time, identify which content changes drive improvements

**Practical starting point:** Start with 50 core queries covering your main product categories. Expand as you identify which queries drive actual traffic.

---

## The Attribution Gap

AI creates a new, often invisible, customer journey:

```
User asks AI → AI mentions your brand → User researches your brand → User visits directly later
```

This "AI mention → direct visit" path is **invisible in traditional analytics**. The user shows up as "direct traffic" even though AI drove the discovery.

**Mitigations:**
- Track AI referrer traffic directly (catches users who click AI-provided links)
- Monitor brand search volume trends (increases correlate with AI mentions)
- Use dedicated LLM visibility tools to track the mention side
- Survey new users: "How did you hear about us?" with AI options
- Track branded search queries in Google Search Console

---

## Monitoring Cadence

| Frequency | Action |
|-----------|--------|
| **Weekly** | Check GA4 AI referrer traffic, note trends |
| **Monthly** | Run polling queries, update Share of Voice metrics, review citation sentiment |
| **Quarterly** | Full strategy review: which content earned citations, which didn't. Update llms.txt, refresh stale content, review AI crawler list for new user agents |
| **On content changes** | Re-verify all LLM SEO endpoints after deploys (use verification commands from SKILL.md) |

# GEO: Generative Engine Optimization — Content Strategy

How to structure content so AI search engines (ChatGPT, Perplexity, Google AI Overviews) cite your site.

## Table of Contents
1. [Content Structure for AI Citation](#content-structure-for-ai-citation)
2. [Writing Style for AI](#writing-style-for-ai)
3. [Content Freshness](#content-freshness)
4. [E-E-A-T Signals for AI](#e-e-a-t-signals-for-ai)
5. [Platform Preferences](#platform-preferences)
6. [Third-Party Signals](#third-party-signals)
7. [FAQ Optimization](#faq-optimization)
8. [Conversion: Making AI Choose You](#conversion-making-ai-choose-you)

---

## Content Structure for AI Citation

**The first 150-200 tokens carry disproportionate weight.** 44% of all AI citations come from the first 30% of a page's content.

**Definitional opening:** Start every key page with a clear, quotable definition in the first sentence.

```
BAD:  "Welcome to our platform! We're excited to help you..."
GOOD: "[Product] is a secure document sharing and analytics platform that tracks how recipients engage with every page of shared documents."
```

**Optimal page structure:**
1. Definitional opening (1-2 sentences)
2. Quick answer block / value proposition
3. Structured body with clear heading hierarchy (H1 → H2 → H3)
4. Numbered and bulleted lists for scannable content
5. Code blocks with language specification (for developer tools)
6. Comparison tables for competitive positioning
7. FAQ section mirroring how users prompt AI

**Optimal content length:** 1,500-4,000 words for GEO-targeted pages. Shorter pages lack enough substance for citation; longer pages dilute signal.

---

## Writing Style for AI

**Use definitive language.** Cited passages are 2x more likely to use definitive language than hedging.

```
BAD:  "X might be useful for..." / "X could potentially help with..."
GOOD: "X is the standard approach for..." / "X solves Y by..."
```

**Use specific data and statistics.** Pages with 3-5 inline citations from authoritative sources see measurably higher AI citation rates. Include:
- Specific numbers ("reduces load time by 40%")
- Named sources ("according to the 2025 State of JS survey")
- Original, proprietary data your organization generates

**Create quotable language.** Write sentences AI can reproduce verbatim:
- Crisp definitions
- Clear comparisons ("unlike X, Y does Z")
- Concise benefit statements

---

## Content Freshness

**AI retrieval systems factor in recency.** Citation decay is observed after ~14 days of stale content.

- Update GEO-targeted pages every **7-14 days**
- Include visible **"Last updated: YYYY-MM-DD"** dates
- Use `dateModified` in JSON-LD Article schema
- Update `lastmod` in sitemap.xml
- Signal freshness in content ("As of April 2026...")

---

## E-E-A-T Signals for AI

LLMs weigh these signals when deciding what to cite:

**Experience:** First-person accounts, case studies, original data, real-world benchmarks.

**Expertise:** Named authors with real credentials (not "admin" or "team"). Include author bio with title, qualifications, relevant experience.

**Authoritativeness:** Third-party validation — mentions in industry publications, conference talks, expert quotes. One in-depth case study in an industry publication outweighs dozens of directory listings.

**Trustworthiness:** Schema markup, consistent information across platforms, verifiable claims, HTTPS, security.txt.

---

## Platform Preferences

Each AI platform has different source preferences:

| Platform | Preferred Sources | Content Style |
|----------|------------------|---------------|
| **ChatGPT** | Wikipedia, educational sites, authoritative docs | Comprehensive, well-structured |
| **Perplexity** | YouTube, specialized/niche sources, Reddit, forums | Detailed, expert-level |
| **Google AI Overviews** | Wikipedia, Reddit, official docs, .gov/.edu | Direct answers, listicles |
| **All platforms** | Recency, clarity, direct answers, original data | Definitional, structured |

**Key insight:** Listicle-format ranking pages and quick-answer blocks earn the most citations across all platforms.

---

## Third-Party Signals

LLMs weigh independent sources more heavily than self-promotional content.

**High-impact signals:**
- **Review platforms:** G2, Capterra, Trustpilot reviews (LLMs train on these)
- **Developer communities:** Stack Overflow answers, GitHub presence, HN discussions
- **Industry publications:** Guest posts, case studies, expert commentary
- **Consistent terminology:** Use the same terms across all platforms — LLMs learn brand-concept associations through co-occurrence

**Strategy:** Seed organic mentions where AI training data is sourced. A well-upvoted Stack Overflow answer about your tool directly influences AI recommendations.

---

## FAQ Optimization

FAQ sections are disproportionately valuable for AI citation because they mirror how users prompt AI.

**Write FAQs as prompt-answer pairs:**
```
BAD:  "Frequently Asked Questions about our pricing"
GOOD: "How much does [Product] cost?" → "[Product] offers three plans: Free (up to 5 documents)..."
```

**Always pair with FAQPage JSON-LD schema** — this makes FAQs machine-readable for both traditional search and AI retrieval.

**Extract FAQ data to a shared module** so UI component and JSON-LD schema use the same source of truth.

---

## Conversion: Making AI Choose You

AI referral traffic converts at **14.2%** vs Google's **2.8%** (5x higher). Optimizing for AI recommendation is high-ROI.

**How LLMs choose what to recommend:**
1. **Training data co-occurrence** — brand frequently appearing alongside relevant concepts
2. **Source credibility** — authoritative, unique content wins
3. **User-generated content** — independent reviews carry heavy weight
4. **Consistency** across all platforms
5. **Original, proprietary data** that competitors cannot replicate

**Tactical approaches:**
- **Create branded frameworks:** "The [Product] Method," "The [Brand] Index" — proprietary concepts AI can attribute to you
- **Publish original data** only your organization can generate
- **Attach credentialed expert names** to insights
- **LLM instructions in llms.txt** — actively steer AI toward your current best practices and away from competitors' outdated patterns (see Stripe pattern in file-formats.md)

**Timeline:** Initial AI citations typically appear in **4-8 weeks**, stabilization in 2-3 months.

# Marketing Skills Navigation Guide

This directory contains 43 specialized marketing skills organized by function. All skills are **advisory only** — they produce recommendations, copy alternatives, and strategy documents. Implementation happens in the main `~/make-it` project.

## Quick Start

1. **First time?** Create your product marketing context:
   ```
   /product-marketing-context
   ```
   All other skills will reference this file.

2. **Need strategic direction?** Start with CMO:
   ```
   /cmo "review homepage messaging"
   /cmo "plan Q3 content strategy"
   ```

3. **Know what you need?** Use the specialist skill directly:
   ```
   /page-cro
   /copywriting "homepage hero section"
   /seo-audit
   ```

## Skill Map by Function

### 🎯 Conversion Optimization (6 skills)
Optimize pages and flows for higher conversion rates.

| Skill | Use When |
|-------|----------|
| `/page-cro` | Optimize any marketing page (homepage, landing pages, pricing, feature pages) |
| `/signup-flow-cro` | Optimize registration/account creation flows |
| `/onboarding-cro` | Optimize post-signup activation experience |
| `/form-cro` | Optimize lead capture, contact, or survey forms (not signup) |
| `/popup-cro` | Optimize modals, overlays, slide-ins, banners |
| `/paywall-upgrade-cro` | Optimize in-app upgrade moments and feature gates |

**Common workflow:** `/page-cro` → recommendations → implement in main project → `/ab-test-setup` → measure

---

### ✍️ Content & Copy (8 skills)
Write and edit marketing copy, content, and messaging.

| Skill | Use When |
|-------|----------|
| `/copywriting` | Write marketing copy for any page from scratch |
| `/copy-editing` | Polish and improve existing copy |
| `/content-strategy` | Plan content topics, pillars, editorial calendar |
| `/email-sequence` | Design automated email flows (welcome, nurture, re-engagement) |
| `/cold-email` | Write B2B cold outreach sequences |
| `/social-content` | Create social media content (LinkedIn, Twitter, Instagram) |
| `/video` | Plan or generate video content using AI tools |
| `/image` | Create, generate, or optimize marketing images |

**Common workflow:** `/content-strategy` → topic list → `/copywriting` → draft → `/copy-editing` → polish

---

### 🔍 SEO & Discovery (6 skills)
Improve organic search visibility and discoverability.

| Skill | Use When |
|-------|----------|
| `/seo-audit` | Audit SEO health (technical, on-page, content quality) |
| `/ai-seo` | Optimize for AI search engines (AEO, GEO, LLMO, AI Overviews) |
| `/programmatic-seo` | Build SEO pages at scale using templates + data |
| `/schema-markup` | Add or fix structured data (JSON-LD, schema.org) |
| `/site-architecture` | Plan page hierarchy, navigation, URL structure, internal linking |
| `/aso-audit` | Audit App Store or Google Play listing optimization |

**Common workflow:** `/seo-audit` → prioritized fixes → implement → `/schema-markup` → validate

---

### 💰 Paid & Distribution (3 skills)
Paid advertising and distribution channels.

| Skill | Use When |
|-------|----------|
| `/paid-ads` | Plan or optimize paid campaigns (Google Ads, Meta, LinkedIn, Twitter/X) |
| `/ad-creative` | Generate and iterate ad creative at scale (headlines, descriptions, primary text) |
| `/directory-submissions` | Submit product to directories (Product Hunt, BetaList, AI directories) |

**Common workflow:** `/paid-ads` → campaign strategy → `/ad-creative` → creative variations → `/page-cro` landing page

---

### 📊 Measurement & Testing (2 skills)
Set up tracking and run experiments.

| Skill | Use When |
|-------|----------|
| `/analytics-tracking` | Set up or audit analytics tracking (GA4, PostHog, Mixpanel) |
| `/ab-test-setup` | Design A/B tests with proper hypothesis, sample size, duration |

**Common workflow:** `/analytics-tracking` → events configured → `/ab-test-setup` → run experiment → analyze

---

### 🔁 Retention & Growth (3 skills)
Keep users, drive referrals, grow organically.

| Skill | Use When |
|-------|----------|
| `/churn-prevention` | Reduce churn (cancel flows, save offers, dunning, payment recovery) |
| `/referral-program` | Design referral or affiliate programs |
| `/community-marketing` | Build and leverage online communities for growth |

**Common workflow:** `/churn-prevention` → save flow design → implement → measure retention impact

---

### 🛠️ Growth Engineering (3 skills)
Build marketing tools and lead generation systems.

| Skill | Use When |
|-------|----------|
| `/free-tool-strategy` | Plan or build free tools for lead gen/SEO (calculators, generators, converters) |
| `/lead-magnets` | Design lead magnets (ebooks, templates, checklists, reports) |
| `/co-marketing` | Find co-marketing partners and plan joint campaigns |

**Common workflow:** `/free-tool-strategy` → concept → build in main project → `/seo-audit` → optimize for discovery

---

### 🎯 Strategy (7 skills)
High-level marketing planning and research.

| Skill | Use When |
|-------|----------|
| `/launch-strategy` | Plan product launches or feature announcements |
| `/pricing-strategy` | Evaluate pricing models, packaging, monetization |
| `/marketing-ideas` | Generate marketing tactics and channel ideas |
| `/marketing-psychology` | Apply psychological principles to marketing |
| `/customer-research` | Synthesize customer interviews, surveys, support tickets |
| `/competitor-profiling` | Research and profile competitors |
| `/competitor-alternatives` | Create "vs" and "alternative to" pages for SEO + sales |

**Common workflow:** `/customer-research` → insights → `/marketing-ideas` → tactics → `/cmo` prioritize

---

### 💼 Sales & RevOps (3 skills)
Sales enablement and revenue operations.

| Skill | Use When |
|-------|----------|
| `/revops` | Design lead lifecycle, scoring, routing, pipeline management |
| `/sales-enablement` | Create sales decks, one-pagers, objection docs, demo scripts |
| `/co-marketing` | Find partnership opportunities and plan joint campaigns |

**Common workflow:** `/revops` → lifecycle map → `/sales-enablement` → collateral → measure conversion

---

## Common Workflows

### Homepage Optimization
```
/cmo "review homepage positioning"
  → Strategic assessment + recommendations
/page-cro
  → Conversion audit + quick wins
/copywriting "homepage hero section"
  → 3 headline alternatives with rationale
/copy-editing
  → Polish final copy

→ Implement in main project via /execute
→ /ab-test-setup to measure impact
```

### Content Marketing Campaign
```
/customer-research
  → Analyze support tickets, interviews
/content-strategy
  → Topic clusters + prioritization
/copywriting "blog post: [topic]"
  → Draft content
/seo-audit
  → On-page optimization checklist
/social-content
  → Social promotion plan

→ Implement in main project
→ /analytics-tracking to measure traffic
```

### Product Launch
```
/cmo "plan [product] launch"
  → GTM strategy + channel mix
/launch-strategy
  → Timeline, milestones, content plan
/copywriting "launch announcement"
  → Messaging for each channel
/email-sequence "launch sequence"
  → Email flow to list
/paid-ads
  → Paid campaign strategy

→ Implement campaign in main project
→ /analytics-tracking to measure results
```

### Paid Acquisition Setup
```
/paid-ads
  → Campaign structure + targeting strategy
/ad-creative
  → Generate 10 headline variations
/page-cro
  → Optimize landing page for paid traffic
/analytics-tracking
  → Set up conversion tracking
/ab-test-setup
  → Test landing page variations

→ Launch campaigns
→ Monitor and optimize
```

## Cross-Skill References

Most skills reference related skills at the end. Common patterns:

- **CRO skills** → reference `/ab-test-setup` for testing recommendations
- **Content skills** → reference `/seo-audit` for optimization
- **Strategy skills** → reference `/cmo` for prioritization
- **Copy skills** → reference `/copy-editing` for polish
- **All skills** → check `/product-marketing-context` first for product context

## Tips

### Start Strategic, Then Tactical
1. Use `/cmo` to set direction and priorities
2. Use specialist skills for detailed execution
3. Save outputs to `~/make-it-marketing/recommendations/`
4. Implement in main project via `/execute`

### Leverage Product Marketing Context
All skills check `.agents/product-marketing-context.md` first. Create it once:
```
/product-marketing-context
```
Then you won't repeat the same product/audience info across skills.

### Chain Skills Together
Many tasks benefit from multiple skills in sequence:
- Research → Strategy → Execution
- Write → Edit → Test
- Audit → Fix → Validate

### Save Your Work
Output strategy documents to `recommendations/` with descriptive names:
```
recommendations/
├── homepage-cro-2026-05-12.md
├── q3-content-strategy-2026-05-12.md
├── email-welcome-sequence-2026-05-12.md
└── ...
```

### When Unsure Which Skill to Use
Ask `/cmo` to recommend the right specialist for your task.

---

## Skill Installation Status

✅ **Installed (P0-P1 — 11 skills)**
- Foundation: product-marketing-context
- Conversion: page-cro, signup-flow-cro, onboarding-cro, form-cro, popup-cro
- Content: copywriting, email-sequence, cold-email
- Paid: paid-ads, ad-creative

⏳ **Pending Installation (P2-P3 — 32 skills)**
- Conversion: paywall-upgrade-cro
- Content: copy-editing, content-strategy, social-content, video, image
- SEO: seo-audit, ai-seo, programmatic-seo, schema-markup, site-architecture, aso-audit
- Measurement: analytics-tracking, ab-test-setup
- Retention: churn-prevention, referral-program
- Growth: free-tool-strategy, lead-magnets, community-marketing
- Strategy: launch-strategy, pricing-strategy, marketing-ideas, marketing-psychology, customer-research, competitor-profiling, competitor-alternatives
- Sales: revops, sales-enablement, co-marketing
- Distribution: directory-submissions

Skills will be installed progressively based on usage and priority.

---

**Last Updated**: 2026-05-12  
**Total Skills**: 43 (11 installed, 32 pending)

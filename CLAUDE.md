# Make-It.ai Marketing Strategy Project

This Claude Code project is dedicated to marketing strategy, messaging, conversion optimization, and content planning for Make-It.ai.

## Purpose

**ADVISORY ONLY** — All skills in this project produce strategy documents, copy alternatives, and recommendations. No code changes happen here. Implementation goes through the main `~/make-it` project via `/execute`.

## What Is Make-It.ai?

Make-It.ai is an AI-powered platform that generates complete DIY electronics projects (wiring diagrams, code, BOM, assembly instructions) from a text prompt. Target audience: hobbyists, makers, students, educators — many non-technical.

## Project Structure

```
make-it-marketing/
├── .agents/
│   └── product-marketing-context.md    # Core product/audience/positioning context
├── .claude/
│   ├── commands/
│   │   ├── cmo.md                      # Strategic marketing leadership
│   │   └── marketing/                  # 43 specialist skills organized by function
│   │       ├── _foundation/            # product-marketing-context skill
│   │       ├── conversion/             # CRO skills (page, signup, onboarding, form, popup, paywall)
│   │       ├── content-copy/           # Copywriting, email, social, video
│   │       ├── seo-discovery/          # SEO audit, AI SEO, programmatic, schema
│   │       ├── paid-distribution/      # Paid ads, ad creative, directories
│   │       ├── measurement/            # Analytics tracking, A/B testing
│   │       ├── retention/              # Churn prevention, referral programs
│   │       ├── growth-engineering/     # Free tools, lead magnets, community
│   │       ├── strategy/               # Launch, pricing, research, competitors
│   │       └── sales-revops/           # RevOps, sales enablement, co-marketing
│   └── memory/                         # Marketing-focused memory
├── recommendations/                     # Output directory for strategy docs
└── CLAUDE.md                           # This file
```

## Workflow: Analyze Here, Implement There

### Standard Process

1. **Analyze in marketing project** (this project)
   - Use marketing skills to generate strategy, copy alternatives, recommendations
   - Output saved to `recommendations/[topic]-[date].md`

2. **Implement in main project** (`~/make-it`)
   - Copy approved recommendations to main project conversation
   - Use `/execute` to implement changes
   - Commit and deploy through normal dev workflow

### Example Workflow

```bash
# In ~/make-it-marketing
$ /page-cro
→ Analyzes ../make-it/webapp/src/components/HomePage.tsx
→ Generates recommendations/homepage-cro-2026-05-12.md

# In ~/make-it
$ cat ../make-it-marketing/recommendations/homepage-cro-2026-05-12.md
$ /execute
→ Implements approved changes
→ Commits to git
```

### Alternative: Inline workflow for small changes
For quick copy generation, you can copy the output directly without saving to recommendations/:
```
~/make-it-marketing $ /copywriting "write 3 homepage headline alternatives"
→ Copy output → paste into main project conversation → /execute
```

## Cross-Project Access

Marketing skills can READ files from `../make-it/` to analyze current state:

**Landing pages:**
```bash
../make-it/webapp/src/components/HomePage.tsx
../make-it/webapp/src/components/CreationPage.tsx
../make-it/webapp/src/components/DesktopProjectView.tsx
```

**Blog posts:**
```bash
../make-it/webapp/public/blog/
```

**Tech decisions:**
```bash
../make-it/docs/tech-decisions/016-seo-strategy.md
../make-it/docs/tech-decisions/019-automated-content-pipeline.md
```

**Analytics configuration:**
```bash
../make-it/webapp/src/utils/analytics.ts
```

## Key Skills Quick Reference

### Strategic
- `/cmo` — Marketing leadership, GTM planning, channel portfolio strategy

### Conversion Optimization
- `/page-cro` — Landing page CRO
- `/signup-flow-cro` — Registration flow optimization
- `/onboarding-cro` — Post-signup activation
- `/form-cro` — Lead capture forms
- `/popup-cro` — Modals and overlays
- `/paywall-upgrade-cro` — In-app upgrade moments

### Content & Copy
- `/copywriting` — Marketing copy for any page
- `/copy-editing` — Polish and improve existing copy
- `/content-strategy` — Content planning and topic prioritization
- `/email-sequence` — Automated email flows
- `/cold-email` — B2B outreach sequences
- `/social-content` — Social media content

### SEO & Discovery
- `/seo-audit` — SEO health check and recommendations
- `/ai-seo` — AI search optimization (AEO, GEO, LLMO)
- `/programmatic-seo` — Scaled page generation
- `/schema-markup` — Structured data implementation
- `/site-architecture` — Page hierarchy and navigation

### Paid & Distribution
- `/paid-ads` — Paid advertising strategy (Google, Meta, LinkedIn)
- `/ad-creative` — Bulk ad creative generation

### Measurement
- `/analytics-tracking` — Event tracking setup
- `/ab-test-setup` — Experiment design

### Retention & Growth
- `/churn-prevention` — Cancel flows, save offers
- `/referral-program` — Referral and affiliate programs
- `/free-tool-strategy` — Marketing tools and calculators
- `/lead-magnets` — Lead generation assets

### Strategy
- `/launch-strategy` — Product launches and announcements
- `/pricing-strategy` — Pricing and monetization
- `/customer-research` — Customer interview synthesis
- `/competitor-profiling` — Competitor analysis
- `/marketing-ideas` — 140 SaaS marketing tactics
- `/marketing-psychology` — Mental models and behavioral science

### Sales & RevOps
- `/revops` — Lead lifecycle, scoring, routing
- `/sales-enablement` — Sales decks, one-pagers, demo scripts

**See `.claude/commands/marketing/README.md` for full skill map and workflows.**

## Foundation: Product Marketing Context

**All marketing skills check `.agents/product-marketing-context.md` first** before asking questions. This file contains:
- Product overview and positioning
- Target audience and personas
- Problems and pain points
- Competitive landscape
- Differentiation
- Customer language (verbatim quotes)
- Brand voice
- Proof points

**To create or update:** `/product-marketing-context`

This skill will auto-draft context from the main project's landing pages, blog, and README, then let you refine it.

## Guardrails

All marketing skills in this project follow these rules:

### ✅ Allowed
- Read files from `../make-it/` (landing pages, blog posts, tech decisions)
- WebFetch competitor sites for analysis
- Generate strategy documents in `recommendations/`
- Produce copy alternatives, frameworks, recommendations

### ❌ Not Allowed
- Modify files in `../make-it/` (use Edit, Write, Bash to change code)
- Create git branches, commits, or pull requests in main project
- Deploy or run builds
- Modify production systems

**Implementation goes through the main project's `/execute` workflow.**

## Memory

Marketing project memory tracks:
- Positioning decisions and rationale
- Messaging tests and results
- Content performance patterns
- Channel strategy and learnings
- Competitive landscape shifts
- Campaign outcomes and lessons

Memory is separate from the main dev project — keeps marketing strategy context focused and clean.

## Related Projects

- **Main Development Project**: `~/make-it` — For feature development, bug fixes, deployments. Use `/execute` there to implement marketing recommendations.

## Getting Started

1. **Create product context** (first-time setup):
   ```
   /product-marketing-context
   ```
   This will read your landing pages and auto-draft a context file. Review and refine.

2. **Analyze current state**:
   ```
   /cmo "review homepage messaging"
   /page-cro
   /seo-audit
   ```

3. **Generate copy/strategy**:
   ```
   /copywriting "homepage hero section"
   /email-sequence "welcome sequence for new users"
   /content-strategy "plan Q3 blog topics"
   ```

4. **Implement approved recommendations** in main project:
   ```bash
   cd ~/make-it
   # Copy recommendation, then:
   /execute
   ```

## Tips

- Start with `/cmo` for strategic direction, then use specialist skills for detailed execution
- Save all strategy outputs to `recommendations/` with descriptive filenames and dates
- Use the product marketing context file — it eliminates repetitive questions across skills
- Marketing skills cross-reference each other (see "Related Skills" sections)
- When in doubt about which skill to use, ask `/cmo` to recommend the right specialist

---

**Project Status**: Active  
**Last Updated**: 2026-05-12  
**Main Project**: ~/make-it

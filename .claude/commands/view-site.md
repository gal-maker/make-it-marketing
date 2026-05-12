# View Site Files

Helper skill to read files from the main `~/make-it` project for marketing analysis.

## Purpose

All marketing skills can read from the main project to analyze current state. This skill documents common paths and provides quick access commands.

## Common File Paths

### Landing Pages
```bash
# Homepage
cat ../make-it/webapp/src/components/HomePage.tsx

# Creation page (main product flow)
cat ../make-it/webapp/src/components/CreationPage.tsx

# Desktop project view
cat ../make-it/webapp/src/components/DesktopProjectView.tsx

# List all page components
ls -1 ../make-it/webapp/src/components/*Page.tsx
```

### Blog Content
```bash
# List blog posts
ls -1 ../make-it/webapp/public/blog/

# Read specific post
cat ../make-it/webapp/public/blog/[post-name].html

# Count blog posts
ls -1 ../make-it/webapp/public/blog/*.html | wc -l
```

### Technical Decisions (Context)
```bash
# SEO strategy
cat ../make-it/docs/tech-decisions/016-seo-strategy.md

# Content pipeline
cat ../make-it/docs/tech-decisions/019-automated-content-pipeline.md

# Marketing health assessment
cat ../make-it/docs/tech-decisions/029-marketing-health-assessment.md

# List all tech decisions
ls -1 ../make-it/docs/tech-decisions/
```

### Analytics & Tracking
```bash
# PostHog analytics config
cat ../make-it/webapp/src/utils/analytics.ts

# Check what events are tracked
grep "data-ph-capture" ../make-it/webapp/src/components/*.tsx
```

### Content Data
```bash
# Guide articles metadata
cat ../make-it/webapp/src/data/guides/articles/index.tsx

# Project examples
ls -1 ../make-it/webapp/src/data/projects/
```

### Package Info
```bash
# Product name, description
cat ../make-it/webapp/package.json | grep -A5 '"name"'

# Server dependencies
cat ../make-it/server/package.json
```

## Marketing Skills Auto-Read These

Most marketing skills automatically check:
1. `.agents/product-marketing-context.md` (if it exists)
2. Landing pages when analyzing conversion
3. Blog posts when planning content
4. Tech decisions when reviewing strategy

You don't need to manually read these for every skill invocation.

## Use Cases

### Manual Analysis
```bash
# Compare competitor homepage to ours
/view-site
cat ../make-it/webapp/src/components/HomePage.tsx

# Then analyze with marketing skill
/page-cro
```

### Verify Current State Before Recommendation
```bash
# Check current headline before generating alternatives
cat ../make-it/webapp/src/components/HomePage.tsx | grep -A5 "hero"

/copywriting "generate 3 homepage headline alternatives"
```

### Context for Strategy Planning
```bash
# Review existing SEO strategy
cat ../make-it/docs/tech-decisions/016-seo-strategy.md

# Then plan content strategy
/content-strategy
```

## Quick Reference: What Lives Where

| Content Type | Path | Use For |
|-------------|------|---------|
| **Landing pages** | `../make-it/webapp/src/components/*Page.tsx` | CRO, copywriting, messaging review |
| **Blog posts** | `../make-it/webapp/public/blog/*.html` | Content strategy, SEO audit |
| **Copy/messaging** | Component files | Copy editing, A/B test ideas |
| **Analytics setup** | `../make-it/webapp/src/utils/analytics.ts` | Event tracking audit |
| **Tech decisions** | `../make-it/docs/tech-decisions/*.md` | Historical context, strategy continuity |
| **Product data** | `../make-it/webapp/src/data/` | Understanding current content, examples |

## Guardrails

✅ **Can read** from `../make-it/` for analysis  
❌ **Cannot modify** files in `../make-it/` (use main project's `/execute`)  
❌ **Cannot commit** to main project from here  
❌ **Cannot deploy** or run builds  

## Pro Tips

- Use `grep -r "keyword" ../make-it/webapp/src/components/` to find specific copy
- Use `git log ../make-it/` to see recent changes context
- Check `../make-it/CHANGELOG.md` for recent features (informs marketing timing)
- Read `../make-it/README.md` for product overview

## Related Skills

All marketing skills use these paths:
- `/page-cro` — Reads landing pages for conversion analysis
- `/copywriting` — Reads current copy before generating alternatives
- `/content-strategy` — Reads blog and tech decisions
- `/seo-audit` — Reads site structure and content
- `/email-sequence` — Understands product context for email flows

---

**When to use**: When you need to manually inspect files before running a marketing skill, or when you want to verify what the skill will see.

**Note**: Most skills auto-read these paths, so manual reading is optional.

# Quick Start Guide

## First Time Setup

1. **Create product marketing context** (5 minutes):
   ```
   /product-marketing-context
   ```
   This will auto-draft from your landing pages. Review and refine.

2. **Test a skill**:
   ```
   /page-cro
   ```
   It will read `../make-it/webapp/src/components/HomePage.tsx` and generate recommendations.

## Most Used Skills

### Strategic Direction
```
/cmo "review homepage messaging"
/cmo "plan Q3 content strategy"
```

### Quick Wins
```
/page-cro                                    # Audit any landing page
/copywriting "homepage hero section"         # Generate copy alternatives
/email-sequence "welcome new users"          # Design email flow
```

### Content Planning
```
/content-strategy                            # Plan topics and editorial calendar
/seo-audit                                   # Check SEO health
```

### Campaigns
```
/paid-ads                                    # Plan ad campaigns
/ad-creative                                 # Generate ad variations
/launch-strategy                             # Plan product launches
```

## Workflow

```
┌─────────────────────────────────────────────┐
│  ~/make-it-marketing (this project)         │
│  - Run marketing skills                     │
│  - Generate recommendations                 │
│  - Output to recommendations/               │
└──────────────────┬──────────────────────────┘
                   │
                   │ Copy approved changes
                   ▼
┌─────────────────────────────────────────────┐
│  ~/make-it (main project)                   │
│  - Paste recommendations                    │
│  - /execute to implement                    │
│  - Commit and deploy                        │
└─────────────────────────────────────────────┘
```

## Examples

### Optimize Homepage
```bash
# In ~/make-it-marketing
$ /page-cro

Agent reads: ../make-it/webapp/src/components/HomePage.tsx
Agent generates: recommendations/homepage-cro-2026-05-12.md

# Review recommendations, then in ~/make-it
$ cat ../make-it-marketing/recommendations/homepage-cro-2026-05-12.md
$ /execute
# Implement approved changes
```

### Write New Copy
```bash
# In ~/make-it-marketing
$ /copywriting "write 3 headline alternatives for homepage hero"

Agent outputs 3 options with rationale.

# Copy best option, then in ~/make-it
# Paste into conversation
$ /execute
# Update HomePage.tsx
```

### Plan Content Strategy
```bash
# In ~/make-it-marketing
$ /content-strategy

Agent analyzes: ../make-it/docs/tech-decisions/016-seo-strategy.md
Agent generates: Q3 content topics with prioritization

Save to: recommendations/q3-content-strategy-2026-05-12.md
```

## Tips

✅ **Always create product context first** — saves time across all skills  
✅ **Save outputs to recommendations/** — organized by topic and date  
✅ **Use /cmo for direction** — delegates to right specialist skills  
✅ **Chain skills together** — research → strategy → copy → edit  
✅ **Test one thing at a time** — use `/ab-test-setup` for experimentation  

❌ **Don't modify ../make-it/ files** — marketing project is read-only  
❌ **Don't try to implement here** — use main project's `/execute`  

## Installed Skills (11 total)

**Foundation**: product-marketing-context  
**Conversion**: page-cro, signup-flow-cro, onboarding-cro, form-cro, popup-cro  
**Content**: copywriting, email-sequence, cold-email  
**Paid**: paid-ads, ad-creative  

32 more skills available for installation — see `.claude/commands/marketing/README.md`

## Need Help?

- Full skill list: `.claude/commands/marketing/README.md`
- Project structure: `CLAUDE.md`
- Main project: `~/make-it`

---

Ready? Run `/product-marketing-context` to get started.

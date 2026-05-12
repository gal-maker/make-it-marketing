# Cross-Project Communication Guide

How the marketing project (`~/make-it-marketing`) and main dev project (`~/make-it`) communicate.

---

## Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│  ~/make-it-marketing (Marketing Project)                    │
│  Role: Advisory - Generate recommendations                  │
│                                                             │
│  Reads from main project ────────┐                         │
│  Writes to recommendations/       │                         │
│                                   │                         │
│  Skills:                          │                         │
│  - /page-cro                      │                         │
│  - /copywriting                   │                         │
│  - /email-sequence                │                         │
│  - /seo-audit                     │                         │
│  - etc.                           │                         │
└───────────────────────────────────┼─────────────────────────┘
                                    │
                                    │ File reads (read-only)
                                    │
                    ┌───────────────▼──────────────────┐
                    │   Shared Resources               │
                    │   (Read by marketing,            │
                    │    owned by main)                │
                    │                                  │
                    │ - Landing pages                  │
                    │ - Blog posts                     │
                    │ - Tech decisions                 │
                    │ - Analytics config               │
                    │ - Product context (symlinked)    │
                    └───────────────┬──────────────────┘
                                    │
                                    │ File modifications
                                    │
┌───────────────────────────────────▼─────────────────────────┐
│  ~/make-it (Main Dev Project)                               │
│  Role: Implementation - Ship code                           │
│                                                             │
│  Reads from marketing/recommendations/ ─────────────────┐   │
│  Implements via /execute                                 │   │
│  Commits and deploys                                     │   │
│                                                             │
│  Skills:                                                    │
│  - /execute                                                 │
│  - /review                                                  │
│  - /run-tests                                               │
│  - /view-marketing-recommendations (helper)                 │
└─────────────────────────────────────────────────────────────┘
```

---

## Communication Mechanisms

### 1. File System Bridge (Primary Pattern)

**Marketing → Main**: Write recommendations to `~/make-it-marketing/recommendations/`  
**Main → Marketing**: Read recommendations via `/view-marketing-recommendations`

#### Example Flow

**In marketing project:**
```bash
cd ~/make-it-marketing

# Analyze homepage
$ /page-cro

# Reads: ../make-it/webapp/src/components/HomePage.tsx
# Generates: recommendations/homepage-cro-2026-05-12.md
# Contains: 10 specific CRO recommendations with rationale
```

**In main project:**
```bash
cd ~/make-it

# Discover recommendations
$ /view-marketing-recommendations
# Lists: recommendations/homepage-cro-2026-05-12.md

# Read recommendation
$ cat ~/make-it-marketing/recommendations/homepage-cro-2026-05-12.md

# Implement approved changes
$ /execute
"Per homepage-cro-2026-05-12.md:
- Update hero headline to Option B
- Add social proof section
- Improve CTA visibility"

# Commit
$ git commit -m "feat: improve homepage CRO
Based on: ../make-it-marketing/recommendations/homepage-cro-2026-05-12.md"
```

---

### 2. Shared Product Context (Symlink)

**File**: `.agents/product-marketing-context.md`  
**Location**: Created in marketing project, symlinked to main project

```bash
# Created in:
~/make-it-marketing/.agents/product-marketing-context.md

# Symlinked to:
~/make-it/.agents/product-marketing-context.md → ~/make-it-marketing/.agents/product-marketing-context.md
```

**Benefits:**
- Single source of truth for product positioning
- Marketing updates are immediately visible to main project
- No duplication or sync issues

**How to use:**
```bash
# Update in marketing project
cd ~/make-it-marketing
/product-marketing-context
# Edits: .agents/product-marketing-context.md

# Automatically available in main project
cd ~/make-it
cat .agents/product-marketing-context.md  # Reads symlinked file
```

---

### 3. Helper Skills

#### In Main Project: `/view-marketing-recommendations`

```bash
cd ~/make-it
/view-marketing-recommendations
```

**What it does:**
- Lists all available marketing recommendations
- Reads specific recommendation files
- Provides implementation pattern guidance

**Use when:** Ready to implement marketing changes

---

#### In Marketing Project: `/view-site`

```bash
cd ~/make-it-marketing
/view-site
```

**What it does:**
- Documents common file paths in main project
- Provides quick commands to read landing pages, blog, analytics
- Shows what marketing skills auto-read

**Use when:** Need to manually inspect files before analysis

---

### 4. Cross-Project File Reading

**Marketing skills can read from main project:**

```bash
# From ~/make-it-marketing, read main project files:
cat ../make-it/webapp/src/components/HomePage.tsx
cat ../make-it/webapp/public/blog/state-of-maker-projects-may-2026.html
cat ../make-it/docs/tech-decisions/016-seo-strategy.md
```

**Main project cannot directly read marketing files**, but can:
```bash
# From ~/make-it, read marketing outputs:
cat ~/make-it-marketing/recommendations/homepage-cro-2026-05-12.md
ls ~/make-it-marketing/recommendations/
```

---

## Communication Patterns by Use Case

### Use Case 1: Optimize Homepage

```bash
# Step 1: Analyze (marketing project)
cd ~/make-it-marketing
/page-cro

→ Reads: ../make-it/webapp/src/components/HomePage.tsx
→ Writes: recommendations/homepage-cro-2026-05-12.md
→ Output: 10 recommendations ranked by impact

# Step 2: Review (manual)
cat recommendations/homepage-cro-2026-05-12.md
# Review, discuss with team, select which to implement

# Step 3: Implement (main project)
cd ~/make-it
/view-marketing-recommendations
cat ~/make-it-marketing/recommendations/homepage-cro-2026-05-12.md
/execute "Implement recommendations 1, 3, 5 from homepage-cro-2026-05-12.md"

→ Modifies: webapp/src/components/HomePage.tsx
→ Commits: With reference to recommendation file
→ Deploys: Via normal workflow
```

---

### Use Case 2: Write New Email Sequence

```bash
# Step 1: Design sequence (marketing project)
cd ~/make-it-marketing
/email-sequence "welcome sequence for new users who create first project"

→ Reads: .agents/product-marketing-context.md (product info)
→ Reads: ../make-it/webapp/src/components/ (to understand product flow)
→ Writes: recommendations/email-welcome-sequence-2026-05-12.md
→ Output: 5-email flow with copy, timing, triggers

# Step 2: Implement (main project)
cd ~/make-it
cat ~/make-it-marketing/recommendations/email-welcome-sequence-2026-05-12.md
/execute "Implement welcome email sequence per email-welcome-sequence-2026-05-12.md"

→ Creates: server/emails/templates/welcome-*.tsx
→ Updates: server/routes/auth.ts (trigger on signup)
→ Configures: Email service (Resend/Mailchimp)
→ Tests: Send test emails
→ Commits: With reference to recommendation
```

---

### Use Case 3: Plan Content Strategy

```bash
# Step 1: Research and plan (marketing project)
cd ~/make-it-marketing
/customer-research
# Analyze support tickets, user interviews

/content-strategy
→ Reads: ../make-it/webapp/public/blog/ (existing content)
→ Reads: ../make-it/docs/tech-decisions/016-seo-strategy.md (SEO context)
→ Reads: .agents/product-marketing-context.md (audience info)
→ Writes: recommendations/q3-content-strategy-2026-05-12.md
→ Output: 20 blog topics, prioritized by impact

# Step 2: Write first post (marketing project)
/copywriting "blog post: How to Choose the Right Arduino Board for Your Project"
→ Writes: recommendations/blog-arduino-board-guide-2026-05-12.md
→ Output: Full blog post draft with SEO optimization

# Step 3: Implement (main project)
cd ~/make-it
cat ~/make-it-marketing/recommendations/blog-arduino-board-guide-2026-05-12.md
/execute "Create blog post from blog-arduino-board-guide-2026-05-12.md"

→ Creates: webapp/public/blog/how-to-choose-arduino-board.html
→ Updates: Blog index
→ Optimizes: Meta tags, images, internal links
→ Commits and deploys
```

---

### Use Case 4: Launch New Feature

```bash
# Step 1: Strategic planning (marketing project)
cd ~/make-it-marketing
/cmo "plan launch for BOM component icons feature"
→ Writes: recommendations/launch-bom-icons-2026-05-12.md
→ Output: GTM strategy, channel mix, timeline

/launch-strategy
→ Detailed launch plan with phases

/copywriting "announcement email for BOM component icons"
→ Email copy

/social-content "launch posts for BOM component icons"
→ Social media posts

# All outputs → recommendations/

# Step 2: Implement campaign (main project)
cd ~/make-it
/view-marketing-recommendations
# Read all launch-bom-icons-* files

/execute "Implement BOM icons launch campaign"
→ Update blog with announcement post
→ Create email template
→ Schedule social posts
→ Update homepage with feature highlight
```

---

## Guardrails & Best Practices

### Marketing Project (Advisory)

✅ **Can Do:**
- Read any file from main project (read-only)
- Analyze landing pages, blog, code
- Generate recommendations
- Write to `recommendations/` directory
- Update product marketing context

❌ **Cannot Do:**
- Modify files in main project
- Create git commits in main project
- Run builds or deploy
- Execute code in main project

### Main Project (Implementation)

✅ **Can Do:**
- Read marketing recommendations
- Implement approved changes via `/execute`
- Commit and deploy
- Reference marketing analysis in commits

❌ **Cannot Do:**
- Run marketing skills directly (use marketing project)
- Modify marketing project files (context updates happen in marketing project)

---

## File Naming Conventions

### Recommendations Directory

Pattern: `[topic]-[type]-YYYY-MM-DD.md`

Examples:
- `homepage-cro-2026-05-12.md` - CRO analysis
- `copy-hero-section-2026-05-12.md` - Copy alternatives
- `email-welcome-sequence-2026-05-12.md` - Email flow design
- `q3-content-strategy-2026-05-12.md` - Content planning
- `seo-audit-2026-05-12.md` - SEO review
- `launch-bom-icons-2026-05-12.md` - Launch plan

**Benefits:**
- Chronological sorting works automatically
- Easy to find by topic or date
- No confusion about what's inside

---

## Commit Message Pattern

When implementing marketing recommendations in main project:

```
<type>: <brief description>

<detailed description>

Based on marketing analysis:
~/make-it-marketing/recommendations/[filename].md

Implemented changes:
- [specific change 1]
- [specific change 2]
- [specific change 3]
```

**Example:**
```
feat: improve homepage value proposition clarity

Updated hero section with benefit-focused headline and clearer
subheadline. Added social proof section with project count and
user testimonials.

Based on marketing analysis:
~/make-it-marketing/recommendations/homepage-cro-2026-05-12.md

Implemented changes:
- Hero headline: "Generate electronics projects with AI" → "Build your next electronics project in minutes, not hours"
- Subheadline: Added "Get wiring diagrams, code, and assembly instructions from a simple text description"
- Social proof: Added "Join 300+ makers who've generated 1,500+ projects"
```

**Benefits:**
- Traceability (can find original analysis)
- Context for future reviewers
- Rationale for design decisions

---

## Communication Anti-Patterns

### ❌ Don't: Mix Projects in Same Conversation

**Bad:**
```bash
cd ~/make-it
/page-cro  # Won't work - skill not in this project
```

**Good:**
```bash
cd ~/make-it-marketing
/page-cro  # Generates recommendation

cd ~/make-it
/view-marketing-recommendations  # Read it
/execute  # Implement it
```

---

### ❌ Don't: Modify Main Project from Marketing Project

**Bad:**
```bash
cd ~/make-it-marketing
/copywriting "homepage hero"
# Then trying to edit ../make-it/webapp/src/components/HomePage.tsx
```

**Good:**
```bash
cd ~/make-it-marketing
/copywriting "homepage hero"
# Outputs copy alternatives → save to recommendations/

cd ~/make-it
# Read recommendations
/execute "Update HomePage.tsx with copy from recommendation"
```

---

### ❌ Don't: Duplicate Product Context

**Bad:**
- Maintain separate product context in each project
- Update one and forget to update the other
- Inconsistent positioning across projects

**Good:**
- Single source in marketing project: `.agents/product-marketing-context.md`
- Symlink in main project: `.agents/product-marketing-context.md → ~/make-it-marketing/.agents/product-marketing-context.md`
- Update once, available everywhere

---

## Quick Reference

| Task | Project | Command |
|------|---------|---------|
| Analyze homepage | Marketing | `/page-cro` |
| Write copy | Marketing | `/copywriting` |
| Plan content | Marketing | `/content-strategy` |
| Audit SEO | Marketing | `/seo-audit` |
| View recommendations | Main | `/view-marketing-recommendations` |
| Implement changes | Main | `/execute` |
| View site files | Marketing | `/view-site` |
| Update product context | Marketing | `/product-marketing-context` |

---

## Troubleshooting

### Problem: Marketing skill can't find main project files

**Solution:**
```bash
# Verify path from marketing project
cd ~/make-it-marketing
ls -la ../make-it/webapp/src/components/

# If path is wrong, check actual location
pwd  # Should be /Users/user/make-it-marketing
```

---

### Problem: Main project can't read recommendations

**Solution:**
```bash
# Verify recommendations exist
ls ~/make-it-marketing/recommendations/

# Use full path
cat ~/make-it-marketing/recommendations/[filename].md

# Or use helper
/view-marketing-recommendations
```

---

### Problem: Product context out of sync

**Solution:**
```bash
# Check if symlink exists
ls -la ~/make-it/.agents/product-marketing-context.md

# Should show: → /Users/user/make-it-marketing/.agents/product-marketing-context.md

# If not, create symlink
cd ~/make-it/.agents
ln -s ~/make-it-marketing/.agents/product-marketing-context.md product-marketing-context.md
```

---

## Summary

**Primary communication**: File-based (recommendations directory)  
**Shared context**: Symlinked product marketing context  
**Helper skills**: `/view-marketing-recommendations`, `/view-site`  
**Pattern**: Analyze → Recommend → Implement → Commit  
**Guardrails**: Marketing reads-only, main implements-only  

**Key principle**: Clean separation with explicit bridges. Marketing generates strategy, main ships code. Each project has clear responsibilities.

---

**Last Updated**: 2026-05-12

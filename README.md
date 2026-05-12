# Make-It.ai Marketing Strategy Project

**Advisory-only marketing analysis project for Make-It.ai**

Separate from main development project to keep marketing strategy conversations clean and focused.

---

## Quick Links

- 🚀 **[QUICKSTART.md](QUICKSTART.md)** - Get started in 5 minutes
- 📚 **[CLAUDE.md](CLAUDE.md)** - Full project documentation
- 🔗 **[CROSS-PROJECT-COMMUNICATION.md](CROSS-PROJECT-COMMUNICATION.md)** - How marketing & main projects communicate
- 🗺️ **[.claude/commands/marketing/README.md](.claude/commands/marketing/README.md)** - Skill navigation guide
- 📋 **[recommendations/SETUP-SUMMARY.md](recommendations/SETUP-SUMMARY.md)** - Setup record

---

## What This Project Does

**Generates marketing strategy, not code.**

- Homepage/landing page optimization → `/page-cro`
- Copy and messaging → `/copywriting`
- Email sequences → `/email-sequence`
- Content strategy → `/content-strategy`
- SEO audits → `/seo-audit`
- Paid ads campaigns → `/paid-ads`
- Launch planning → `/cmo`, `/launch-strategy`
- And 35+ more marketing skills...

All outputs go to `recommendations/` directory. Implementation happens in main `~/make-it` project via `/execute`.

---

## First-Time Setup (5 minutes)

1. **Switch to this project:**
   ```bash
   cd ~/make-it-marketing
   ```

2. **Create product marketing context:**
   ```
   /product-marketing-context
   ```
   Auto-drafts from your landing pages. Review and refine.

3. **Try your first analysis:**
   ```
   /page-cro
   ```
   Analyzes homepage, generates CRO recommendations.

4. **Implement in main project:**
   ```bash
   cd ~/make-it
   /view-marketing-recommendations
   /execute
   ```

Done! See [QUICKSTART.md](QUICKSTART.md) for more details.

---

## Project Structure

```
make-it-marketing/
├── README.md                    # This file
├── QUICKSTART.md                # Quick start guide
├── CLAUDE.md                    # Full documentation
├── CROSS-PROJECT-COMMUNICATION.md  # Communication patterns
│
├── .agents/
│   └── product-marketing-context.md  # Product/audience/positioning context
│                                      # (symlinked to main project)
│
├── .claude/commands/
│   ├── cmo.md                   # Strategic leadership skill
│   ├── view-site.md             # Helper: read main project files
│   └── marketing/               # 43 specialist skills
│       ├── README.md            # Navigation guide
│       ├── _foundation/         # product-marketing-context
│       ├── conversion/          # CRO skills (5 installed)
│       ├── content-copy/        # Content skills (3 installed)
│       ├── paid-distribution/   # Paid ads (2 installed)
│       ├── seo-discovery/       # (pending)
│       ├── measurement/         # (pending)
│       ├── retention/           # (pending)
│       ├── growth-engineering/  # (pending)
│       ├── strategy/            # (pending)
│       └── sales-revops/        # (pending)
│
└── recommendations/             # Output directory
    └── SETUP-SUMMARY.md         # Setup record
```

---

## Installed Skills (11 total)

### 🎯 Strategic
- `/cmo` - Marketing leadership, GTM planning

### 🔧 Foundation
- `/product-marketing-context` - Create/update product context
- `/view-site` - Helper to read main project files

### 📈 Conversion (5)
- `/page-cro` - Landing page optimization
- `/signup-flow-cro` - Registration flow optimization
- `/onboarding-cro` - Post-signup activation
- `/form-cro` - Lead capture forms
- `/popup-cro` - Modals and overlays

### ✍️ Content & Copy (3)
- `/copywriting` - Marketing copy for any page
- `/email-sequence` - Automated email flows
- `/cold-email` - B2B outreach sequences

### 💰 Paid & Distribution (2)
- `/paid-ads` - Paid advertising strategy
- `/ad-creative` - Ad creative generation

**32 more skills available** - See [skill map](.claude/commands/marketing/README.md)

---

## Common Workflows

### Optimize Homepage
```bash
/page-cro                                 # Analyze
# → recommendations/homepage-cro-[date].md

cd ~/make-it && /execute                  # Implement
```

### Write Copy
```bash
/copywriting "homepage hero section"      # Generate alternatives
# → Copy 3 options with rationale

cd ~/make-it && /execute                  # Apply approved version
```

### Plan Content
```bash
/content-strategy                         # Plan topics
# → recommendations/content-strategy-[date].md

/copywriting "blog post: [topic]"         # Write first post
# → recommendations/blog-[topic]-[date].md

cd ~/make-it && /execute                  # Publish
```

### Launch Feature
```bash
/cmo "plan launch for [feature]"          # Strategic direction
/launch-strategy                          # Detailed plan
/copywriting "announcement email"         # Copy
/email-sequence "launch sequence"         # Email flow
/social-content "launch posts"            # Social posts

cd ~/make-it && /execute                  # Implement campaign
```

---

## How Projects Communicate

### Marketing → Main
1. Marketing project reads main project files (read-only)
2. Generates recommendations → `recommendations/[topic]-[date].md`
3. Main project reads recommendations
4. Implements via `/execute`

### Shared Resources
- **Product context**: `.agents/product-marketing-context.md`
  - Created in marketing project
  - Symlinked to main project
  - Single source of truth

- **Helper skills**:
  - Main: `/view-marketing-recommendations`
  - Marketing: `/view-site`

See [CROSS-PROJECT-COMMUNICATION.md](CROSS-PROJECT-COMMUNICATION.md) for details.

---

## Key Principles

✅ **Marketing project = Advisory**
- Generates strategy, copy, recommendations
- Read-only access to main project
- Never modifies code

✅ **Main project = Implementation**
- Reads recommendations
- Implements via `/execute`
- Commits and deploys

✅ **Clean Separation**
- Marketing conversations stay focused on strategy
- Dev conversations stay focused on implementation
- No cross-contamination

---

## Documentation

| Document | Purpose |
|----------|---------|
| [QUICKSTART.md](QUICKSTART.md) | Get started in 5 minutes |
| [CLAUDE.md](CLAUDE.md) | Full project documentation |
| [CROSS-PROJECT-COMMUNICATION.md](CROSS-PROJECT-COMMUNICATION.md) | Communication patterns |
| [.claude/commands/marketing/README.md](.claude/commands/marketing/README.md) | Skill navigation guide |
| [recommendations/SETUP-SUMMARY.md](recommendations/SETUP-SUMMARY.md) | Setup record |

---

## Main Project

**Location**: `~/make-it`  
**Purpose**: Feature development, bug fixes, deployments  
**Link**: See `.claude/CLAUDE.md` for cross-reference

---

## Status

**Created**: 2026-05-12  
**Skills Installed**: 11 / 43 (P0-P1 priority)  
**Next Step**: `/product-marketing-context`

---

**Ready to use!** Run `/product-marketing-context` to get started.

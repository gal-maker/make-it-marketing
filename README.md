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

## Getting Started

### Prerequisites
- [Claude Code](https://claude.ai/code) installed
- Git installed
- Access to Make-It.ai GitHub repositories

### Step-by-Step Setup

#### 1. Clone Both Projects

The marketing project reads from the main project, so you need both:

```bash
cd ~

# Clone main project
git clone https://github.com/gal-maker/make-it.git

# Clone marketing project
git clone https://github.com/gal-maker/make-it-marketing.git
```

**Required directory structure** (sibling directories):
```
/Users/[your-username]/
├── make-it/              # Main dev project
└── make-it-marketing/    # Marketing project (this one)
```

#### 2. Fix Symlink for Your System

The product context is shared between projects via symlink. The symlink uses a relative path, but you may need to verify it works:

```bash
# Check if symlink works
ls -la ~/make-it/.agents/product-marketing-context.md

# If broken, recreate it
cd ~/make-it/.agents
rm -f product-marketing-context.md
ln -s ../../make-it-marketing/.agents/product-marketing-context.md product-marketing-context.md
```

#### 3. Open Marketing Project in Claude Code

```bash
cd ~/make-it-marketing
# Then open Claude Code in this directory
```

#### 4. Create Product Marketing Context

In Claude Code, run:
```
/product-marketing-context
```

This will:
- Read main project's landing pages, blog, README
- Auto-draft product/audience/positioning context
- Save to `.agents/product-marketing-context.md`
- Become available in both projects via symlink

Review and refine the generated context.

#### 5. Try Your First Analysis

```
/page-cro
```

This will:
- Read `../make-it/webapp/src/components/HomePage.tsx`
- Analyze conversion optimization opportunities
- Generate `recommendations/homepage-cro-[date].md`

#### 6. Implement Recommendations

Switch to main project:
```bash
cd ~/make-it
```

In Claude Code:
```
/view-marketing-recommendations
```

Read the recommendation, then implement:
```
/execute "Update homepage hero section per homepage-cro-2026-05-13.md"
```

---

## Daily Usage

Once set up, the workflow is simple:

**Analyze in marketing project:**
```bash
cd ~/make-it-marketing
/page-cro
/copywriting "homepage hero section"
/content-strategy
```

**Implement in main project:**
```bash
cd ~/make-it
/view-marketing-recommendations
/execute
```

See [QUICKSTART.md](QUICKSTART.md) for more examples and workflows.

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

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

## Setup for New Users

### Prerequisites
- [Claude Code](https://claude.ai/code) installed
- Git installed
- Access to Make-It.ai repositories

### Step 1: Clone Both Projects

The marketing project **reads from the main project**, so you need both:

```bash
# Choose a parent directory (e.g., your home directory)
cd ~

# Clone main development project
git clone https://github.com/gal-maker/make-it.git

# Clone marketing project
git clone https://github.com/naltony/make-it-marketing.git
# or if under organization:
# git clone https://github.com/gal-maker/make-it-marketing.git
```

**Important**: Both projects must be sibling directories:
```
/Users/[your-username]/
├── make-it/              # Main dev project
└── make-it-marketing/    # Marketing project (this)
```

### Step 2: Fix Symlink for Your System

The product context is shared via symlink. Recreate it for your system:

```bash
cd ~/make-it/.agents
rm product-marketing-context.md
ln -s ../../make-it-marketing/.agents/product-marketing-context.md product-marketing-context.md
```

Verify it works:
```bash
ls -la ~/make-it/.agents/
# Should show: product-marketing-context.md -> ../../make-it-marketing/.agents/product-marketing-context.md
```

### Step 3: Open Marketing Project in Claude Code

```bash
cd ~/make-it-marketing
# Open in Claude Code (exact command depends on your setup)
```

### Step 4: Create Product Marketing Context

In Claude Code, run:
```
/product-marketing-context
```

This skill will:
1. Read main project's landing pages, blog, README
2. Auto-draft product/audience/positioning context
3. Save to `.agents/product-marketing-context.md`
4. Available in both projects via symlink

Review and refine the generated context.

### Step 5: Test Your Setup

Try your first marketing analysis:
```
/page-cro
```

This will:
1. Read `../make-it/webapp/src/components/HomePage.tsx`
2. Generate CRO recommendations
3. Save to `recommendations/homepage-cro-[date].md`

### Step 6: Implement a Recommendation

Switch to main project:
```bash
cd ~/make-it
```

In Claude Code:
```
/view-marketing-recommendations
```

Read a recommendation, then:
```
/execute "Implement [specific changes from recommendation]"
```

---

## Setup for Project Creator (Already Done)

If you're setting this up from scratch (not cloning):

1. Create marketing project directory
2. Install skills from external package
3. Configure CLAUDE.md and documentation
4. Create symlink in main project
5. Push both projects to GitHub

See [recommendations/SETUP-SUMMARY.md](recommendations/SETUP-SUMMARY.md) for full setup record.

---

## First-Time Usage (After Setup)

1. **Switch to this project:**
   ```bash
   cd ~/make-it-marketing
   ```

2. **Run a marketing skill:**
   ```
   /page-cro
   /copywriting "homepage hero section"
   /content-strategy
   ```

3. **Implement in main project:**
   ```bash
   cd ~/make-it
   /view-marketing-recommendations
   /execute
   ```

See [QUICKSTART.md](QUICKSTART.md) for more examples.

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

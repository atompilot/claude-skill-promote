<p align="center">
  <h1 align="center">Claude Skill Promote</h1>
  <p align="center">
    <strong>Promote your projects — without leaving the terminal.</strong>
  </p>
  <p align="center">
    <a href="#installation">Install</a> &middot;
    <a href="#commands">Commands</a> &middot;
    <a href="#what-it-does">What It Does</a> &middot;
    <a href="./README_CN.md">中文</a>
  </p>
</p>

---

A Claude Code skill that turns promotion from "I should probably do this" into a structured, repeatable workflow. Extensible via sub-skills for different promotion targets.

```bash
/promote                        # Auto-detect what to promote
/promote github                 # GitHub open-source project
/promote github readme          # Audit & fix README
```

> **README audits. Blog post generation. Social media content. Launch checklists. Growth tracking.**
> All powered by your project's actual code and metadata — not generic templates.

---

## Architecture

```
promote (router)
├── subs/github.md     ✅ GitHub open-source projects
├── subs/appstore.md   🔜 iOS/macOS App Store
├── subs/webapp.md     🔜 Web products / SaaS
└── subs/npm.md        🔜 npm/PyPI packages
```

The main skill auto-detects your project type and routes to the right sub-skill. You can also invoke sub-skills directly.

## Why Claude Skill Promote?

| Without | With |
|---|---|
| "I'll promote it later" (never happens) | Structured checklist tells you exactly what to do next |
| Generic marketing advice | Channel recommendations based on your actual tech stack |
| Staring at a blank page for blog posts | Full draft generated from your README and code |
| README missing critical elements | Automated audit catches what you missed |
| No idea if promotion is working | Growth metrics from GitHub API in one command |

## Installation

```bash
# Plugin marketplace (recommended)
claude plugin marketplace add atompilot/claude-skill-promote
claude plugin install claude-skill-promote@claude-skill-promote

# Or copy manually
cp -r skills/promote ~/.claude/skills/
```

## Commands (GitHub Sub-Skill)

| Command | What it does |
|---------|-------------|
| `/promote` | Auto-detect project type and run full diagnostic |
| `/promote github` | Full GitHub promotion diagnostic — profile, README audit, channels, action plan |
| `/promote github readme` | Audit README quality (13-point checklist) and fix issues |
| `/promote github blog [channel]` | Generate a blog post for dev.to / Medium / 掘金 / V2EX / 知乎 |
| `/promote github post [platform]` | Generate social content for Twitter / HN / Reddit / V2EX |
| `/promote github launch` | First-launch checklist with pre/during/post actions |
| `/promote github status` | Growth metrics from GitHub API (stars, traffic, referrers) |

## What It Does

### 1. Project Profiling

Automatically reads your repo metadata, README, tech stack, and git history to build a project profile. Determines your promotion stage (cold start → growth → mature) and tailors advice accordingly.

### 2. README Audit

13-point quality checklist across three tiers:

- **Must-have** (❌ if missing): Value proposition, Quick Start, LICENSE
- **Recommended** (⚠️ if missing): GIF/screenshot, badges, comparison table, usage examples, target audience
- **Bonus**: Contributing guide, changelog, i18n, GitHub description, topics

Doesn't just flag issues — offers to fix them directly.

### 3. Channel Strategy

Recommends promotion channels based on your **actual tech stack**, not generic advice:

| Your Stack | Recommended Channels |
|-----------|---------------------|
| Claude Code / AI Agent | Anthropic Discord, AI Twitter, r/ClaudeAI |
| React / Next.js | React Discord, Vercel Discussions, r/reactjs |
| Python / ML | PyData, MLOps Community, r/MachineLearning |
| Go | Gophers Slack, r/golang |
| Rust | Rust Users Forum, r/rust |
| Swift / iOS | Swift Forums, r/iOSProgramming |
| DevOps / Infra | CNCF Slack, r/selfhosted |
| CLI tools | Hacker News (Show HN), r/commandline |

### 4. Content Generation

Generates platform-specific content with the right tone:

- **Blog posts**: Pain-point driven, with real code examples from your project
- **Twitter threads**: Problem→Solution→CTA format, ≤280 chars per tweet
- **HN posts**: Minimal, direct, no marketing language
- **V2EX posts**: Conversational Chinese, story-driven
- **Reddit posts**: Community-first, value before self-promotion

### 5. Growth Tracking

```
⭐ Stars: 127 (+23 this week)
📈 Views: 1,842 (Unique: 892)
🔗 Top referrers: Hacker News, Twitter, dev.to
```

## Anti-Patterns (Built-in Guards)

Claude Skill Promote actively prevents common promotion mistakes:

- **No star-farming** — never suggests mutual-star groups
- **No marketing buzzwords** — flags "revolutionary", "amazing", "best" in generated content
- **No cold-spam** — won't generate content for communities you haven't engaged with
- **No one-shot launches** — emphasizes sustained promotion over single-day efforts

## Supported Languages

- Generated content: English and Chinese
- Platform coverage: Global (HN, Reddit, Twitter, dev.to, Medium) + Chinese (V2EX, 掘金, 知乎)

## License

MIT

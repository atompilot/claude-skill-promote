<p align="center">
  <h1 align="center">Claude Skill Promote</h1>
  <p align="center">
    <strong>Promote your projects — without leaving the terminal.</strong>
  </p>
  <p align="center">
    <a href="#skills">Skills</a> &middot;
    <a href="#installation">Install</a> &middot;
    <a href="#promote-github">GitHub</a> &middot;
    <a href="./README_CN.md">中文</a>
  </p>
</p>

---

A collection of Claude Code skills for project promotion. Each promotion target is an **independent skill** — install only what you need.

---

## Skills

| Skill | Command | Status | Description |
|-------|---------|--------|-------------|
| **promote-github** | `/promote-github` | ✅ Available | GitHub open-source project promotion |
| promote-video | `/promote-video` | 🔜 Planned | Short-form video promotion |
| promote-appstore | `/promote-appstore` | 🔜 Planned | iOS/macOS App Store optimization |
| promote-webapp | `/promote-webapp` | 🔜 Planned | Web product / SaaS growth |
| promote-npm | `/promote-npm` | 🔜 Planned | npm/PyPI package promotion |

## Installation

```bash
# Plugin marketplace (recommended)
claude plugin marketplace add atompilot/claude-skill-promote
claude plugin install claude-skill-promote@claude-skill-promote

# Or copy individual skills
cp -r skills/promote-github ~/.claude/skills/
```

---

## Promote GitHub

Structured workflow for promoting GitHub open-source projects.

### Commands

| Command | What it does |
|---------|-------------|
| `/promote-github` | Full diagnostic — project profile, README audit, channels, action plan |
| `/promote-github readme` | Audit README quality (13-point checklist) and fix issues |
| `/promote-github blog [channel]` | Generate a blog post for dev.to / Medium / 掘金 / V2EX / 知乎 |
| `/promote-github post [platform]` | Generate social content for Twitter / HN / Reddit / V2EX |
| `/promote-github launch` | First-launch checklist with pre/during/post actions |
| `/promote-github status` | Growth metrics from GitHub API (stars, traffic, referrers) |

### What It Does

**1. Project Profiling** — Reads repo metadata, README, tech stack, git history. Determines promotion stage (cold start → growth → mature).

**2. README Audit** — 13-point checklist: value proposition, Quick Start, LICENSE, GIF/screenshot, badges, comparison table, usage examples, target audience, contributing guide, changelog, i18n, description, topics.

**3. Channel Strategy** — Recommends channels based on your tech stack:

| Your Stack | Recommended Channels |
|-----------|---------------------|
| Claude Code / AI Agent | Anthropic Discord, AI Twitter, r/ClaudeAI |
| React / Next.js | React Discord, Vercel Discussions, r/reactjs |
| Python / ML | PyData, MLOps Community, r/MachineLearning |
| Go | Gophers Slack, r/golang |
| Rust | Rust Users Forum, r/rust |
| Swift / iOS | Swift Forums, r/iOSProgramming |
| CLI tools | Hacker News (Show HN), r/commandline |

**4. Content Generation** — Platform-specific tone: blog posts (pain-point driven), Twitter threads (Problem→Solution→CTA), HN posts (minimal, no marketing), V2EX posts (conversational Chinese), Reddit posts (community-first).

**5. Growth Tracking** — Stars, forks, traffic views/clones, referrer sources via GitHub API.

### Anti-Patterns (Built-in Guards)

- **No star-farming** — never suggests mutual-star groups
- **No marketing buzzwords** — flags "revolutionary", "amazing", "best"
- **No cold-spam** — won't generate content for unfamiliar communities
- **No one-shot launches** — emphasizes sustained promotion

## License

MIT

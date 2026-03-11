<p align="center">
  <h1 align="center">Claude Skill Promote</h1>
  <p align="center">
    <strong>不离开终端，推广你的项目。</strong>
  </p>
  <p align="center">
    <a href="#skill-列表">Skill 列表</a> &middot;
    <a href="#安装">安装</a> &middot;
    <a href="#promote-github">GitHub 推广</a> &middot;
    <a href="./README.md">English</a>
  </p>
</p>

---

一组用于项目推广的 Claude Code skills。每个推广对象是一个**独立 skill**——按需安装。

---

## Skill 列表

| Skill | 命令 | 状态 | 说明 |
|-------|------|------|------|
| **promote-github** | `/promote-github` | ✅ 可用 | GitHub 开源项目推广 |
| promote-video | `/promote-video` | 🔜 规划 | 短视频推广 |
| promote-appstore | `/promote-appstore` | 🔜 规划 | App Store 应用优化 |
| promote-webapp | `/promote-webapp` | 🔜 规划 | Web 产品 / SaaS 增长 |
| promote-npm | `/promote-npm` | 🔜 规划 | npm/PyPI 包推广 |

## 安装

```bash
# Plugin 市场（推荐）
claude plugin marketplace add atompilot/claude-skill-promote
claude plugin install claude-skill-promote@claude-skill-promote

# 或单独复制某个 skill
cp -r skills/promote-github ~/.claude/skills/
```

---

## Promote GitHub

GitHub 开源项目推广的结构化工作流。

### 命令

| 命令 | 功能 |
|------|------|
| `/promote-github` | 完整推广诊断 — 项目画像 + README 审计 + 渠道推荐 + 行动计划 |
| `/promote-github readme` | README 质量审计（13 项清单）并直接修复 |
| `/promote-github blog [渠道]` | 生成博文（dev.to / Medium / 掘金 / V2EX / 知乎） |
| `/promote-github post [平台]` | 生成帖文（Twitter / HN / Reddit / V2EX） |
| `/promote-github launch` | 首发 checklist（发布前 / 发布日 / 发布后 48h） |
| `/promote-github status` | 增长指标（Stars / 流量 / 来源） |

### 核心能力

**1. 项目画像** — 自动读取仓库元数据、README、技术栈、git 历史。判断推广阶段（冷启动 → 增长 → 成熟）。

**2. README 审计** — 13 项检查：价值主张、Quick Start、LICENSE、GIF/截图、badges、对比表、使用示例、目标用户、Contributing 指南、Changelog、多语言、Description、Topics。

**3. 渠道策略** — 根据技术栈推荐渠道：

| 技术栈 | 推荐渠道 |
|--------|---------|
| Claude Code / AI Agent | Anthropic Discord、AI Twitter、r/ClaudeAI |
| React / Next.js | React Discord、Vercel Discussions、r/reactjs |
| Python / ML | PyData、MLOps Community、r/MachineLearning |
| Go | Gophers Slack、r/golang |
| Rust | Rust Users Forum、r/rust |
| Swift / iOS | Swift Forums、r/iOSProgramming |
| CLI 工具 | Hacker News (Show HN)、r/commandline |

**4. 内容生成** — 按平台风格定制：博文（痛点导向）、Twitter Thread（问题→方案→CTA）、HN 帖（极简）、V2EX 帖（口语化）、Reddit 帖（社区优先）。

**5. 增长追踪** — Stars、forks、流量、来源（通过 GitHub API）。

### 内置防坑

| 规则 | 为什么 |
|------|--------|
| **不刷 star** | GitHub 会检测，虚假 star 无价值 |
| **不用营销词** | 自动标记 "revolutionary" "amazing" 等 |
| **不冷启动硬推** | 不在陌生社区发广告 |
| **不一次性发完** | 渠道间隔 1-2 天，避免 spam |

## License

MIT

<p align="center">
  <h1 align="center">Claude Skill Promote</h1>
  <p align="center">
    <strong>不离开终端，推广你的项目。</strong>
  </p>
  <p align="center">
    <a href="#安装">安装</a> &middot;
    <a href="#命令">命令</a> &middot;
    <a href="#核心能力">核心能力</a> &middot;
    <a href="./README.md">English</a>
  </p>
</p>

---

一个 Claude Code skill，把"我应该推广一下"变成结构化、可重复的工作流。通过子 skill 扩展支持不同推广对象。

```bash
/promote                        # 自动检测推广对象
/promote github                 # GitHub 开源项目推广
/promote github readme          # README 审计
```

> **README 审计、博文生成、社交帖文、首发清单、增长追踪。**
> 基于你项目的真实代码和元数据生成内容，不是通用模板。

---

## 架构

```
promote（路由器）
├── subs/github.md     ✅ GitHub 开源项目
├── subs/appstore.md   🔜 App Store 应用
├── subs/webapp.md     🔜 Web 产品 / SaaS
└── subs/npm.md        🔜 npm/PyPI 包
```

主 skill 自动检测项目类型，路由到对应子 skill。也可以直接调用子 skill。

## 为什么选 Claude Skill Promote？

| 没有它 | 有了它 |
|--------|--------|
| "等有空了再推广"（永远不会有空） | 结构化清单，明确告诉你下一步做什么 |
| 看了一堆通用推广建议 | 根据你的技术栈推荐具体渠道 |
| 对着空白页面写博文 | 从你的 README 和代码直接生成完整草稿 |
| README 缺了关键元素自己不知道 | 13 项自动审计，逐项修复 |
| 推广了也不知道效果如何 | 一条命令查看增长指标 |

## 安装

```bash
# Plugin 市场（推荐）
claude plugin marketplace add atompilot/claude-skill-promote
claude plugin install claude-skill-promote@claude-skill-promote

# 或手动复制
cp -r skills/promote ~/.claude/skills/
```

## 命令

### GitHub 推广（已实现）

| 命令 | 功能 |
|------|------|
| `/promote` | 自动检测项目类型，执行完整推广诊断 |
| `/promote github` | GitHub 完整推广诊断 — 项目画像 + README 审计 + 渠道推荐 + 行动计划 |
| `/promote github readme` | README 质量审计（13 项清单）并直接修复 |
| `/promote github blog [渠道]` | 生成博文草稿（dev.to / Medium / 掘金 / V2EX / 知乎） |
| `/promote github post [平台]` | 生成社交帖文（Twitter / HN / Reddit / V2EX） |
| `/promote github launch` | 首发 checklist（发布前 / 发布日 / 发布后 48h） |
| `/promote github status` | 增长指标（Stars / 流量 / 来源） |

## 核心能力

### 1. 项目画像

自动读取仓库元数据、README、技术栈和 git 历史，生成项目画像。判断推广阶段（冷启动 → 增长 → 成熟），针对性给出策略。

### 2. README 审计

13 项质量检查，分三个等级：

- **必备**（缺失 = ❌）：价值主张、Quick Start、LICENSE
- **推荐**（缺失 = ⚠️）：GIF/截图、badges、对比表、使用示例、目标用户
- **加分**：Contributing 指南、Changelog、多语言、GitHub Description、Topics

不只是标问题——直接帮你修。

### 3. 渠道策略

根据**技术栈**推荐推广渠道，而非千篇一律的通用建议：

| 技术栈 | 推荐渠道 |
|--------|---------|
| Claude Code / AI Agent | Anthropic Discord、AI Twitter、r/ClaudeAI |
| React / Next.js | React Discord、Vercel Discussions、r/reactjs |
| Python / ML | PyData、MLOps Community、r/MachineLearning |
| Go | Gophers Slack、r/golang |
| Rust | Rust Users Forum、r/rust |
| Swift / iOS | Swift Forums、r/iOSProgramming |
| DevOps / 基础设施 | CNCF Slack、r/selfhosted |
| CLI 工具 | Hacker News (Show HN)、r/commandline |

### 4. 内容生成

按平台风格生成定制内容：

- **博文**：痛点导向，包含项目真实代码示例
- **Twitter Thread**：问题→方案→CTA，每条 ≤ 280 字
- **HN 帖**：极简直接，不用营销词
- **V2EX 帖**：口语化、故事感
- **Reddit 帖**：社区优先，先给价值再提项目

### 5. 增长追踪

```
⭐ Stars: 127 (+23 本周)
📈 浏览: 1,842 (独立: 892)
🔗 来源 Top 3: Hacker News, Twitter, dev.to
```

## 内置防坑

| 规则 | 为什么 |
|------|--------|
| **不刷 star** | GitHub 会检测，虚假 star 不带来真实用户 |
| **不用营销词** | 自动检查并标记 "revolutionary" "amazing" 等词 |
| **不冷启动硬推** | 不在陌生社区直接发广告 |
| **不一次性发完** | 渠道间隔 1-2 天，避免被标记为 spam |

## 支持语言

- 生成内容：中文 + 英文
- 平台覆盖：全球（HN、Reddit、Twitter、dev.to、Medium）+ 中文（V2EX、掘金、知乎）

## License

MIT

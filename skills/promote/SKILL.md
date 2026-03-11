---
name: promote
description: >
  通用推广工作流。根据推广对象类型（GitHub 项目、产品、个人品牌等）路由到对应子 skill，
  提供内容生成、渠道策略、受众分析、增长追踪等能力。
  触发词：推广、promote、宣传、marketing、写博文、发帖、launch、growth、增长。
version: 1.0.0
source: claude-skill-promote
license: MIT
author: Atompilot
keywords: ["promote", "marketing", "growth", "launch", "content"]
---

# Promote — 通用推广 Skill

> 系统化推广你的项目、产品或品牌。

---

## 触发方式

```
/promote                        # 自动检测推广对象，路由到对应子 skill
/promote github                 # 直接进入 GitHub 开源项目推广
/promote github readme          # GitHub 项目 README 审计
/promote github blog [渠道]     # 为 GitHub 项目生成博文
/promote github post [平台]     # 为 GitHub 项目生成社交帖文
/promote github launch          # GitHub 项目首发 checklist
/promote github status          # GitHub 项目增长指标
```

**ARGUMENTS**: $ARGUMENTS

---

## Phase 0: 推广对象检测

每次执行 `/promote`（无子命令）时，自动检测当前项目类型：

```bash
# 检测 Git 仓库 + 公开 remote → GitHub 开源项目
git remote -v 2>/dev/null | grep -q "github.com" && echo "github"

# 检测 App Store 相关（*.xcodeproj, *.xcworkspace）→ iOS/macOS 应用
ls *.xcodeproj *.xcworkspace 2>/dev/null && echo "app"

# 检测 Web 应用（有部署配置：vercel.json, netlify.toml, Dockerfile）
ls vercel.json netlify.toml fly.toml render.yaml 2>/dev/null && echo "webapp"

# 检测 npm 包（package.json 有 "publishConfig" 或 "bin"）
grep -q '"publishConfig"\|"bin"' package.json 2>/dev/null && echo "npm-package"
```

### 路由规则

| 检测结果 | 推广类型 | 子 Skill |
|---------|---------|---------|
| GitHub 公开仓库 | 开源项目推广 | `subs/github.md` ✅ |
| iOS/macOS 应用 | App Store 推广 | `subs/appstore.md`（🔜 规划中） |
| Web 应用 + 部署 | SaaS/Web 产品推广 | `subs/webapp.md`（🔜 规划中） |
| npm 包 | 包生态推广 | `subs/npm.md`（🔜 规划中） |
| 无法自动检测 | 询问用户 | — |

当前已实现：**GitHub 开源项目推广**。其他类型 coming soon。

### 无法检测时

```
📣 我需要了解你要推广什么：

  a) GitHub 开源项目 — README 优化、社区推广、增长追踪
  b) iOS/macOS 应用 — App Store 优化、评价管理（🔜 开发中）
  c) Web 产品/SaaS — Landing page、SEO、用户获取（🔜 开发中）
  d) npm/PyPI 包 — 包生态推广、文档优化（🔜 开发中）
  e) 其他 — 告诉我具体场景

选择？
```

---

## 通用推广原则（所有子 skill 共享）

### 内容生成规则

| 规则 | 说明 |
|------|------|
| **痛点导向** | 标题和开头从用户痛点切入，而非产品功能 |
| **真实具体** | 使用真实数据、代码、截图，不用虚构案例 |
| **平台适配** | 每个平台有自己的风格和规则，不一稿多投 |
| **禁止营销词** | 生成文本中不允许出现 "revolutionary" "amazing" "best" "game-changer" |
| **CTA 克制** | 号召行动放在末尾，一句话即可，不要反复推销 |

### 避坑规则

| 陷阱 | 为什么 | 替代方案 |
|------|--------|---------|
| 刷数据（star/下载/评分） | 平台检测 + 虚假数据无价值 | 靠内容和社区自然增长 |
| 一稿多投 | 每个平台的用户期望不同 | 按平台风格定制内容 |
| 只发一次就等着 | 推广是持续行为 | 按节奏持续输出 |
| 冷启动硬推 | 社区反感广告 | 先贡献价值，再自然提及 |
| 忽略反馈 | 不回复 = 无人维护 | 48 小时内回复所有评论 |

### 内容存储

所有子 skill 生成的推广内容统一存储：

```
docs/promote/
├── blog/                    # 博文草稿
│   ├── devto-2026-03-11.md
│   └── juejin-2026-03-11.md
├── posts/                   # 社交帖文
│   ├── twitter-2026-03-11.md
│   └── hn-2026-03-11.md
└── status-log.md            # 增长记录
```

---

## 子 Skill 目录

| 子 Skill | 文件 | 状态 | 说明 |
|----------|------|------|------|
| GitHub 开源项目 | `subs/github.md` | ✅ 可用 | README 审计、渠道策略、内容生成、增长追踪 |
| App Store 应用 | `subs/appstore.md` | 🔜 规划 | ASO、评价管理、截图优化 |
| Web 产品/SaaS | `subs/webapp.md` | 🔜 规划 | Landing page、SEO、用户获取 |
| npm/PyPI 包 | `subs/npm.md` | 🔜 规划 | 包生态推广、文档优化 |

> 新增子 skill 时在此表中登记。

---

## 自我进化协议

> 本 skill 在日常使用中自动进化。无需显式触发。

### 何时提议进化

| 信号 | 示例 | 行为 |
|------|------|------|
| 新推广类型需求 | 用户要推广 Chrome 扩展 | 提议新增对应子 skill |
| 通用规则优化 | 用户发现某条避坑规则不适用 | 提议更新通用原则 |
| 路由规则不准 | 检测到的推广类型不对 | 提议调整检测逻辑 |
| 新平台涌现 | 用户提到 Bluesky / 小红书 | 提议加入渠道矩阵 |

### 确认流程

```
🔔 我注意到一个可以写入 skill 的改进：

{描述}

建议写入：promote/SKILL.md 的「{章节名}」
内容预览：
---
{内容}
---

是否写入？(Y/N)
```

写入后 version patch +1。

### Size Guard

**守护线**：主 SKILL.md ≤ 8KB（路由器角色，保持精简）
各子 skill ≤ 15KB

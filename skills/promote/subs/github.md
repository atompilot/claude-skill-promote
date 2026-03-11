# GitHub 开源项目推广

> 子 Skill：`promote/subs/github.md`
> 父 Skill：`promote/SKILL.md`

---

## 触发方式

```
/promote github                 # 完整推广诊断（首次使用推荐）
/promote github readme          # README 质量审计 + 优化
/promote github blog [渠道]     # 生成推广博文（dev.to / 掘金 / Medium）
/promote github post [平台]     # 生成社交帖文（Twitter / HN / V2EX / Reddit）
/promote github launch          # 生成首发 checklist
/promote github status          # 查看增长指标
```

也可通过父 skill 自动路由进入（检测到 GitHub 公开仓库时）。

---

## Phase 0: 项目感知

自动收集项目信息：

```bash
# 1. 仓库元数据
gh repo view --json name,description,stargazerCount,forkCount,createdAt,licenseInfo,repositoryTopics,homepageUrl

# 2. README
cat README.md

# 3. 技术栈（package.json / go.mod / Cargo.toml / setup.py 等）
ls package.json go.mod Cargo.toml setup.py pyproject.toml *.xcodeproj 2>/dev/null

# 4. 项目年龄和活跃度
git log --oneline | head -20
git log --since="30 days ago" --oneline | wc -l
```

### 项目画像

```
📊 项目画像

仓库：{owner}/{repo}
描述：{description}
技术栈：{language} + {framework}
Stars：{stargazerCount} | Forks：{forkCount}
创建时间：{createdAt} | 最近 30 天提交：{commitCount}
License：{license}
Topics：{topics}

推广阶段：{阶段}
```

### 推广阶段判断

| Stars | 项目年龄 | 阶段 | 策略侧重 |
|-------|---------|------|---------|
| 0-50 | < 1 月 | 🚀 冷启动 | README 打磨 + 首发渠道 |
| 0-50 | > 1 月 | 🧊 沉默期 | 找到产品问题或推广渠道问题 |
| 50-500 | 任意 | 📈 增长期 | 内容营销 + 社区建设 |
| 500+ | 任意 | 🌟 成熟期 | 生态集成 + 演讲 + 贡献者培养 |

---

## 命令：完整诊断

### Step 1: 展示项目画像

### Step 2: README 快速体检

按 README 审计清单打分（详见 `readme` 子命令）。

### Step 3: 渠道推荐

根据项目**技术栈和生态**推荐渠道：

| 技术栈/生态 | 核心社区 | Awesome List | Subreddit |
|------------|---------|-------------|-----------|
| Claude Code / AI Agent | Anthropic Discord, AI Twitter | awesome-claude-code | r/ClaudeAI |
| React / Next.js | React Discord, Vercel Discussions | awesome-react | r/reactjs |
| Python / ML | PyData, MLOps Community | awesome-python, awesome-ml | r/MachineLearning |
| Go | Gophers Slack | awesome-go | r/golang |
| Rust | Rust Users Forum | awesome-rust | r/rust |
| Swift / iOS | Swift Forums | awesome-swift | r/iOSProgramming |
| DevOps / Infra | CNCF Slack | awesome-selfhosted | r/selfhosted |
| CLI 工具 | Hacker News (Show HN) | awesome-cli-apps | r/commandline |
| 通用开发工具 | dev.to, Hacker News | — | r/programming |

不在表中的技术栈：
1. 检查依赖文件识别核心框架
2. 搜索 `awesome-{framework}` 是否存在
3. 搜索框架官方 Discord / Slack / Forum

### Step 4: 生成行动计划

```
📋 推广行动计划（{阶段}）

🔴 本周必做：
  1. [ ] {具体动作 + 预期效果}
  2. [ ] {具体动作 + 预期效果}

🟡 下周推荐：
  3. [ ] {具体动作}
  4. [ ] {具体动作}

🟢 持续进行：
  5. [ ] {具体动作}

💡 执行任何一项，直接告诉我，我帮你生成内容。
```

---

## 命令：README 审计

逐项检查 README.md，每项 ✅ / ⚠️ / ❌ 评级。

### 必备元素（缺失 = ❌）

| # | 检查项 | 检查方式 | 为什么重要 |
|---|--------|---------|-----------|
| 1 | **首屏价值主张** | README 前 5 行内有一句话说明 | 路人 10 秒决定去留 |
| 2 | **安装/Quick Start** | 有 install / setup / getting started 章节 | 30 秒跑通 = 转化 |
| 3 | **LICENSE** | LICENSE 文件存在 | 企业用户硬性要求 |

### 强烈推荐（缺失 = ⚠️）

| # | 检查项 | 检查方式 | 为什么重要 |
|---|--------|---------|-----------|
| 4 | **视觉演示** | 引用了 .gif / .png / .mp4 / 图片 URL | 视觉比文字有效 10x |
| 5 | **Badges** | 有 `![` 开头的 badge 图片 | 建立信任 |
| 6 | **对比表** | 有 With/Without 或 vs 对比 | 强化差异价值 |
| 7 | **使用示例** | 有代码块展示核心用法 | 让用户"看到"而非"想象" |
| 8 | **目标用户** | 说明了"谁应该用这个" | 帮读者自我筛选 |

### 加分项（缺失 = 灰色）

| # | 检查项 | 检查方式 |
|---|--------|---------|
| 9 | **Contributing 指南** | 有 CONTRIBUTING.md 或相关章节 |
| 10 | **Changelog** | 有 CHANGELOG.md |
| 11 | **多语言** | 有中英文双版本 |
| 12 | **GitHub Description** | `gh repo view --json description` 精准 |
| 13 | **Topics/Tags** | `gh repo view --json repositoryTopics` 充分 |

### 审计输出

```
📋 README 审计报告

得分：{X}/13

必备元素：
  1. ✅ 首屏价值主张 — "{描述}"
  2. ❌ 安装/Quick Start — 未找到
  3. ✅ LICENSE — MIT

强烈推荐：
  4. ❌ 视觉演示 — 没有 GIF/截图
  ...

🔧 修复建议（按优先级）：
1. [❌ 安装/Quick Start] 建议添加：
   ```bash
   {从依赖文件推断}
   ```

2. [❌ 视觉演示] 建议：
   - 录制终端 GIF：`brew install vhs && vhs record`
   - 或截图核心界面

要修哪些？（编号 / 全部 / 跳过）
```

用户确认后直接编辑 README.md。

---

## 命令：生成博文

### 支持渠道

| 渠道 | 语言 | 风格 | 长度 |
|------|------|------|------|
| `dev.to` | 英文 | 技术教程风 | 800-1500 词 |
| `medium` | 英文 | 叙事 + 技术 | 1000-2000 词 |
| `juejin` | 中文 | 技术实战 | 1500-3000 字 |
| `v2ex` | 中文 | 口语化 | 500-1000 字 |
| `zhihu` | 中文 | 深度分析 | 1500-3000 字 |

### 生成流程

**Step 1: 选角度**

| 角度 | 适用场景 | 标题模板 |
|------|---------|---------|
| 痛点驱动 | 解决明确痛点 | "{痛点} — Here's How I Fixed It" |
| 故事驱动 | 有趣的创作背景 | "Why I Built {项目名}" |
| 教程驱动 | 明确使用场景 | "How to {动作} with {项目名}" |
| 对比驱动 | 有明确竞品 | "{项目名} vs {竞品}" |
| 趋势驱动 | 踩中技术趋势 | "{趋势} Is Changing {领域}" |

**Step 2: 生成大纲** → 用户确认

**Step 3: 生成全文**

**写作规则**：
- 标题痛点导向，不要产品名导向
- 开头用真实场景，不要"在这篇文章中"
- 代码块可直接复制运行
- 不用 "amazing" "revolutionary" 等营销词
- CTA 放末尾，一句话

生成后写入 `docs/promote/blog/{渠道}-{日期}.md`。

---

## 命令：生成帖文

### 各平台模板

#### Twitter / X Thread

```
1/N {场景引出问题}
2/N {展示痛苦}
3/N {引出方案} 📎 建议配图
4/N {快速上手命令}
5/N {CTA + GitHub 链接}
```

#### Hacker News

```
标题：Show HN: {项目名} – {一句话（≤80 字）}
正文：2-3 段，覆盖问题、方案、差异化

⚠️ 工作日美东 8-10 AM 发 | 不用营销词 | 准备回答技术问题
```

#### V2EX

```
标题：口语化（"做了个工具解决 xxx 问题"）
节点：分享创造 / 程序员 / 开源软件
正文：故事化叙述 + 截图 + GitHub 链接

⚠️ 口语化真诚 | 认真回复评论
```

#### Reddit

```
Subreddit：{根据技术栈推荐}
正文：先说问题再引项目 | 不要 "I built" 开头 | 先给价值
```

#### Product Hunt

```
Tagline + Description + Makers Comment
```

生成后写入 `docs/promote/posts/{平台}-{日期}.md`。

---

## 命令：首发 Checklist

```
🚀 首发 Checklist

📦 发布前：
  - [ ] README 审计 ≥ 10/13
  - [ ] GitHub description 精准
  - [ ] Topics ≥ 3 个
  - [ ] LICENSE 存在
  - [ ] 有 GIF/截图
  - [ ] Quick Start 30 秒跑通
  - [ ] 无硬编码密钥 / debug 输出

📣 首发日（选工作日）：
  - [ ] HN Show HN（美东 8-10 AM）
  - [ ] Reddit（对应 subreddit）
  - [ ] Twitter/X Thread
  - [ ] V2EX + 掘金
  - [ ] 相关项目 Discussions/Discord

📈 首发后 48h：
  - [ ] 回复所有评论
  - [ ] 回复所有 Issues
  - [ ] PR 到 Awesome Lists
  - [ ] 记录各渠道数据
```

---

## 命令：增长指标

```bash
gh repo view --json stargazerCount,forkCount,watchers,openIssues
gh api repos/{owner}/{repo}/traffic/views
gh api repos/{owner}/{repo}/traffic/clones
gh api repos/{owner}/{repo}/traffic/popular/referrers
```

输出：

```
📊 {项目名} 增长报告

⭐ Stars: {count} ({趋势})
🍴 Forks: {count}
📈 14 天流量：Views {count} | Clones {count}
🔗 Top 来源：{referrer list}

💡 建议：{1-2 条具体建议}
```

---

## 社区建设检查

### 降低贡献门槛

- [ ] CONTRIBUTING.md 存在
- [ ] 有 `good first issue` 标签
- [ ] Issue/PR 模板已配置
- [ ] 回复 issue 平均 < 24h

### 生态集成

- [ ] 在相关工具/框架中提供集成示例
- [ ] README 展示"谁在用"
- [ ] 被 awesome list 收录

# project-interview-coach · 项目面试教练

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Cursor Skill](https://img.shields.io/badge/Cursor-Skill-1e1e2e)](https://docs.cursor.com/agent/skills)
[![Claude Compatible](https://img.shields.io/badge/Claude-Compatible-d97757)](https://docs.anthropic.com/en/docs/agents-and-tools/agent-skills/overview)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

> 把简历上的每个项目点，练到面试官挑不出毛病。一个会**追问、讲课、联网搜索**的 AI 面试教练 Skill。

一个基于 [Agent Skills](https://docs.anthropic.com/en/docs/agents-and-tools/agent-skills/overview) 标准的 Cursor / Claude Code 通用 Skill。接入后 AI 会以**一线大厂面试官视角**，把你简历上的项目从里到外拆成四层、追问到底，最后产出一份可直接背诵的 STAR 复盘文档。

## 它解决什么

- ❓ 项目是跟视频敲的 / 从 GitHub clone 的，自己都讲不清架构？
- ❓ "性能提升 80%" 这种数字被问"怎么测的"就卡壳？
- ❓ 选型理由只会说"业界最佳实践"，一问 trade-off 就露馅？
- ❓ 面试前一天发现八股文和项目细节完全串不起来？
- ❓ 项目懂一些但讲不出层次，STAR 写成流水账？

## 核心模型：四层洋葱（由内到外，面试权重由高到低）

```
┌─────────────────────────────────────┐
│ L4  外延层：八股文 / 通用理论        │  ← 最广，权重最低（点名不展开）
│    ┌──────────────────────────────┐ │
│    │ L3  评价层：指标 + 测量原理   │ │  ← 量化思维 + bad case
│    │   ┌────────────────────────┐ │ │
│    │   │ L2  实现层：怎么做     │ │ │  ← 架构 > 代码
│    │   │  ┌──────────────────┐  │ │ │
│    │   │  │ L1  核心：       │  │ │ │  ← 决定一切
│    │   │  │ 场景 + 选型      │  │ │ │
│    │   │  └──────────────────┘  │ │ │
│    │   └────────────────────────┘ │ │
│    └──────────────────────────────┘ │
└─────────────────────────────────────┘
```

## 三种工作模式（自动切换，不逼用户适应）

| 模式 | 适用人群 | 行为 |
|---|---|---|
| 🎯 **面试官模式** | 自己主导过项目 | 苏格拉底式追问 + poke hole 埋雷，逼出 trade-off |
| 📚 **教练讲解模式** | 跟教程敲 / 从 GitHub clone | 先系统讲解再问，让用户复述验证，全程不挫败 |
| 📝 **文档生成模式** | 亮点已问透 | 输出 STAR + Learnings 复盘卡片，每个数字可溯源 |

Phase 0 阶段会通过 4 个问题（项目来源、简历原话、想深挖的点、目标公司）自动诊断用户熟悉度并路由到合适的模式。

## 核心特性

- 🧭 **首轮熟悉度诊断**，5 档分级，跟视频敲 / 买的项目 / 自主开发都能服务
- 🎚️ **回答降级三档**，用户说"不知道"立即切讲解稿，连续触发自动进教练模式，绝不让用户挫败
- 🔍 **主动联网搜索**，涉及选型对比 / 指标原理 / 目标公司技术栈时自动调 `WebSearch`，不靠陈旧知识
- 📊 **指标四连发**，每个数字追问「分子分母 / 测量工具 / 手动复现方式 / bad case」，训练量化意识
- 🕳️ **8 种面试官陷阱埋点**，主动刺破「这是团队做的 / 没出过问题 / 业界最佳实践」等危险表达
- 📋 **STAR + PARL 模板**，强制 Result 量化、强制 Learning 反思、强制代码证据链接
- 🧩 **按领域的八股索引**（前端 / 后端 / 数据库 / 分布式 / 安全 / AI），L4 只点名不展开
- 🎤 **3 级讲述版本**（30 秒电梯 pitch / 3 分钟标准 / 10 分钟深挖），按面试官兴趣临场切换

## 快速开始

### 1. 安装

```bash
# macOS / Linux
git clone https://github.com/Erica-cod/interview_skills_for_project ~/.cursor/skills/project-interview-coach

# Windows (PowerShell)
git clone https://github.com/Erica-cod/interview_skills_for_project "$env:USERPROFILE/.cursor/skills/project-interview-coach"
```

### 2. 在 Cursor 中启用

Cursor 会自动发现 `~/.cursor/skills/` 下的 skill。无需额外配置。

### 3. 开始复盘

在 Cursor 里打开你要复盘的项目，对 Agent 说：

> 我要准备这个项目的面试复盘

或者任何包含这些关键词的表达："项目复盘 / 模拟面试 / 项目深挖 / 面试准备"。Skill 会自动触发。

### 4. 也可以用于 Claude Code / Claude.ai

本 skill 符合 [Agent Skills 标准](https://docs.anthropic.com/en/docs/agents-and-tools/agent-skills/overview)，可直接上传到 Claude.ai 的自定义 Skill 或放到 Claude Code 的 `.claude/skills/` 目录下使用。

## 使用示例

**用户**：我要准备字节前端一面，项目是基于 Modern.js 的 AI Agent。

**Skill**（Phase 0 诊断）：
> OK，先对齐几件事：① 你是从 0 规划的还是跟团队 / 教程做的？② 简历上这个项目写了几条原话？③ 最想被深挖的 2-3 个亮点？④ 目标公司 / 部门是？

**用户**：自己做的。想深挖 SSE 流式和多 Agent 协作。

**Skill**（自动搜索字节前端技术栈 + 最近面经，然后进入 L1）：
> 查了下字节 Web Infra 最近在推 Rspack + Modern.js，和你项目对口。我们从 SSE 开始：
>
> 1. 这个 SSE 解决的业务问题用一句话说是什么？
> 2. 项目预期**并发流数**峰值是多少？怎么算的？
> 3. 候选方案还有 WebSocket、长轮询、Fetch+打字机模拟，给我一张 3 列对比表，维度至少包含方向性、断连恢复、代理穿透、场景匹配。
>
> 先答这三个，答完我看情况追问。

——后续 4-6 轮追问走完 L1→L2→L3，用户说"出文档"后产出完整 STAR 卡片。

完整示例见 [`EXAMPLES.md`](EXAMPLES.md)。

## 仓库结构

```
project-interview-coach/
├── SKILL.md                  # 主入口：四层洋葱 / 三模式 / 工作流 / 六条铁律
├── INTERVIEW_PLAYBOOK.md     # 提问脚手架：按层级和领域 / 模糊表达拦截器 / 8 个陷阱 / 降级三档话术
├── DOCUMENT_TEMPLATE.md      # STAR+L 输出模板：单亮点卡片 + 项目面试手册
├── QUESTION_BANK.md          # 八股索引：前端 / 后端 / 数据库 / 分布式 / 安全 / AI
├── EXAMPLES.md               # 6 个完整示例（含模式 C 讲解 + 跨亮点追问 + 搜索嵌入）
├── LICENSE
└── README.md
```

## 适用场景

- ✅ 校招 / 社招前的项目深挖准备
- ✅ 简历项目润色（把"做了 X"改成"为了 Y 做了 X，达到 Z"）
- ✅ 模拟面试陪练
- ✅ 自查技术决策是否经得起推敲
- ✅ 读别人 / 开源项目时训练自己的工程品味

## 不适用场景

- ❌ LeetCode 算法面试准备（本 Skill 不涉及）
- ❌ 纯八股背诵（本 Skill 只做"点名指路"，背诵靠你自己）
- ❌ 完全没写过任何项目（建议先跟一个教程做完再来）

## 设计理念

面试项目深挖失败的 Top 1 原因不是"八股背得不够"，而是**没把自己做过的事真正想透**。

这个 Skill 的工作不是给你灌知识，而是逼你把"敲过"变成"理解"——
- 用面试官视角的追问，让你主动发现盲区
- 用量化四连发，让你养成"不允许自己说大概"的习惯
- 用联网搜索，让你的认知不停留在陈旧知识
- 用讲解兜底，让零基础也能被拉起来而不是劝退

## 路线图

- [ ] 支持多语言（英文版 SKILL / PLAYBOOK）
- [ ] 按岗位细分的提问模板（前端 / 后端 / 算法工程 / SRE）
- [ ] 集成主流面经社区爬虫（1point3acres / nowcoder）做更精准的公司搜索
- [ ] 产出 Anki 牌组（把每个亮点的 Poke Hole 自动转成 flashcard）

## 贡献

欢迎 PR：
- 补充 `QUESTION_BANK.md` 里的八股题目（务必标注必知 / 常问 / 可能问优先级）
- 补充 `INTERVIEW_PLAYBOOK.md` 里按领域的深度问题
- 分享你用这个 skill 的真实案例（欢迎做成 issue）

## 致谢

- [Anthropic Agent Skills](https://docs.anthropic.com/en/docs/agents-and-tools/agent-skills/overview) —— Skill 标准和 progressive disclosure 思想来源
- [awesome-cursor-skills](https://github.com/spencerpauly/awesome-cursor-skills) —— README 结构参考
- [EngineersOfAI](https://engineersofai.com/docs/break-into-ai/behavioral/Project-Deep-Dives) —— 项目深挖七维度评价模型
- 国内中文面经社区（牛客 / 一亩三分地 / 掘金） —— STAR 法则和量化指标的实践总结

## License

[MIT](LICENSE) © 2026 Erica-cod

---

> 如果这个 skill 帮你拿到了 offer，欢迎回来给个 star ⭐ 或开 issue 分享你的故事。

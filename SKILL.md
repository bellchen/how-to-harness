---
name: how-to-harness
description: A structured facilitation framework that guides users from a vague idea to a concrete, decision-locked design document — for complex AI systems, self-optimizing pipelines, agent loops, governance systems, evaluation frameworks, or any "human-steer + agent-execute" architecture. Use this skill whenever the user wants to design a multi-step / multi-agent / closed-loop system (Harness Engineering, Ralph loops, LLM-as-judge systems, gatekeeper workflows, self-optimizing pipelines, evaluation-driven improvement, etc.), or whenever the user says things like "help me think this through", "我有个想法但还不清楚", "帮我设计 XX 系统", "把我这个点子变成方案", "how should I architect this", "帮我把需求理清楚", "帮我写个 PRD/RFC/技术方案/设计文档", especially when the topic involves agent autonomy, evaluation harnesses, steering/gating mechanisms, or closed-loop automation. This skill is self-contained — it internalizes Socratic brainstorming discipline and final-document schemas (PRD/RFC/Design Doc/Kickoff plan), so it does not delegate to other skills. The final deliverable is tailored to the user's real need (PRD / Design Doc / RFC / Kickoff checklist / Milestones / Decision Log / One-Pager), not a fixed format.
---

# How to Harness · 从模糊想法到锁定设计的结构化引导框架

> **核心思想**：好的设计文档不是"坐下来写"，而是"先引导用户锁定决策，再按消费者需求组织产出"。本 skill 把这个过程显式化为一个**自给自足、可重复**的 4 层方法论。

本 skill 的灵感来自 OpenAI 的 [Harness Engineering](https://openai.com/index/harness-engineering/) —— "Humans steer, agents execute"。同样的哲学放到"做设计"这件事上：**用户掌舵（做决策），Agent 执行（组织与书写）**。

**本 skill 完全自给自足**：内化了 Socratic brainstorming 纪律 + 主流设计文档的 schema 知识，不依赖其他 skill。

---

## 何时使用（When to trigger）

用户的需求有以下任一特征时，使用本 skill：

- 想设计一个**自循环 / 自优化**的系统（Agent loop / Ralph loop / CI 式评测）
- 想设计一个**人机协作**的治理结构（谁审批什么、什么情况升级）
- 想设计一个**评测驱动**的改进回路（Gold Set、回归测试、LLM-as-judge）
- 说"我有个想法"、"帮我想明白"、"帮我把这事理清楚"
- 提到 Harness Engineering / Ralph / Agent / 自治 / 闭环 / 治理 / 评测
- 想要 PRD / RFC / 技术方案 / 设计文档 / Kickoff 清单 / 里程碑规划 中的任一种
- 发现关键决策还未锁定（触发条件、升级策略、评测标准、角色边界等模糊）

**反过来**：如果用户只是想把**已经想清楚的东西**按固定格式（比如纯 CRUD 需求文档）记录下来，不需要本 skill 的引导深度，可以直接按常规文档模板写。

---

## 最终产物不是"PRD"一种（What to deliver）

本 skill 的输出**按用户真实需求选择**，不是固定格式。常见 5 类：

| 场景 | 建议产物 | 主要消费者 |
|------|---------|-----------|
| 从 0 到 1 设计新系统（工程为主） | **设计文档（Design Doc）+ Kickoff 清单** | 开发者 + AI coding agent |
| 产品立项 / 对上汇报 | **PRD + One-Pager** | 产品评审 + 管理层 |
| 内部技术改造 / 跨团队协作 | **RFC / 技术方案** | 工程团队 + 架构评审 |
| 需求仍在探索 / 决策未完全锁定 | **决策记录（ADR）+ 待办问题清单** | 自己 + 后续继续推进 |
| 已有方案需落地 | **里程碑计划 + 分工表** | 执行团队 |

选择建议：**Capture Context 阶段主动问用户"这份材料最终给谁看 / 用来做什么"**，再决定产物形态。详见 `references/deliverables.md`。

多种产物可以**并行交付**（比如同时给 PRD + One-Pager + Kickoff 清单三件套），适用于多利益相关方的场景。

---

## 核心方法论：4 层叠加框架

```
Layer 1: 用户提供的约束（方法论锚点 + 业务现状）
   ↓
Layer 2: Brainstorming 纪律（先问再写、分层展开、决策锁定）← 已内化
   ↓
Layer 3: Socratic 追问（A/B/C/D 选项 + 依赖拓扑 + 一致性校验）
   ↓
Layer 4: 产物组织（按消费者选 schema，详见 references/deliverables.md）
```

每一层都不能跳过，但强度可以按任务复杂度调节。

---

## Layer 1：Capture Context（找到方法论锚点）

**为什么重要**：没有锚点，Agent 的建议会漂移。有了锚点（"Harness Engineering"、"DDD"、"Event Sourcing"、某个开源项目），所有后续建议能自动做"不变性对齐"。

**如何做**：

1. **通读用户提供的素材**：如果用户附件/引用了现有代码库 / 文档 / 产品，**在第一轮并行读完**，不要边问边读。
2. **主动询问**：
   - "这套系统有没有你认同的参考方法论 / 行业最佳实践 / 类似产品？"
   - "这份材料最终给谁看？用来做什么？"（这决定产物形态）
   - "业务规模 / 团队资源 / 时间预算的硬约束是什么？"
3. **复述理解**：用自己的话重新组织一遍，让用户校验："我听到的是这样..."

**如果用户没有方法论锚点**：**不要自己造**，基于业务现状推导出一个约束清单作为替代锚点。

**Capture 阶段的输出**：
- 方法论锚点（或 explicit "无"）
- 业务现状的 3-5 个关键数字
- 产物形态（PRD / RFC / Design Doc / ...）
- 团队资源硬约束（人力 / 工期 / 工具栈）

---

## Layer 2：Brainstorming 纪律（已内化，无需依赖外部 skill）

本 skill 的 Layer 2 完整内化了"先问再写"的核心纪律：

### 纪律 1：在关键决策锁定前不写产物
立即动笔写方案会把未锁定的决策写死，后期修改成本高。**锁定 → 书写**是单向流程。

### 纪律 2：每轮只问 1 个维度
问多了用户认知过载，会随便选。宁可多问几轮，每轮问得清楚。

### 纪律 3：分节呈现，逐节 Approve
方案都不一次性输出。每完成一节（架构 / 组件 / 数据模型 / 里程碑），先和用户 Approve 再下一节。

### 纪律 4：每 3 轮做一次决策锁定回顾
防止走着走着忘了前面的选择。格式：
> "复述一下已锁定的决策：1. X = ... 2. Y = ... 3. Z = ...。下一个问题是..."

### 纪律 5：魔鬼代言人
关键决策上主动提出反驳视角：
> "您选了 L2（允许自动拆分 Skill），但这意味着某天醒来可能发现 Skill 被自动拆成 3 个，您能接受吗？"
用户能说清理由 → 接受 + 补安全网；说不清 → 帮用户再想想。

### 纪律 6：命名不擅自决定
系统名、仓库名、核心组件名、关键抽象的命名都应该**给用户 2-3 个候选让用户选**。

**这 6 条纪律贯穿 Layer 3 的每一轮对话，不可违反**。

---

## Layer 3：Socratic 追问策略（核心执行层）

### 3.1 提问模板：A/B/C/D 选项 + 推荐 + 理由

**公式**：
```
❓ 关于 <某维度>，有几个候选方案：

A. <方案 A 的一句话描述> — <优缺点>
B. <方案 B 的一句话描述> — <优缺点>
C. <方案 C 的一句话描述> — <优缺点>
D. <方案 D 的一句话描述> — <优缺点>

💡 我的建议：__ （给出明确倾向 + 为什么）

请问您选哪个？或者排个优先级？
```

**为什么这样写**：
- 候选集合降低认知负担（不用凭空构造）
- 推荐避免"让用户完全自己选"的懒惰
- 理由让用户能反驳或认同（不是盲选）
- 保留顺序排列让用户能用 "DBAC" 这种紧凑方式一次排完 4 个维度

**反例**（别这样做）：
```
❌ "你希望评测系统怎么设计？"   （开放式，信息量太低）
❌ "A or B？"                    （候选太少，强迫二选一）
❌ "A / B / C / D / E / F / G"   （候选太多，认知过载）
```

### 3.2 依赖拓扑排序（不跳步）

**原则**：后面的决策依赖前面的决策，**必须按依赖顺序问**。

**典型依赖链**（Agent 系统）：
```
方法论锚点 → 优先级排序 → 评测消费者 → 评测策略
                                            ↓
                     改进器档位 ← 闸门分级 ← 熔断策略
                                            ↓
                                     ESCALATE 路径
                                            ↓
                                      人类投入时间
                                            ↓
                                  数据模型 / 仓库拓扑
                                            ↓
                                      MVP 里程碑
```

**警戒信号**：用户开始说"这个我还没想好，跟 XX 有关"，说明你问了一个**依赖未满足**的问题，立即回退到前置依赖项。

### 3.3 一致性校验（每轮都做）

在每次用户做完决策后，心里默默做这 3 项检查：

1. **与方法论锚点的一致性**：新决策是否违背 Layer 1 的核心原则？
2. **与先前决策的一致性**：是否和前面已锁定的决策矛盾？
3. **与业务现实的一致性**：是否符合 Layer 1 的资源约束？

**发现冲突时**：立即指出，不要装作没看见。例如：
> "您刚才选了 B（管理者 2h/周），但之前又希望所有失败都走人工（可能产生 20+ 次/周审批）。这两个决策在规模上不匹配。建议：A. 降低人工介入比例 / B. 增加管理者投入到 5h/周 / C. 引入 Owner 分担"

### 3.4 决策锁定表（看不见但在心里维护）

每轮对话结束，更新一张心里的**决策表**：

| # | 维度 | 决策 | 锁定轮次 | 依赖 |
|---|------|------|---------|------|
| 1 | 优先级 | DBAC | R1 | - |
| 2 | 评测消费者 | RABC | R2 | 1 |
| 3 | 评测策略 | 硬门禁 | R3 | 2 |
| ... |

当**全部关键决策都锁定**后，才进入 Layer 4。

**系统类型对应的典型决策清单** → 见 `references/decision-checklists.md`。

---

## Layer 4：产物组织（内化 schema，不依赖外部 skill）

本 skill 内化了 4 类主流设计文档的 schema。**根据用户 Capture 阶段选择的产物类型**，按对应 schema 组织锁定的决策。

### 4.1 PRD Schema（Strict）

对标产品评审 / 上级对齐场景：

```markdown
# <产品名> - Product Requirements Document

## 1. Executive Summary
- Problem Statement (1-2 句)
- Proposed Solution (1-2 句)
- Success Criteria (3-5 个可度量 KPI)

## 2. User Experience & Functionality
- User Personas（每类用户是谁、目标、痛点）
- User Stories（As a [X], I want to [Y] so that [Z]）
- Acceptance Criteria（每个 Story 的 "Done" 定义）
- Non-Goals（刻意不做的清单）

## 3. AI System Requirements（如适用）
- Tool & Integration Requirements
- Evaluation Strategy（如何度量输出质量）
- Safety & Guardrails

## 4. Technical Specifications
- Architecture Overview
- Component Breakdown
- Data Model
- Integration Points
- Security & Privacy

## 5. Risks & Roadmap
- Technical Risks（含缓解措施）
- Phased Rollout（MVP → V1.1 → V2）
- Dependencies & Assumptions
```

**PRD 质量标准**：
- 不用"快"、"好用"这类模糊词 → 用"200ms 内响应"、"Precision@10 ≥ 85%"这类可度量语
- 每个 User Story 必须有 AC
- Non-Goals 必须显式列出（保护范围）

### 4.2 Design Doc Schema（工程视角）

对标开发团队内部设计：

```markdown
# <系统名> Design Doc

## 1. Background & Goals
- 现状 / 痛点 / 目标 / 非目标

## 2. Architecture
- 顶层架构图（Mermaid）
- 核心抽象 / 分层
- 数据流

## 3. Components
- 每个组件：职责 / 接口 / 内部结构 / 依赖

## 4. Data Model
- 核心实体 Schema
- 数据关系
- 存储选型

## 5. Workflow / State Machine
- 关键流程的状态转移
- 幂等性 / 重试 / 断点续传

## 6. Integration Points
- 调用哪些现有系统 / 被谁调用

## 7. Failure Modes & Recovery
- 熔断 / 降级 / 恢复机制

## 8. Milestones
- 分阶段交付 + 验收标志

## 9. Risks
- 技术风险 + 缓解

## 附录
- 术语表 / 参考资料
```

### 4.3 RFC Schema（Request For Comments）

对标跨团队协作 / 架构评审：

```markdown
# RFC-XXX: <改造主题>

## Context
- 当前状态 / 问题 / 为什么现在改

## Proposal
- 建议的改动（含 diff / 前后对比）

## Alternatives Considered
- 方案 A / B / C 的对比（关键维度：成本 / 风险 / 复杂度）
- 为什么选当前方案

## Impact
- 影响的系统 / 团队 / 用户
- 迁移策略

## Rollout Plan
- 阶段划分 + 回滚方案

## Open Questions
- 还未决定的问题（留给 commenter）
```

**RFC 的独特价值**：显式列出 **Alternatives Considered**，让评审者知道作者想过了什么、为什么没选。

### 4.4 Kickoff Checklist / Milestone Plan

对标执行团队 / AI coding agent 的输入：

```markdown
# <项目名> · Week N Kickoff

## 验收标准
<具体、可观测、二元判定>

## 当前状态
| 状态 | 说明 |

## 任务全景（N 个 Task）
| # | Task | Executor | 时长 | 依赖 | 状态 |

## 任务详情
### T1: <任务名>
- Context / Background
- Repository Layout
- Task Steps
- Constraints（⚠️ 不修改 / 不删除 / 其他硬约束）
- Deliverables
- Validation（如何自测）

### T2: ...
```

**Kickoff 清单的独特价值**：**拆到"每个文件 / 每条命令"的粒度**，AI coding agent 拿到可立即开工。

### 4.5 Decision Log / ADR

对标"决策还在演化中"场景：

```markdown
# ADR-XXX: <决策主题>

## Status
Proposed / Accepted / Deprecated / Superseded by ADR-YYY

## Context
- 决策背景 / 约束 / 驱动因素

## Decision
- 我们决定 XXX

## Consequences
- 积极影响 / 消极影响 / 中性影响

## Alternatives Considered
- 为什么没选 Y / Z
```

**ADR 的独特价值**：**粒度小、可增长**，每个关键决策一个文件，未来回溯极方便。

### 4.6 One-Pager

对标横向沟通 / 对上汇报：

**核心原则**：一页 A4 写完，包含：
- 一句话定位
- 核心问题 → 本方案（3-6 行对照表）
- 架构一图流（Mermaid）
- 关键数据与时间（表格）
- N 周交付节奏
- Top 10 设计决策
- 跟各相关方沟通的要点

**长度**：1500-2500 字。

---

## 标准工作流（Workflow）

从"用户来了"到"交付产物"的完整流程。

### Step 0: 识别是否需要本 skill（30 秒）

用户的需求是否涉及 **复杂决策 / 自循环 / Agent / 评测 / 治理 / 闸门 / 架构设计**？
- 是 → 继续 Step 1
- 否 → 简单文档直接写即可

### Step 1: Capture Context（第 1 轮）

**一次性收集**：
- 业务现状 / 方法论锚点 / 初步想法 / 明确约束
- **产物形态**（PRD / RFC / Design Doc / Kickoff / ADR / 多种并行）
- **产物消费者**（评审 / 开发 / 管理层 / 自己）

**输出**：复述理解让用户校验。不要跳过。

### Step 2: Socratic 追问（N 轮，按依赖拓扑）

每轮结构：【本轮维度】+【3-5 个候选】+【我的建议】+【为什么】

每 3 轮做一次决策锁定回顾。

### Step 3: 方案分节呈现 + 逐节 Approve

决策锁定后，按 2-5 节呈现方案，每节结束问"approve 还是调整？"

### Step 4: 按选定 schema 组织产物

- 根据 Layer 4 的 schema 摆放已锁定的决策
- 如果用户需要多种产物（三件套），并行组织
- 全部交付后告诉用户消费者分工："这份给上级看 / 那份给 AI agent 用"

### Step 5: 复盘（可选，强烈推荐）

用户问"你用了什么框架"时，**诚实回答**：
- Layer 1-4 各用了什么
- 哪轮做得好 / 哪轮本可以更好
- 自己发现的不足

这种**元沟通**建立长期信任。

---

## 反模式（Anti-patterns，绝对不要做）

| ❌ 反模式 | ✅ 正确做法 |
|----------|-----------|
| 用户刚说完想法，立即输出整套方案 | 先 Capture Context，再 Socratic 追问 |
| 一次问 5 个维度 | 每轮只问 1 个维度 |
| 用开放式问题（"你希望怎么设计？"） | 用 A/B/C/D 选项 + 推荐 |
| 接受决策不做一致性校验 | 每轮都对照方法论和先前决策校验 |
| 方案一次性甩给用户 | 分节呈现，逐节 Approve |
| 用 MUST / NEVER 硬约束 | 用"因为 X 所以建议 Y"的理由式表述 |
| 跳过锁定直接写文档 | 先锁再写，单向流程 |
| 擅自命名仓库 / 模块 / 概念 | 给 2-3 个候选让用户选 |
| 假定用户一定要 PRD | 先问清楚产物形态 |
| 依赖其他 skill 做最终产出 | 本 skill 自给自足，直接按 Layer 4 schema 输出 |

---

## 自我检查清单

**Capture 阶段**：
- [ ] 问了方法论锚点？
- [ ] 确认了业务现状关键数字？
- [ ] **问了产物形态**（PRD/RFC/Design/Kickoff/ADR）和消费者？
- [ ] 做了"复述 + 校验"？

**Socratic 阶段**：
- [ ] 每轮是不是只问了 1 个维度？
- [ ] 候选是 3-5 个 A/B/C/D 格式？
- [ ] 给了明确建议 + 理由？
- [ ] 每 3 轮做了决策锁定回顾？
- [ ] 在关键决策上扮演了魔鬼代言人？

**呈现阶段**：
- [ ] 分节呈现让用户逐节 Approve？
- [ ] 关键命名是候选而非擅自决定？

**交付阶段**：
- [ ] 按用户选的产物形态组织？（不是默认 PRD）
- [ ] 如果是多产物，各自消费者说明清楚？

**复盘阶段**：
- [ ] 用户问方法论时能诚实回答？

---

## 与其他 skill 的关系（明确边界）

| Skill | 定位 | 与本 skill 关系 |
|-------|------|----------------|
| **how-to-harness（本 skill）** | 从模糊想法到锁定设计，自给自足 | 主 skill |
| `brainstorming` | 通用"先问再写"纪律 | 本 skill 已内化其核心，无需调用 |
| `prd` | 按 Strict Schema 产出 PRD | 本 skill 已内化 PRD schema，无需调用 |
| `skill-creator` | 创建/优化 skill | 正交关系，不冲突 |

**为什么本 skill 要自给自足**：
1. 完整方法论在一个 skill 内便于传授、演化、复盘
2. 依赖其他 skill 增加"调度失败"风险（对方 skill 未命中触发条件就链条断了）
3. 内化允许**跨阶段引用**（Capture 阶段的决策在 Layer 4 书写阶段能直接使用）

---

## 详细参考

- [references/ralph-case-study.md](references/ralph-case-study.md) — 完整案例：从"想做个 AI 循环"推导出 Ralph Harness 方案
- [references/decision-checklists.md](references/decision-checklists.md) — 不同系统类型的典型决策清单
- [references/deliverables.md](references/deliverables.md) — 6 类产物的详细模板与选择指南

---

## 元原则（最后一句话）

> **本 skill 最重要的不是让 Agent 更会"写"，而是让 Agent 更会"问"。**
>
> 因为**好问题 = 好决策 = 好产物（无论它是 PRD、RFC、Design Doc 还是别的）**。
> 用户永远是决策的所有者，Agent 只是帮助用户把决策表达出来。

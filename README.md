# How-to-Harness

> **从模糊想法到决策锁定的设计文档——一个结构化的"人类掌舵，Agent 执行"facilitation skill。**

`how-to-harness` 把"做设计"这件事显式化为一套**自给自足、可重复**的方法论：当用户带着一个模糊的想法走进来（复杂 AI 系统 / Agent loop / 评测闭环 / 治理系统 / 自优化流水线……），这个 skill 不会立刻输出方案，而是先用 Socratic 追问把**关键决策锁定下来**，再按**真实消费者**选择的 schema（PRD / RFC / Design Doc / Kickoff / ADR / One-Pager）把决策组织成交付物。

核心哲学来自 OpenAI 的 [Harness Engineering](https://openai.com/index/harness-engineering/)——**Humans steer, agents execute**。把这句话放到"做设计"这件事上就是：**用户掌舵（做决策），Agent 执行（组织与书写）**。

---

## 为什么需要这个 skill

绝大多数设计失败都不是"写得不好"，而是**决策还没锁定就开始写**：

- 方案写到一半才发现评测标准没定 → 推倒重来
- 文档交付后评审问"为什么不是方案 B" → 因为从没显式对比过
- 给 AI coding agent 的 Kickoff 清单粒度太粗 → 跑偏
- 一份 PRD 想同时服务管理层和开发团队 → 两边都不满意

`how-to-harness` 通过把**决策锁定**和**产物书写**显式分离，并强制决策按依赖拓扑顺序推进，解决上面这一整类问题。

---

## 何时触发

用户的需求有以下任一特征时，就该用这个 skill：

- 想设计一个**自循环 / 自优化**系统：Agent loop、Ralph loop、CI 式评测
- 想设计一个**人机协作治理**结构：谁审批什么、什么情况升级
- 想设计一个**评测驱动**的改进回路：Gold Set、回归测试、LLM-as-judge
- 说"我有个想法"、"帮我想明白"、"帮我把这事理清楚"
- 提到 Harness Engineering / Ralph / Agent / 自治 / 闭环 / 治理 / 评测
- 想要 PRD / RFC / 技术方案 / 设计文档 / Kickoff 清单 / 里程碑规划
- 发现关键决策还未锁定（触发条件、升级策略、评测标准、角色边界等模糊）

**什么时候不该用**：如果用户只是想把**已经想清楚的东西**按固定格式记录下来（比如纯 CRUD 需求文档），直接按常规模板写即可，不需要这套引导深度。

---

## 最终产物不是"PRD"一种

本 skill 的输出**按真实消费者选择**，不是固定格式：

| 场景 | 建议产物 | 主要消费者 |
|------|----------|-----------|
| 从 0 到 1 设计新系统（工程为主） | **Design Doc + Kickoff 清单** | 开发者 + AI coding agent |
| 产品立项 / 对上汇报 | **PRD + One-Pager** | 产品评审 + 管理层 |
| 内部技术改造 / 跨团队协作 | **RFC / 技术方案** | 工程团队 + 架构评审 |
| 需求仍在探索 / 决策未完全锁定 | **ADR + 待办问题清单** | 自己 + 后续推进 |
| 已有方案需落地 | **里程碑计划 + 分工表** | 执行团队 |

多种产物可以**并行交付**（例如 PRD + One-Pager + Kickoff 三件套，给不同受众看）。详细模板与选择决策树见 [`references/deliverables.md`](./references/deliverables.md)。

---

## 核心方法论：4 层叠加框架

```
Layer 1: Capture Context —— 方法论锚点 + 业务现状 + 产物消费者
   ↓
Layer 2: Brainstorming 纪律（已内化）—— 6 条硬纪律约束节奏
   ↓
Layer 3: Socratic 追问 —— A/B/C/D 候选 + 依赖拓扑 + 一致性校验
   ↓
Layer 4: 产物组织 —— 按消费者选 schema，把锁定的决策摆进去
```

每一层都不能跳，但强度可按任务复杂度调节。

### Layer 1 · Capture Context
一次性问清楚 4 件事：**方法论锚点**、**业务现状关键数字**、**产物形态**、**产物消费者**。然后**复述理解**让用户校验——花 30 秒避免一整轮歧义。

### Layer 2 · 6 条硬纪律（内化在 skill 内部）
1. 关键决策锁定前不写产物（锁定 → 书写，单向流程）
2. 每轮只问 1 个维度（避免认知过载）
3. 方案分节呈现，逐节 Approve
4. 每 3 轮做一次决策锁定回顾
5. 关键决策上扮演魔鬼代言人（主动提反驳视角）
6. 命名不擅自决定（系统名 / 仓库名 / 核心概念名都给候选让用户选）

### Layer 3 · Socratic 追问
标准提问公式：

```
❓ 关于 <某维度>，有几个候选方案：

A. <方案 A> — <优缺点>
B. <方案 B> — <优缺点>
C. <方案 C> — <优缺点>
D. <方案 D> — <优缺点>

💡 我的建议：__ （明确倾向 + 为什么）

请问您选哪个？或者排个优先级？
```

并且按**依赖拓扑顺序**问——后面的决策依赖前面的决策，警戒信号是用户开始说"这个我还没想好，跟 XX 有关"，说明你问了一个**依赖未满足**的问题，应立即回退到前置依赖项。

每轮用户做完决策后，心里做 3 项一致性校验：**对方法论锚点**、**对先前决策**、**对业务现实**。

### Layer 4 · 产物组织（4 + 2 个 schema）
决策全部锁定后，按用户选定的产物类型组织：**PRD / Design Doc / RFC / Kickoff Checklist / ADR / One-Pager**。完整 schema 见 [`SKILL.md`](./SKILL.md) 第 Layer 4 节与 [`references/deliverables.md`](./references/deliverables.md)。

---

## 标准工作流

```
Step 0  识别是否需要本 skill（30 秒）
   │
   ▼
Step 1  Capture Context（第 1 轮：现状 + 锚点 + 产物形态 + 消费者，复述校验）
   │
   ▼
Step 2  Socratic 追问（N 轮，按依赖拓扑，每 3 轮做一次决策锁定回顾）
   │
   ▼
Step 3  方案分节呈现（2–5 节，每节结束问 "approve 还是调整？"）
   │
   ▼
Step 4  按选定 schema 组织产物（多产物并行交付 + 说明各自消费者）
   │
   ▼
Step 5  复盘（可选，强烈推荐）—— 诚实回答"你用了什么框架"
```

---

## 仓库结构

```
how-to-harness/
├── SKILL.md                               # 完整 skill 规范——4 层框架 + 6 纪律 + 工作流 + 反模式
├── README.md                              # （本文件）面向人类的入口与总览
├── assets/                                # 预留：后续可放架构图、流程图等配图
└── references/
    ├── decision-checklists.md             # 按系统类型（Agent 循环 / 评测驱动 / 人机治理 / 普通产品）的决策清单
    ├── deliverables.md                    # 6 类产物（PRD / Design Doc / RFC / Kickoff / ADR / One-Pager）详细模板与选择决策树
    └── ralph-case-study.md                # 真实案例：从"想做个 AI 循环"到 Ralph Harness 方案的 9 轮推导过程
```

- **[`SKILL.md`](./SKILL.md)** — Canonical spec。AI agent 真正加载执行的文件。想用或想移植这个 skill 从这里入手。
- **[`references/decision-checklists.md`](./references/decision-checklists.md)** — Socratic 追问时**不遗漏关键维度**的清单。按 A/B/C/D 四种系统类型分块（AI Agent 自优化循环 / 评测驱动改进 / 人机协作治理 / 普通软件产品），加上成本、风险、命名 3 个通用维度。
- **[`references/deliverables.md`](./references/deliverables.md)** — 6 类产物的完整模板 + Capture 阶段的产物选择决策树。**这是 Layer 4 书写阶段的弹药库。**
- **[`references/ralph-case-study.md`](./references/ralph-case-study.md)** — 方法论落地的端到端案例：从用户一句"基于 Harness Engineering 给我的排障 AI Agent 做个自优化循环"开始，9 轮对话推出完整 Ralph Harness 方案。**最好的学习材料。**

---

## 反模式（绝对不要做）

| ❌ 反模式 | ✅ 正确做法 |
|----------|-----------|
| 用户刚说完想法，立即输出整套方案 | 先 Capture Context，再 Socratic 追问 |
| 一次问 5 个维度 | 每轮只问 1 个维度 |
| 用开放式问题（"你希望怎么设计？"） | 用 A/B/C/D 候选 + 推荐 + 理由 |
| 接受决策不做一致性校验 | 每轮都对照方法论和先前决策校验 |
| 方案一次性甩给用户 | 分节呈现，逐节 Approve |
| 用 MUST / NEVER 硬约束 | 用"因为 X 所以建议 Y"的理由式表述 |
| 跳过锁定直接写文档 | 先锁再写，单向流程 |
| 擅自命名仓库 / 模块 / 概念 | 给 2–3 个候选让用户选 |
| 假定用户一定要 PRD | 先问清楚产物形态 |
| 依赖其他 skill 做最终产出 | 本 skill 自给自足，直接按 Layer 4 schema 输出 |

---

## 自给自足原则（为什么不拆成多个 skill）

`how-to-harness` 内化了 Socratic brainstorming 纪律 + 4 类主流文档的 schema 知识，**不依赖其他 skill**。原因：

1. **完整方法论在一个 skill 内**便于传授、演化、复盘；
2. **避免调度失败风险**——依赖的外部 skill 未命中触发条件，整条链就断了；
3. **允许跨阶段引用**——Capture 阶段锁定的决策，Layer 4 书写阶段能直接使用，不丢上下文。

| Skill | 定位 | 关系 |
|-------|------|------|
| **how-to-harness（本 skill）** | 从模糊想法到锁定设计，自给自足 | 主 skill |
| `brainstorming` | 通用"先问再写"纪律 | 本 skill 已内化核心，无需调用 |
| `prd` | 按 Strict Schema 产出 PRD | 本 skill 已内化 PRD schema，无需调用 |
| `skill-creator` | 创建/优化 skill | 正交关系，不冲突 |

---

## 如何在 AI agent 中使用这个 skill

支持 skill 加载的平台（CodeBuddy / Claude skills 等）：

1. 把整个目录放到平台的 skills 文件夹下（例如 `.codebuddy/skills/how-to-harness/`）；
2. 当用户的请求匹配 skill 描述（"帮我设计 XX 系统"、"help me think this through"、提到 Harness / Ralph / Agent / 评测闭环等）时，agent 会自动加载 `SKILL.md`；
3. `references/` 下的文件**按需加载**——agent 只在当前对话真正需要决策清单、产物模板或参考案例时才读，让 `SKILL.md` 本身保持精简。

如果你是想自己当 facilitator：完整读一遍 `SKILL.md` 把 6 条纪律内化，把三份 reference 文件在对话时开在旁边随时查。

---

## 元原则

> **本 skill 最重要的不是让 Agent 更会"写"，而是让 Agent 更会"问"。**
>
> 因为 **好问题 = 好决策 = 好产物**（无论它最终是 PRD、RFC、Design Doc 还是别的）。
> 用户永远是决策的所有者，Agent 只是帮助用户把决策表达出来。

---

## License

除非单独文件另有说明，本仓库内容遵循 MIT License。详见仓库中的 `LICENSE`（若有）。

---

## Credits

由 [@bellchen](https://github.com/bellchen) 设计并维护。灵感来自 OpenAI 的 Harness Engineering 思想，融合了 Socratic 引导、依赖拓扑排序、决策一致性校验，以及主流设计文档体系（PRD / RFC / ADR / Design Doc），最终压缩成一套**可在真实对话里跑起来**的规则集。

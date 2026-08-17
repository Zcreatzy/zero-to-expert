<div align="center">

# Zero to Expert

**Turn an unfamiliar field into a concise, source-backed, highly visual HTML learning atlas.**

<a href="#中文"><kbd>中文</kbd></a>&nbsp;&nbsp;·&nbsp;&nbsp;<a href="#english"><kbd>English</kbd></a>

</div>

---

<a id="中文"></a>

## 中文

`zero-to-expert` 是一个基于开放 `SKILL.md` 格式的跨平台 Agent Skill，可用于 Codex、Claude Code、OpenCode、WorkBuddy 及其他兼容 Agent Skills 的工具。它帮助具有理工科本科基础、但对目标领域没有专业知识的读者，快速建立从入门到专家视角的完整认知地图。

它不会把搜索结果堆成一篇百科文章，而是先判断主题更偏向**学术研究**、**技术产业**还是**混合领域**，再围绕关键问题、因果机制、系统结构、重要争议、最新进展和专家判断方法，生成一份可独立阅读的单文件 HTML 图谱。

> “Zero to Expert” 指获得专家级的知识地图、词汇体系和判断框架，并不等同于替代长期的研究、工程或行业实践。

### 核心能力

- **自动选择分析框架**：区分学术、技术产业和混合主题，避免用同一套目录生搬硬套所有领域。
- **从问题树开始**：先找出真正支配一个领域的 8–18 个问题，再研究和组织答案。
- **循序渐进地建立能力**：按照 60 秒定位、10 分钟基础、30 分钟系统图、专家视角和行动路径逐层展开。
- **强调机制而非名词堆积**：解释概念之间如何连接、系统如何运行、瓶颈在哪里以及权衡为何存在。
- **证据驱动**：对最新动态、定量信息、争议和预测进行联网核验，并在内容附近提供编号引用。
- **明确区分证据状态**：用一致的视觉标签区分基础共识、当前状态、前沿、争议、推断和情景。
- **信息型可视化**：根据主题生成流程图、架构栈、时间线、比较矩阵、价值链、指标面板或案例拆解。
- **单文件交付**：输出自包含 `.html` 文件，CSS 和少量 JavaScript 均内联，无需构建步骤或外部字体。
- **可访问且响应式**：包含粘性目录、阅读进度、键盘焦点、移动端宽内容滚动提示和打印样式。
- **跟随提示词语言**：中文问题生成中文 HTML，英文问题生成英文 HTML；首次出现的关键术语可保留标准英文。

### Lite 与 Full

如果提示词没有指定模式，Skill 会在收到主题后、开始研究前询问你选择 **Lite（推荐）** 或 **Full**。

| | Lite | Full |
|---|---|---|
| 适合 | 快速建立可靠全景 | 复杂、争议大或跨学科主题 |
| 执行方式 | 单 Agent，一次限定研究 | 最多 3 个研究 Agent，多视角并行 |
| 核心问题 | 8–12 个 | 12–18 个 |
| 参考来源 | 约 8–14 个高质量来源 | 去重后约 18–28 个来源 |
| 主要章节 | 6–9 个 | 9–13 个 |
| 信息型图表 | 2–4 个 | 4–7 个 |
| 目标 | 更快、更紧凑 | 更广的交叉验证和跨视角综合 |

两种模式使用相同的引用、事实核验和质量标准。Lite 减少的是研究广度与输出体量，而不是证据要求。

### 两种主题框架

#### 学术框架

适用于理论、机制、研究方法、文献和开放问题占主导的主题，例如凝聚态物理、CRISPR 研究或因果推断。

重点覆盖：

- 研究对象、边界与核心问题
- 前置知识和概念依赖
- 第一性原理、模型、方程与适用边界
- 学派、范式和竞争性解释
- 研究方法、数据、基准、误差与复现
- 经典成果、关键转折和当前文献地图
- 前沿问题、争议以及专家识别弱证据的方法

#### 技术产业框架

适用于产品、工程栈、制造、供应链、企业、经济性和政策占主导的主题，例如芯片、动力电池或云计算产业。

重点覆盖：

- 客户需求、交付价值和产业边界
- 技术基础、架构栈、接口和瓶颈
- 研发、制造、良率、可靠性、部署与运维
- 产品、使用场景和性能—成本权衡
- 价值链、利润池、竞争格局和护城河
- 行业指标、周期、标准、监管与地缘约束
- 最新进展、情景推演以及专家判断供应商声明的方法

混合主题会选择其中一个作为主线，并嵌入另一框架中真正必要的模块。

### 兼容平台与安装

核心 Skill 不依赖 Codex 专有功能。`SKILL.md`、`references/` 和 `assets/` 可被兼容 Agent Skills 的工具直接使用；`agents/openai.yaml` 仅提供 Codex 的界面元数据，其他平台会忽略它。

| 平台 | 用户级安装位置或方式 | 调用方式 |
|---|---|---|
| Codex | `~/.codex/skills/zero-to-expert/` | `$zero-to-expert` 或自然语言自动触发 |
| Claude Code | `~/.claude/skills/zero-to-expert/` | `/zero-to-expert` 或自动触发 |
| OpenCode | `~/.config/opencode/skills/zero-to-expert/` | 自然语言触发或通过 Skill 工具加载 |
| WorkBuddy | 在“专家・技能・连接器”中导入本地 Skill 包 | 在对话中选择、召唤或自动触发 |

Lite 模式在所有平台都只使用当前 Agent。Full 模式会在平台提供多 Agent 能力时并行使用最多三个研究 Agent；如果平台没有该能力，则顺序执行相同的多视角研究分工。

选择你的平台目录执行安装：

```bash
# Codex
mkdir -p ~/.codex/skills
git clone https://github.com/Zcreatzy/zero-to-expert.git ~/.codex/skills/zero-to-expert

# Claude Code
mkdir -p ~/.claude/skills
git clone https://github.com/Zcreatzy/zero-to-expert.git ~/.claude/skills/zero-to-expert

# OpenCode
mkdir -p ~/.config/opencode/skills
git clone https://github.com/Zcreatzy/zero-to-expert.git ~/.config/opencode/skills/zero-to-expert
```

OpenCode 也兼容 `~/.claude/skills` 和 `~/.agents/skills`，因此可以与其他工具共享同一份安装。WorkBuddy 推荐通过技能管理界面导入本仓库目录或打包文件；支持工作区 Skill 的版本也可放入 `.codebuddy/skills/zero-to-expert/`。

更新时，在实际安装目录执行：

```bash
git -C <你的安装目录>/zero-to-expert pull
```

### 使用方法

最简提示词（示例使用 Codex 调用语法；其他平台可直接写“使用 zero-to-expert”）：

```text
用 $zero-to-expert 帮我了解芯片行业
```

直接指定快速模式：

```text
用 $zero-to-expert 的 Lite 模式，生成一份量子计算行业的中文 HTML 图谱。
```

指定深度、多视角研究：

```text
用 $zero-to-expert 的 Full 模式带我系统理解计算神经科学，重点关注研究范式、证据方法和近三年的前沿。
```

也可以在提示词中补充地区、时间范围、目标读者和希望重点回答的问题。若未提供，Skill 会做合理限定并在 HTML 顶部公开范围、分类置信度和证据截止日期。

### HTML 中会有什么

生成结果通常包括：

1. 主题定位、范围、路线分类、所选模式和证据截止日期
2. 60 秒总览与一张主视觉地图
3. 5–9 个高杠杆概念及容易混淆的区别
4. 核心机制、系统结构、技术栈或价值链
5. 关键历史转折及其解决的问题
6. 方法、产品、参与者、指标与权衡
7. 当前状态、最新进展、争议、瓶颈和前沿情景
8. 专家如何识别错误假设、指标游戏和过度宣传
9. “现在你能解释什么”、仍需实践的能力和带答案的自测
10. AI 辅助的 2 小时 / 2 天 / 7 天能力冲刺及分类来源库

### 设计原则

- **解释杠杆优先于覆盖面**：选择能解释大部分领域的少量概念，而不是追求百科式完整。
- **事实、推断和预测分开**：有日期的事实不与主观情景混写。
- **当前信息必须核验**：最新产品、市场、政策、标准和研究进展不能仅依赖模型记忆。
- **引用贴近论断**：重要的当前状态、数字、争议和预测必须有直接引用或明确标注的多来源推断。
- **图表必须帮助理解**：不生成纯装饰性插图，每张图都说明读者应该观察什么。
- **最终叙事集中完成**：Full 模式的子 Agent 用于发现和证据收集，主 Agent 统一范围、判断、引用和 HTML 设计。

### 项目结构

```text
zero-to-expert/
├── SKILL.md                              # 核心工作流与交付标准
├── agents/openai.yaml                    # 可选的 Codex 界面元数据
├── assets/html-blueprint.html            # 响应式 HTML 组件与样式参考
└── references/
    ├── modes.md                           # Lite / Full 预算和停止规则
    ├── frameworks.md                      # 学术、技术产业和混合框架
    ├── research-quality.md                # 证据、引用和研究质量规则
    └── multi-agent-orchestration.md       # Full 模式的并行研究协议
```

### 反馈与贡献

欢迎通过 [Issues](https://github.com/Zcreatzy/zero-to-expert/issues) 提交问题、真实使用案例、版式缺陷或框架建议。提交修改时，请确保 Skill 校验通过，并用一个实际主题检查生成 HTML 的桌面端、移动端、引用和横向溢出。

<p align="right"><a href="#zero-to-expert">返回顶部 ↑</a></p>

---

<a id="english"></a>

## English

`zero-to-expert` is a cross-platform Agent Skill built on the open `SKILL.md` format. It works with Codex, Claude Code, OpenCode, WorkBuddy, and other Agent Skills-compatible tools. It is designed for readers with a STEM bachelor's-level background who need a coherent map of an unfamiliar field without already knowing its specialist vocabulary.

Instead of assembling search results into an encyclopedia-like article, it first classifies the topic as **academic**, **technology–industry**, or **mixed**. It then builds a standalone visual HTML atlas around governing questions, causal mechanisms, system structure, major debates, current developments, and the judgment methods experts use.

> “Zero to Expert” means acquiring an expert-grade map, vocabulary, and evaluation framework. It does not replace years of research, engineering, commercial, or regulatory practice.

### What it does

- **Selects the right lens**: academic, technology–industry, or a deliberately composed mixed route.
- **Starts with a question tree**: identifies the 8–18 questions that govern the field before collecting evidence.
- **Builds capability progressively**: moves from a 60-second orientation to foundations, a system map, expert judgment, and an action path.
- **Explains mechanisms, not just terms**: shows how concepts connect, how the system behaves, where bottlenecks arise, and why tradeoffs exist.
- **Uses source-backed research**: verifies recent, quantitative, disputed, and predictive claims and cites them near their use.
- **Separates evidence states**: visually distinguishes foundations, current state, frontier, debate, inference, and scenarios.
- **Creates information-bearing visuals**: flows, architecture stacks, timelines, comparison matrices, value chains, metric panels, and worked examples.
- **Delivers one portable file**: produces a self-contained `.html` artifact with inline CSS and minimal JavaScript—no build step or external font required.
- **Is responsive and accessible**: includes sticky navigation, reading progress, keyboard focus, discoverable overflow, mobile layout, and print styles.
- **Matches the prompt language**: a Chinese prompt produces Chinese HTML; an English prompt produces English HTML. Standard English terminology may accompany first mentions when useful.

### Lite and Full modes

When the prompt does not name a mode, the Skill asks you to choose **Lite (recommended)** or **Full** after receiving the topic and before research begins.

| | Lite | Full |
|---|---|---|
| Best for | A fast, reliable field map | Complex, disputed, or cross-disciplinary topics |
| Execution | One agent, one bounded research pass | Up to 3 research agents in parallel perspective lanes |
| Governing questions | 8–12 | 12–18 |
| Sources | About 8–14 high-quality sources | About 18–28 unique sources after deduplication |
| Main sections | 6–9 | 9–13 |
| Information visuals | 2–4 | 4–7 |
| Goal | Faster and more compact | Broader triangulation and stronger cross-lens synthesis |

Both modes use the same citation, verification, and factual-quality standards. Lite reduces breadth and artifact size—not rigor.

### Topic frameworks

#### Academic route

For topics dominated by theories, mechanisms, methods, literature, and open research questions—for example condensed-matter physics, CRISPR research, or causal inference.

It emphasizes:

- the field's object, boundary, and central questions;
- prerequisite and concept dependencies;
- first principles, models, equations, and limits;
- paradigms and competing explanations;
- methods, data, benchmarks, uncertainty, and replication;
- canonical results, turning points, and the current literature map;
- open questions, disputes, and how experts identify weak evidence.

#### Technology–industry route

For topics dominated by products, engineering stacks, manufacturing, supply chains, companies, economics, and policy—for example semiconductors, EV batteries, or the cloud-computing industry.

It emphasizes:

- customer needs, delivered value, and industry boundaries;
- technical foundations, stacks, interfaces, and bottlenecks;
- R&D, manufacturing, yield, reliability, deployment, and operations;
- products, use cases, and performance–cost tradeoffs;
- value chains, profit pools, competition, and durable advantages;
- industry metrics, cycles, standards, regulation, and geopolitics;
- recent progress, scenarios, and how experts evaluate vendor claims.

A mixed topic uses one route as the narrative spine and inserts only the necessary modules from the other.

### Compatible platforms and installation

The core Skill does not depend on Codex-specific behavior. Compatible Agent Skills runtimes can use `SKILL.md`, `references/`, and `assets/` directly. `agents/openai.yaml` only supplies optional Codex UI metadata and can be ignored by other platforms.

| Platform | User-level location or method | Invocation |
|---|---|---|
| Codex | `~/.codex/skills/zero-to-expert/` | `$zero-to-expert` or automatic natural-language selection |
| Claude Code | `~/.claude/skills/zero-to-expert/` | `/zero-to-expert` or automatic selection |
| OpenCode | `~/.config/opencode/skills/zero-to-expert/` | Natural-language selection or the Skill tool |
| WorkBuddy | Import a local Skill package from Experts・Skills・Connectors | Select, invoke, or let WorkBuddy trigger it automatically |

Lite always uses the current agent only. In Full mode, the Skill uses up to three research agents when the runtime supports multi-agent execution; otherwise, it runs the same perspective lanes sequentially.

Clone the repository into the directory for your platform:

```bash
# Codex
mkdir -p ~/.codex/skills
git clone https://github.com/Zcreatzy/zero-to-expert.git ~/.codex/skills/zero-to-expert

# Claude Code
mkdir -p ~/.claude/skills
git clone https://github.com/Zcreatzy/zero-to-expert.git ~/.claude/skills/zero-to-expert

# OpenCode
mkdir -p ~/.config/opencode/skills
git clone https://github.com/Zcreatzy/zero-to-expert.git ~/.config/opencode/skills/zero-to-expert
```

OpenCode also discovers `~/.claude/skills` and `~/.agents/skills`, so one installation can be shared with another tool. For WorkBuddy, import this repository directory or a packaged copy through the Skill management UI. Editions that support workspace Skills can also use `.codebuddy/skills/zero-to-expert/`.

To update, run this command with the directory you actually installed into:

```bash
git -C <your-install-directory>/zero-to-expert pull
```

### Usage

Minimal prompt (shown with Codex invocation syntax; on another platform, simply say “use zero-to-expert”):

```text
Use $zero-to-expert to help me understand the semiconductor industry.
```

Choose the fast path directly:

```text
Use $zero-to-expert in Lite mode to create an English HTML atlas of the quantum-computing industry.
```

Request deeper multi-perspective research:

```text
Use $zero-to-expert in Full mode to teach me computational neuroscience, focusing on research paradigms, evidence methods, and the last three years of frontier work.
```

You can also specify geography, time horizon, audience, exclusions, or questions that the atlas must answer. If you do not, the Skill chooses a useful boundary and discloses its scope, classification confidence, and evidence cutoff date near the top of the HTML.

### What the HTML contains

A typical atlas includes:

1. Topic framing, scope, route classification, selected mode, and evidence cutoff
2. A 60-second orientation and one master visual
3. Five to nine high-leverage concepts and commonly confused distinctions
4. The core mechanism, system architecture, technical stack, or value chain
5. Historical turning points and the problems they resolved
6. Methods, products, participants, metrics, and tradeoffs
7. Current state, recent progress, disputes, bottlenecks, and frontier scenarios
8. How experts detect bad assumptions, metric gaming, and overclaiming
9. “What you can now explain,” remaining practice requirements, and a scored self-test
10. An AI-assisted 2-hour / 2-day / 7-day capability sprint and a categorized source library

### Design principles

- **Explanatory leverage over coverage**: choose the few concepts that explain most of the field instead of pursuing encyclopedic completeness.
- **Facts, inferences, and forecasts stay separate**: dated evidence is not blended with scenarios.
- **Current information is verified**: recent products, markets, policy, standards, and research are not taken from model memory alone.
- **Citations live near claims**: consequential current-state, quantitative, disputed, and predictive claims require direct citations or labeled multi-source inference.
- **Visuals must teach**: decorative imagery does not count; every visual states what the reader should notice.
- **Final synthesis stays centralized**: in Full mode, subagents collect questions and evidence while the main agent owns scope, judgment, citations, and HTML design.

### Repository structure

```text
zero-to-expert/
├── SKILL.md                              # Core workflow and delivery contract
├── agents/openai.yaml                    # Optional Codex UI metadata
├── assets/html-blueprint.html            # Responsive HTML component/style reference
└── references/
    ├── modes.md                           # Lite / Full budgets and stopping rules
    ├── frameworks.md                      # Academic, industry, and mixed frameworks
    ├── research-quality.md                # Evidence, citation, and research-quality rules
    └── multi-agent-orchestration.md       # Parallel research protocol for Full mode
```

### Feedback and contributions

Use [Issues](https://github.com/Zcreatzy/zero-to-expert/issues) for bugs, real-world examples, layout defects, or framework proposals. For changes, validate the Skill and test a generated HTML artifact for desktop/mobile layout, citations, and body-level horizontal overflow.

<p align="right"><a href="#zero-to-expert">Back to top ↑</a></p>

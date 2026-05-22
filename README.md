# 毕业论文 idea 打磨器

`thesis-idea` 是一个面向经济学毕业论文选题和早期研究设计的 Codex skill。它帮助研究生和研究初学者把模糊 idea、老师给的题目或初步研究直觉，转化为更可行的研究问题、数据路径、识别方案和论文蓝图。

# Thesis Idea Builder

`thesis-idea` is a Codex skill for economics thesis topic selection and early research design. It helps graduate students and early-stage researchers turn vague ideas, advisor-suggested topics, or first research intuitions into more feasible research questions, data paths, identification plans, and thesis blueprints.

## 不使用 AI Agent 时

如果你不使用 Codex skill 或其他 AI agent，也可以直接复制主目录里的 [`WEB_AI_PROMPT.md`](WEB_AI_PROMPT.md) 到网页版 AI 中使用。

网页版 AI 有上下文限制。更稳妥的做法是把这份 prompt 放进 AI 的背景、个性化设置、项目说明或 Custom instructions 中；如果平台不支持，就在每次开始新的 idea 打磨前粘贴一次。长对话后、隔了一段时间后、换窗口后，或模型输出开始偏离规则时，请重新上传或粘贴这份 prompt。

## Without An AI Agent

If you do not use the Codex skill or another AI agent, you can copy [`WEB_AI_PROMPT.md`](WEB_AI_PROMPT.md) from the repository root into a web AI chat and use it directly.

Web AI tools have context limits. A safer approach is to put this prompt into the AI tool's background, custom instructions, project instructions, or similar settings. If the platform does not support that, paste the prompt before starting a new idea-polishing session. After a long conversation, a long break, a new chat window, or when the model starts drifting from the rules, upload or paste the prompt again.

## 核心功能

- 面向经济学毕业论文选题和研究设计。
- 不生成空泛题目，而是诊断、压力测试和打磨 idea。
- 先过数据可行性门槛，再谈识别和论文蓝图。
- 输出红黄绿判定、行动决策、第一周验证、导师 memo、论文结构、主回归、变量、数据和图表安排。

## Core Features

- Serves economics thesis topic selection and research design.
- Does not generate empty topic lists; it diagnoses, pressure-tests, and polishes an idea.
- Checks data feasibility before discussing identification strategy or paper blueprint.
- Outputs feasibility colors, action decisions, first-week validation, advisor memo, paper structure, main regression, variables, data, tables, and figures.

## 工作流程

1. 先判断用户阶段、截止时间、数据权限、方法水平、导师偏好和目标层级。
2. 将模糊 idea 改写成一句可检验的经济学研究问题。
3. 执行经验研究数据门槛：相关文献、公开数据库、本地材料或授权渠道必须支持可信数据路径，经验 idea 才能获得 `green/proceed`。
4. 先寻找可用变异，再讨论 DID、IV、RDD、固定效应、shift-share 或其他方法。
5. 同时输出可行性判定和行动决策：`green/yellow/red` 加 `proceed/pivot/park/kill/upgrade/downgrade`。
6. 对可行或修复后的 idea，产出论文蓝图：章节功能、主回归或核心比较、变量、数据、表格、图形、第一周验证任务、导师 memo，以及升级或降级路径。

## Core Workflow

1. Classify the user's stage, deadline, data access, method level, advisor preference, and ambition level.
2. Rewrite the vague idea into a testable economics research question.
3. Apply the empirical data gate: prior literature, public databases, local materials, or authorized channels must support a credible data path before an empirical idea can receive `green/proceed`.
4. Search for usable variation before naming DID, IV, RDD, fixed effects, shift-share, or other methods.
5. Give both a feasibility verdict and an action decision: `green/yellow/red` plus `proceed/pivot/park/kill/upgrade/downgrade`.
6. For viable or repaired ideas, produce a thesis blueprint with section roles, main regression or comparison, variables, data, tables, figures, first-week validation tasks, advisor memo, and upgrade or downgrade paths.

## 数据可行性规则

对经验研究来说，题目有意思还不够。除非数据路径现实可行，否则这个 skill 不应把 idea 判定为可以推进。

可接受的数据路径包括：相关既有论文、公开数据库、用户已有本地材料、导师组或课题组权限、学院或图书馆权限、论文复现材料、数据管理方、合规第三方数据服务，或其他授权渠道。

对中国相关题目，英文中国研究和中文经济学或管理学期刊文章是重要数据先例。小红书、微信公众号、Xiaohongshu、WeChat public accounts 等平台只能用于搜索或发帖求助数据来源线索。平台回复只是线索，不是已经验证的数据。使用任何由此发现的数据前，必须核查来源、授权、隐私风险、引用规则、可复现性，以及能否合法、合规、合伦理地用于毕业论文。

## Data Feasibility Rule

For empirical ideas, intellectual excitement is not enough. The skill should not mark an idea ready unless the data path is realistic.

Acceptable data paths include relevant prior papers, public databases, user-owned local materials, advisor or research-team access, school or library access, replication archives, data owners, compliant third-party services, or other authorized channels.

For China-related topics, English-language China papers and Chinese economics or management journal articles are important data precedents. 小红书, 微信公众号, Xiaohongshu, WeChat public accounts, and similar platforms may be used only to search or ask for data-source leads. Platform replies are leads, not validated data. Before using any discovered dataset, verify provenance, authorization, privacy risk, citation rules, reproducibility, and legal or ethical fit for a thesis.

## 默认输出

对于单个 idea，默认输出包括：

- 一句话研究问题；
- 论文类型和用户模式；
- `green/yellow/red` 可行性判定和 `proceed/pivot/park/kill/upgrade/downgrade` 行动决策；
- 最小可行论文版本；
- 数据与变量表；
- 识别选项和主要威胁；
- 用户不能声称的内容；
- 第一周验证计划；
- 导师 memo；
- 包含论文结构、主回归、变量、数据、表格和图形的论文蓝图；
- 升级和降级路径。

## Output Contract

For a single idea, the default output includes:

- one-sentence research question;
- paper type and user mode;
- `green/yellow/red` feasibility and `proceed/pivot/park/kill/upgrade/downgrade` decision;
- minimum viable thesis version;
- data and variable map;
- identification options and threats;
- unsupported claims the user must not make;
- first-week validation plan;
- advisor memo;
- thesis blueprint with structure, main regression, variables, data, tables, and figures;
- upgrade and downgrade path.

## 安装

将这个仓库克隆到本地 Codex skills 目录：

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/juliaError/Econ-thesis-idea.git ~/.codex/skills/thesis-idea
```

安装后，重启或刷新 Codex，让 skill 列表重新加载。

## Install

Clone this repository into your local Codex skills directory:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/juliaError/Econ-thesis-idea.git ~/.codex/skills/thesis-idea
```

After installation, restart or refresh Codex so the skill list is reloaded.

## 使用

中文示例：

```text
用 thesis-idea 作为我的毕业论文 idea 打磨器。我有一个关于[主题]的经济学毕业论文 idea。请判断它是否可行，检查数据路径，压力测试识别思路，并把它整理成论文蓝图。
```

## Use

English example:

```text
Use thesis-idea as my Thesis Idea Builder. I have an economics thesis idea about [topic]. Please diagnose whether it is feasible, check the data path, pressure-test identification, and turn it into a thesis blueprint.
```

## 仓库结构

这个仓库只包含 `thesis-idea` standalone skill 和公开说明文件。

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── 01_modes_and_inputs.md
    ├── 02_verdict_rules.md
    ├── 03_data_feasibility.md
    ├── 04_identification_diagnostics.md
    ├── 05_output_templates.md
    └── 06_research_design_patterns.md
```

## Repository Structure

This repository contains only the standalone `thesis-idea` skill and public-facing documentation.

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── 01_modes_and_inputs.md
    ├── 02_verdict_rules.md
    ├── 03_data_feasibility.md
    ├── 04_identification_diagnostics.md
    ├── 05_output_templates.md
    └── 06_research_design_patterns.md
```

## 边界

这个 skill 用于研究设计辅助。它不能替代导师判断、文献综述、来源核查、数据权限检查、实证执行，或学生自己的学术责任。它不得编造论文、引用、政策、数据、系数、制度事实、变量或结果。

## Boundaries

This skill is for research design support. It does not replace advisor judgment, literature review, source verification, data access checks, empirical execution, or the student's own academic responsibility. It must not fabricate papers, citations, policies, data, coefficients, institutional facts, variables, or results.

## 许可

本仓库原创内容采用 Creative Commons Attribution-NonCommercial 4.0 International（CC BY-NC 4.0）许可。商业使用需要取得仓库维护者的单独书面许可。详情见 `LICENSE`。

## License

Original content in this repository is licensed under Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0). Commercial use requires separate written permission from the repository maintainer. See `LICENSE` for details.

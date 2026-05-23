# 毕业论文 idea 打磨器

`thesis-idea` 是一个面向经济学毕业论文选题和早期研究设计的 Codex skill。它用总控路由把原始兴趣、逐 idea / 逐轮五维评分、论文类型路由、IRIS-style 树搜索、文献拥挤度、三维题目搜选、数据/模型/测度可行性、识别诊断和论文蓝图串起来：先帮助研究生和研究初学者判断题目是否已经被中英文文献挤满；如果原题过于拥挤但兴趣仍有价值，再从原题的 X、Y、机制或反向因果中生发相邻方向，最后把仍有空间的 idea 转化为更可行的研究问题、数据路径、模型路径、识别方案或论文蓝图。

# Thesis Idea Builder

`thesis-idea` is a Codex skill for economics thesis topic selection and early research design. It uses a master router to connect raw-interest intake, per-idea and per-iteration five-dimensional scoring, paper-type routing, IRIS-style tree search, literature crowding, three-dimensional topic branching, data/model/measurement feasibility, identification diagnosis, and thesis blueprints. It first checks whether a topic is already crowded in Chinese and English literature; if the exact topic is saturated but the underlying interest is still useful, it branches from the original X, Y, mechanism, or reverse causal direction to find adjacent options, then turns viable ideas into research questions, data paths, model paths, identification plans, or thesis blueprints.

## 模型要求提示

AI 选题和研究设计对大模型的推理、知识组织、识别诊断和不确定性处理要求很高。建议优先使用当前最强的大模型：优先使用 GPT-5.5 Thinking 以上模型，以及 Claude 4.7 以上模型。DeepSeek 可以在中国大陆内部无法使用前两个模型时作为备选，但目前效果仍然不够好，尤其是在数据可行性、识别压力测试和论文蓝图细化上需要更谨慎地人工核查。

## Model Recommendation

AI-assisted topic selection and research design place high demands on a model's reasoning, knowledge organization, identification diagnostics, and uncertainty handling. Prefer the strongest available models: currently GPT-5.5 Thinking or above, and Claude 4.7 or above. DeepSeek can be used as a fallback when the first two model families are not accessible in mainland China, but its results are still not strong enough for this task; data feasibility, identification pressure-testing, and thesis-blueprint details require especially careful human checking.

## 不使用 AI Agent 时

如果你不使用 Codex skill 或其他 AI agent，也可以直接复制主目录里的 [`WEB_AI_PROMPT.md`](WEB_AI_PROMPT.md) 到网页版 AI 中使用。

网页版 AI 有上下文限制。更稳妥的做法是把这份 prompt 放进 AI 的背景、个性化设置、项目说明或 Custom instructions 中；如果平台不支持，就在每次开始新的 idea 打磨前粘贴一次。长对话后、隔了一段时间后、换窗口后，或模型输出开始偏离规则时，请重新上传或粘贴这份 prompt。

## Without An AI Agent

If you do not use the Codex skill or another AI agent, you can copy [`WEB_AI_PROMPT.md`](WEB_AI_PROMPT.md) from the repository root into a web AI chat and use it directly.

Web AI tools have context limits. A safer approach is to put this prompt into the AI tool's background, custom instructions, project instructions, or similar settings. If the platform does not support that, paste the prompt before starting a new idea-polishing session. After a long conversation, a long break, a new chat window, or when the model starts drifting from the rules, upload or paste the prompt again.

## 核心功能

- 面向经济学毕业论文选题和研究设计。
- 不生成空泛题目，而是诊断、压力测试和打磨 idea。
- 每个 idea、每个候选分支、每次 refinement 迭代都必须输出 novelty、clarity、feasibility、effectiveness、impact 五维评分、平均分、最弱项和下一步路由。
- 用总控路由管理原始兴趣、IRIS-style 多维评分、论文类型路由、MCTS/UCT 树搜索、文献拥挤度、候选题池、数据筛选、识别诊断、模型诊断和论文蓝图。
- 先判断论文类型：经验因果、测度/事实、理论、结构/量化、政策报告或混合类型；不把所有 idea 都压成实证回归。
- 每轮都必须给出“是否继续打磨”：建议继续打磨、建议冻结当前版本、可以推进也可继续升级，或建议暂停/更换路线。用户输出不显示内部状态代码。
- 对数字化、共同富裕等拥挤题目，先查中英文接近文献，必要时建议 `park/kill/pivot`。
- 对原题过于拥挤但兴趣仍有价值的情况，使用横向、纵向、逆向三维生发法寻找相邻方向。
- 通过文献拥挤度 gate 或三维生发后，保留候选题池，先冻结用户选中的候选题，再做数据/模型/测度路径、识别、变量、样本、模型、命题、主回归或表图精炼。
- 数据可得性验证拆分为 AI agent 能做的证据核查和用户必须确认的权限/下载/授权核查。
- 输出红黄绿判定、行动决策、第一周验证、导师 memo、论文结构、主回归或模型蓝图、变量/测度/命题/参数、数据和图表安排。

## Core Features

- Serves economics thesis topic selection and research design.
- Does not generate empty topic lists; it diagnoses, pressure-tests, and polishes an idea.
- Requires five-dimensional scores for every idea, candidate branch, and refinement iteration: novelty, clarity, feasibility, effectiveness, and impact, plus average score, weakest dimensions, and next route.
- Uses a master router to manage raw-interest intake, IRIS-style multi-dimensional scoring, paper-type routing, MCTS/UCT tree search, literature crowding, candidate banks, data screening, identification diagnosis, model diagnosis, and thesis blueprints.
- Routes ideas first as empirical causal, measurement/facts, theory, structural/quantitative, policy report, or mixed; it does not force every idea into an empirical regression.
- Every round must include a public stop-or-continue judgment: continue polishing, freeze the current version, proceed while optionally upgrading, or pause/change route. User-facing output must not show internal status codes.
- For crowded topics such as digitalization and common prosperity, checks close Chinese and English literature first and may recommend `park/kill/pivot`.
- If the exact topic is too crowded but the underlying interest is still useful, uses horizontal, vertical, and reverse branching to find adjacent directions.
- After the literature crowding gate or branch search, keeps a candidate bank and freezes the user's selected candidate before refining data/model/measurement paths, identification, variables, sample, model, propositions, main regression, tables, and figures.
- Splits data feasibility verification into agent-side evidence checks and user-side access, download, and authorization confirmation.
- Outputs feasibility colors, action decisions, first-week validation, advisor memo, paper structure, main regression or model blueprint, variables/measures/propositions/parameters, data, tables, and figures.

## 工作流程

1. 先用总控路由记录当前阶段、活跃候选题、备选候选题、阻塞风险和下一步模块。
2. 接受用户的原始兴趣、导师方向、政策、变量、现象或口语化直觉，保留原话并生成临时 idea card。
3. 对每个 idea、候选分支和迭代版本做五维评分：novelty、clarity、feasibility、effectiveness、impact，并根据最弱项决定下一步。
4. 当存在多个可能方向时，运行小规模 IRIS-style MCTS/UCT 树搜索：生成 research brief，先评分每个节点，再执行 review/refine/refresh/retrieve 等动作，记录 visits/value，并用文献、数据和识别 gate 调整 reward。
5. 判断用户阶段、截止时间、数据权限、方法水平、导师偏好和目标层级。
6. 对硕士生和拥挤题目先执行文献拥挤度 gate：查中英文接近文献，判断是否已有相同 X、Y、数据、方法和机制。
7. 若原题 `high/saturated` 但用户仍想保留部分兴趣，进入拥挤题目生发模块：横向拆 X/Y、纵向追机制链、逆向问“什么导致 X/Y”。
8. 对多个可行分支建立候选题池，让用户选择一个主线，同时保留其他方向作为备选。
9. 用户选中一个候选题后，冻结该分支，不再继续泛化生发。
10. 将选中候选题改写成一句可检验的经济学研究问题，并压成最小可行设计。
11. 按论文类型执行门槛：经验因果看数据与识别；测度/事实看概念、测量、覆盖与验证；理论看主体、约束、时序、均衡和命题；结构/量化看模型-数据映射、矩、估计/校准、拟合和反事实。
12. 对使用数据的 idea，区分 agent 证据核查和用户权限确认；先寻找可用变异、测度验证、理论机制或模型矩，再讨论 DID、IV、RDD、固定效应、结构估计、校准或仿真。
13. 同时输出可行性判定和行动决策：`green/yellow/red` 加 `proceed/pivot/park/kill/upgrade/downgrade`。
14. 在每轮结尾用自然语言给出“是否继续打磨”，判断是否必须继续、可以冻结、可选继续升级，或应该暂停/更换路线。
15. 对可行或修复后的 idea，产出类型匹配的论文蓝图：经验回归、测度事实、理论模型、结构/量化模型或混合设计。

## Core Workflow

1. Use the master router to track the current stage, active candidate, backup candidates, blocking risk, and next module.
2. Accept the user's raw interest, advisor direction, policy, variable, phenomenon, or colloquial intuition; preserve the wording and create a temporary idea card.
3. Score every idea, candidate branch, and iteration version on novelty, clarity, feasibility, effectiveness, and impact, then route by the weakest dimensions.
4. When several possible directions exist, run a small IRIS-style MCTS/UCT tree search: generate research briefs, score every node before advancing it, apply review/refine/refresh/retrieve actions, track visits/value, and use literature, data, and identification gates to adjust reward.
5. Classify the user's stage, deadline, data access, method level, advisor preference, and ambition level.
6. For master's students and crowded topics, run a literature crowding gate first: inspect close Chinese and English papers and check whether the same X, Y, data, method, and mechanism already exist.
7. If the original idea is `high/saturated` but the user wants to preserve part of the interest, run the crowded topic pivot lab: horizontal X/Y splitting, vertical mechanism-chain search, and reverse-causality search.
8. Build a candidate bank for viable branches, ask the user to choose one primary branch, and keep other directions as backups.
9. After the user selects one candidate, freeze that branch instead of continuing broad ideation.
10. Rewrite the selected candidate into a testable economics question and compress it into a minimum viable design.
11. Apply type-specific gates: empirical causal ideas need data and identification; measurement/facts ideas need concept, measurement, coverage, and validation; theory ideas need agents, constraints, timing, equilibrium, and propositions; structural/quantitative ideas need model-data mapping, moments, estimation/calibration, fit, and counterfactuals.
12. For data-using ideas, separate agent-side evidence checks from user-side access confirmation; search for usable variation, measurement validation, theory mechanism, or model moments before naming DID, IV, RDD, fixed effects, structural estimation, calibration, or simulation.
13. Give both a feasibility verdict and an action decision: `green/yellow/red` plus `proceed/pivot/park/kill/upgrade/downgrade`.
14. End each round with a natural-language stop-or-continue judgment: continue polishing, freeze the current version, proceed while optionally upgrading, or pause/change route.
15. For viable or repaired ideas, produce a type-matched thesis blueprint: empirical regression, measurement/facts, theory model, structural/quantitative model, or mixed design.

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
- 总控路由状态，以及每个 idea、候选分支和迭代版本的五维评分；
- IRIS-style idea tree：节点、动作、五维评分、visits、value、gate-adjusted reward、最佳分支和备选分支；
- 文献拥挤度 gate，特别是拥挤题目的 closest literature pattern 和答辩风险；
- 拥挤题目生发表：横向、纵向、逆向分支、数据路径、答辩风险和建议；
- 候选题池：主线、备选方向、返回条件；
- 选中题目精炼：冻结一个候选分支，压成经验、测度/事实、理论、结构/量化或混合类型的最小可行设计；
- 论文类型和用户模式；
- `green/yellow/red` 可行性判定和 `proceed/pivot/park/kill/upgrade/downgrade` 行动决策；
- 最小可行论文版本；
- 数据/模型/测度对象表，且区分 agent 证据核查和用户权限确认；
- 识别、测度、理论或结构/量化选项和主要威胁；
- 用户不能声称的内容；
- 第一周验证计划；
- 导师 memo；
- 包含论文结构、主回归或模型蓝图、变量/测度/命题/参数、数据、表格和图形的论文蓝图；
- 升级和降级路径。
- 是否继续打磨：建议继续打磨、建议冻结当前版本、可以推进也可继续升级，或建议暂停/更换路线。

## Output Contract

For a single idea, the default output includes:

- one-sentence research question;
- master-router state and five-dimensional scoring for every idea, candidate branch, and iteration version;
- IRIS-style idea tree with nodes, actions, five-dimensional scores, visits, value, gate-adjusted reward, best branch, and backup branches;
- literature crowding gate, especially the closest literature pattern and defense risk for crowded topics;
- crowded-topic pivot table with horizontal, vertical, and reverse branches, data paths, defense risks, and verdicts;
- candidate bank with the primary branch, backup branches, and return conditions;
- selected-topic refinement that freezes one candidate branch and compresses it into a type-specific minimum viable design;
- paper type and user mode;
- `green/yellow/red` feasibility and `proceed/pivot/park/kill/upgrade/downgrade` decision;
- minimum viable thesis version;
- data/model/measurement map that separates agent-side evidence checks from user-side access confirmation;
- identification, measurement, theory, or structural/quantitative options and threats;
- unsupported claims the user must not make;
- first-week validation plan;
- advisor memo;
- thesis blueprint with structure, main regression or model blueprint, variables/measures/propositions/parameters, data, tables, and figures;
- upgrade and downgrade path.
- a natural-language stop-or-continue judgment.

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
如果这个题目属于数字化、共同富裕、数字金融、绿色金融、ESG、智慧城市、低碳城市、高质量发展等拥挤方向，请先查中英文接近文献，判断是否已经做无可做；如果空间不足，请直接建议我换题、暂缓或大幅转向。
如果原题太拥挤但我仍想保留部分兴趣，请从原题的 X、Y、机制和反向因果出发，按横向、纵向、逆向三个维度生发相邻方向，并筛选哪些值得继续验证。
```

## Use

English example:

```text
Use thesis-idea as my Thesis Idea Builder. I have an economics thesis idea about [topic]. Please diagnose whether it is feasible, check the data path, pressure-test identification, and turn it into a thesis blueprint.
If this is a crowded topic such as digitalization, common prosperity, digital finance, green finance, ESG, smart cities, low-carbon cities, or high-quality development, first inspect close Chinese and English literature and tell me whether prior papers already exhaust the idea. If the remaining space is too thin, recommend that I change, park, or substantially pivot the topic.
If the exact topic is too crowded but I still want to preserve part of the interest, branch from the original X, Y, mechanisms, and reverse causal direction through horizontal, vertical, and reverse searches, then screen which adjacent directions deserve validation.
```

## 仓库结构

这个仓库只包含 `thesis-idea` standalone skill 和公开说明文件。

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── 00_master_router.md
    ├── 01_modes_and_inputs.md
    ├── 02_verdict_rules.md
    ├── 03_data_feasibility.md
    ├── 04_identification_diagnostics.md
    ├── 05_output_templates.md
    ├── 06_research_design_patterns.md
    ├── 07_literature_crowding_gate.md
    ├── 08_crowded_topic_pivot_lab.md
    ├── 09_selected_topic_refinement.md
    ├── 10_iris_ideation_loop.md
    └── 11_paper_type_gates.md
```

## Repository Structure

This repository contains only the standalone `thesis-idea` skill and public-facing documentation.

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── 00_master_router.md
    ├── 01_modes_and_inputs.md
    ├── 02_verdict_rules.md
    ├── 03_data_feasibility.md
    ├── 04_identification_diagnostics.md
    ├── 05_output_templates.md
    ├── 06_research_design_patterns.md
    ├── 07_literature_crowding_gate.md
    ├── 08_crowded_topic_pivot_lab.md
    ├── 09_selected_topic_refinement.md
    ├── 10_iris_ideation_loop.md
    └── 11_paper_type_gates.md
```

## 边界

这个 skill 用于研究设计辅助。它不能替代导师判断、文献综述、来源核查、数据权限检查、实证执行，或学生自己的学术责任。它不得编造论文、引用、政策、数据、系数、制度事实、变量或结果。

## Boundaries

This skill is for research design support. It does not replace advisor judgment, literature review, source verification, data access checks, empirical execution, or the student's own academic responsibility. It must not fabricate papers, citations, policies, data, coefficients, institutional facts, variables, or results.

## 灵感来源与引用

本项目的 IRIS-style idea tree 只是在抽象层面受 IRIS 论文启发：Garikaparthi, Aniketh, Manasi Patwardhan, Lovekesh Vig, and Arman Cohan. 2025. “IRIS: Interactive Research Ideation System for Accelerating Scientific Discovery.” ACL 2025 System Demonstrations. DOI: `10.18653/v1/2025.acl-demo.57`。

本项目没有包含 IRIS 的源码路径、源码映射、源码、prompt、UI、README 文案或运行说明；也不是 IRIS 的复刻版。本项目只借鉴“多维度评估、迭代 refinement、MCTS/UCT 分支探索”这些论文层面的公开方法思想，并将其重新设计为经济学毕业论文选题与研究设计流程。

## Inspiration And Citation

The IRIS-style idea tree in this project is inspired only at the abstract method level by: Garikaparthi, Aniketh, Manasi Patwardhan, Lovekesh Vig, and Arman Cohan. 2025. “IRIS: Interactive Research Ideation System for Accelerating Scientific Discovery.” ACL 2025 System Demonstrations. DOI: `10.18653/v1/2025.acl-demo.57`.

This project does not include IRIS source paths, source mappings, source code, prompts, UI, README wording, or setup instructions, and it is not a reimplementation of IRIS. It only adapts publicly described methodological ideas such as multi-dimensional evaluation, iterative refinement, and MCTS/UCT branch exploration into an economics thesis topic-selection and research-design workflow.

## 许可

本仓库原创内容采用 Creative Commons Attribution-NonCommercial 4.0 International（CC BY-NC 4.0）许可。商业使用需要取得仓库维护者的单独书面许可。详情见 `LICENSE`。

## License

Original content in this repository is licensed under Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0). Commercial use requires separate written permission from the repository maintainer. See `LICENSE` for details.

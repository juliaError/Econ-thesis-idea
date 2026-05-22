# 毕业论文 idea 打磨器 / Thesis Idea Builder

`thesis-idea` is a Codex skill for economics thesis topic selection and early research design. It helps graduate students and early-stage researchers turn vague ideas, advisor-suggested topics, or first research intuitions into more feasible research questions, data paths, identification plans, and thesis blueprints.

中文名：毕业论文 idea 打磨器

English name: Thesis Idea Builder

Technical slug: `thesis-idea`

## 核心卖点

- 面向经济学毕业论文选题和研究设计。
- 不生成空泛题目，而是诊断、压力测试和打磨 idea。
- 先过数据可行性门槛，再谈识别和论文蓝图。
- 输出红黄绿判定、行动决策、第一周验证、导师 memo、论文结构、主回归、变量、数据和图表安排。

## What It Does

- Serves economics thesis topic selection and research design.
- Does not generate empty topic lists; it diagnoses, pressure-tests, and polishes an idea.
- Checks data feasibility before discussing identification strategy or paper blueprint.
- Outputs feasibility colors, action decisions, first-week validation, advisor memo, paper structure, main regression, variables, data, tables, and figures.

## Core Workflow

1. Classify the user's stage, deadline, data access, method level, advisor preference, and ambition level.
2. Rewrite the vague idea into a testable economics research question.
3. Apply the empirical data gate: prior literature, public databases, local materials, or authorized channels must support a credible data path before an empirical idea can receive `green/proceed`.
4. Search for usable variation before naming DID, IV, RDD, fixed effects, shift-share, or other methods.
5. Give both a feasibility verdict and an action decision: `green/yellow/red` plus `proceed/pivot/park/kill/upgrade/downgrade`.
6. For viable or repaired ideas, produce a thesis blueprint with section roles, main regression or comparison, variables, data, tables, figures, first-week validation tasks, advisor memo, and upgrade or downgrade paths.

## Data Feasibility Rule

For empirical ideas, intellectual excitement is not enough. The skill should not mark an idea ready unless the data path is realistic.

Acceptable data paths include relevant prior papers, public databases, user-owned local materials, advisor or research-team access, school or library access, replication archives, data owners, compliant third-party services, or other authorized channels.

For China-related topics, English-language China papers and Chinese economics or management journal articles are important data precedents. 小红书, 微信公众号, Xiaohongshu, WeChat public accounts, and similar platforms may be used only to search or ask for data-source leads. Platform replies are leads, not validated data. Before using any discovered dataset, verify provenance, authorization, privacy risk, citation rules, reproducibility, and legal or ethical fit for a thesis.

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

## Install

Clone this repository into your local Codex skills directory:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/juliaError/Econ-thesis-idea.git ~/.codex/skills/thesis-idea
```

After installation, restart or refresh Codex so the skill list is reloaded.

## Use

Example prompt:

```text
Use thesis-idea as my Thesis Idea Builder. I have an economics thesis idea about [topic]. Please diagnose whether it is feasible, check the data path, pressure-test identification, and turn it into a thesis blueprint.
```

## Repository Structure

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

## Boundaries

This skill is for research design support. It does not replace advisor judgment, literature review, source verification, data access checks, empirical execution, or the student's own academic responsibility. It must not fabricate papers, citations, policies, data, coefficients, institutional facts, variables, or results.

## License

Original content in this repository is licensed under Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0). Commercial use requires separate written permission from the repository maintainer. See `LICENSE` for details.

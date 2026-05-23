# Output Templates

## Single Idea Diagnosis

```markdown
# Idea Diagnosis

## 0a. Router State
- Current stage:
- Active candidate:
- Backup candidates:
- Binding risk:
- Next route:

## 0b. Per-Idea And Per-Iteration IRIS Review
Required for every idea, every candidate branch, and every refinement iteration. If multiple branches are listed, score each branch separately before recommending or rejecting it.

| Criterion | Score | Feedback |
| --- | --- | --- |
| Novelty | /10 | Provisional until literature is checked. |
| Clarity | /10 | |
| Feasibility | /10 | |
| Effectiveness | /10 | |
| Impact | /10 | |

- Average score:
- Score change from previous iteration: improved / flat / worse / not available
- Weakest dimensions:
- MCTS status: run / skipped
- If skipped, why:
- Next route:

## 0c. IRIS-Style Idea Tree
Use this section only when tree exploration is used.

| Node | Parent | Action | Title | Scores | Visits | Value | Gate status | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| n0 | - | raw | | N/C/F/E/I | | | | root |
| n1 | n0 | generate / review_and_refine / refresh_idea / retrieve_and_refine | | | | | | active |

- Best branch:
- Backup branches:
- Weakest remaining dimensions:
- Next gate:

## 0d. Literature Crowding Gate
- Literature crowding: low / medium / high / saturated / not checked
- Closest literature pattern:
- Defense risk:
- Decision before focusing: proceed / pivot / park / kill / downgrade
- Why continue or stop:

## 0e. Candidate Bank
| ID | Candidate | Source | Status | Why keep or reject | Return if |
| --- | --- | --- | --- | --- | --- |
| c0 | original interest | raw input | active / rejected / parked | | |
| c1 | | horizontal / vertical / reverse / user feedback | primary / backup / rejected | | |
| c2 | | horizontal / vertical / reverse / user feedback | primary / backup / rejected | | |

## 1. One-Sentence Rewrite
[Turn the raw idea into a testable economics question.]

## 2. Paper Type And Mode
- Type: empirical causal / measurement-facts / theory / structural-quantitative / policy report / mixed
- Mode: thesis rescue / research-design strengthening / top-field or top-journal
- Why:

## 3. Feasibility Verdict
- Feasibility: green / yellow / red
- Decision: proceed / pivot / park / kill / upgrade / downgrade
- Binding constraint:

## 4. Minimum Viable Thesis Version
- Title:
- Core question:
- Type-specific minimum version:
- Empirical causal: sample, period, outcome, treatment/key variable, baseline method.
- Measurement/facts: concept, measurement rule, coverage, validation fact, main figures.
- Theory: agents, choices, constraints, timing, friction, equilibrium, proposition.
- Structural/quantitative: model block, data moments, estimation/calibration, fit, counterfactual.

## 5. Data / Model / Measurement Map
| Component | Object | Source or model role | Agent-side evidence | User-side confirmation | Difficulty | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| Outcome / fact / target moment | | | | | | |
| Treatment / key variable / primitive | | | | | | |
| Mechanism / parameter / friction | | | | | | |
| Controls / validation / benchmark | | | | | | |
| Unit / agent / state | | | | | | |
| Time / timing / horizon | | | | | | |

## 6. Design Options
| Route | Required object | Main assumption | Main threat | Feasibility |
| --- | --- | --- | --- | --- |
| Empirical causal | variation / comparison | | | |
| Measurement/facts | concept / measurement / validation | | | |
| Theory | primitives / equilibrium / proposition | | | |
| Structural/quantitative | moments / parameters / counterfactual | | | |
| Policy report | evidence / option / implementation | | | |

## 7. What Not To Claim
[Unsupported causal, mechanism, policy, novelty, or external-validity claims.]

## 8. Thesis Blueprint
- Section plan:
- Main regression, measurement design, model proposition, or structural block:
- Main table, figure, proposition, or counterfactual:
- Robustness, validation, comparative statics, sensitivity, or fit checks:
- Mechanism, heterogeneity, decomposition, extension, or policy exercise:
- Figures:
- Appendix:

## 9. First-Week Validation Plan
Day 1:
Day 2:
Day 3:
Day 4:
Day 5:
Day 6:
Day 7:

## 10. Advisor Memo
[200-300 Chinese characters or a concise English paragraph, depending on the user's language.]

## 11. Upgrade And Downgrade Path
- Thesis version:
- Excellent thesis version:
- Working paper version:
- Top-field/top-journal version:

## 12. 是否继续打磨
Required for every substantive output. The decision controls whether more iteration is needed or merely optional.

- 判断：建议继续打磨 / 建议冻结当前版本 / 可以推进，也可继续升级 / 建议暂停或更换路线
- 理由：
- 建议下一步：
- 如果需要用户选择，给出自然语言选项，例如继续打磨当前分支、换一个相邻方向、先查文献、先确认数据权限、按模型重写、从候选题池选择、暂停或放弃。
```

For crowded master's topics, output section 0 first and stop there if the idea is `high`/`saturated` and the student has no new data, setting, measurement, mechanism, or identification. Do not produce sections 4-11 unless the idea passes the crowding gate or the user explicitly chooses to proceed despite the risk.

If the original idea is `high`/`saturated` but the user wants nearby alternatives, output the pivot lab before sections 1-11:

```markdown
## 0b. Crowded Topic Pivot Lab

| Branch | Source from original topic | Dimension | Candidate question | Closest literature pattern | Data path | Main design | Defense risk | Verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| A | X-side / Y-side / mechanism / reverse-X / reverse-Y | horizontal / vertical / reverse | | | | | | proceed / verify / pivot / park / kill |

Recommended branch:
Backup branch:
Why not the others:
First verification task:
Do not claim yet:
```

Only continue to a full thesis blueprint for a branch with `proceed` or `verify`.

After the user selects one branch, update the candidate bank and mark non-selected viable branches as `backup`. If the selected branch fails the data or identification gate, return to the highest-quality backup rather than restarting from zero.

## Batch Screening Table

```markdown
# Idea Screening Table

| Rank | Candidate idea | One-sentence question | N/C/F/E/I score | Average | Data access | Identification | Advisor acceptance | Overall | Verdict |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | | | | | | | | | |
| 2 | | | | | | | | | |
| 3 | | | | | | | | | |

## Recommended Choice
[Pick the best fit for the user's deadline, data access, and ambition.]

## Why Not The Others
[State the binding risk for each rejected idea.]

## 是否继续打磨
[State in natural language whether to continue, freeze, optionally upgrade, or stop/change route; ask for a choice only when the user must choose among branches or continuation actions.]
```

## First-Week Validation Plan

Default plan:

- Day 1: find 5 closest Chinese and English papers and inspect data, identification, mechanism, and novelty claims.
- Day 2: confirm or download the core data source or metadata.
- Day 3: build rough treatment/key variable and outcome definitions.
- Day 4: plot treatment intensity, time trend, sample coverage, or basic distribution.
- Day 5: run a baseline descriptive relation or feasibility regression if data exist.
- Day 6: inspect the most fatal identification threat.
- Day 7: write an advisor memo with decision, data status, and next action.

Short deadlines can compress this to 3 days; long projects can expand it into two weeks.

## Advisor Memo

The memo should include:

- topic and one-sentence question;
- why the question matters;
- data path and current access status;
- identification or descriptive strategy;
- main risk;
- first validation result needed;
- requested advisor decision.

Avoid grand claims. The memo is for decision-making, not selling a finished paper.

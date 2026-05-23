# Selected Topic Refinement

Use this module after the user has chosen one candidate topic from the literature crowding gate or the crowded topic pivot lab. The goal is not to generate more topics. The goal is to turn the selected candidate into the smallest credible economics research design.

This module is called by `references/00_master_router.md`. It should freeze one selected candidate, refine that branch, and return gate statuses to the router. If the selected branch fails, return to the candidate bank rather than restarting broad topic search.

The selected candidate and each refined version must retain the five-dimensional score record: novelty, clarity, feasibility, effectiveness, and impact. When a refinement changes the idea, report the score change from the previous version and the next route.

## When To Trigger

Trigger this module when the user says things like:

- "就选这个方向";
- "把这个压成一个最小可行设计";
- "先不要继续找题，帮我把这个做成 paper";
- "把 n2 / branch 2 / 这个候选题继续 refine";
- "我想知道这个题能不能启动".

If the user has not selected a candidate yet, continue screening or ask them to choose one branch.

## Freeze The Candidate

Start by restating the chosen candidate:

```text
selected_candidate:
original_interest:
candidate_question:
setting:
claim_type: causal / descriptive / measurement / theory
known_data_path:
biggest_uncertainty:
```

Do not re-open broad ideation unless the data or identification gate fails.

Immediately after freezing the candidate, include:

```markdown
## Selected Branch IRIS Review
| Criterion | Score | Feedback |
| --- | --- | --- |
| Novelty | /10 | |
| Clarity | /10 | |
| Feasibility | /10 | |
| Effectiveness | /10 | |
| Impact | /10 | |

- Average score:
- Score change from previous iteration:
- Weakest dimensions:
- Next route:
```

## Refinement Sequence

1. **Question compression**: rewrite the idea as `Does X affect Y, through Z, in setting P, using variation V?` If the idea is descriptive, rewrite it as a measurement or fact question.
2. **Data availability gate**: verify outcome, treatment/key X, mechanism, controls, unit, period, and merge keys before choosing a method.
3. **Identification diagnosis**: name the usable variation and main identifying assumption before naming DID, IV, RDD, shift-share, event study, or fixed effects.
4. **Variable mapping**: define the dependent variable, treatment/key explanatory variable, mechanism variables, heterogeneity dimensions, controls, and labels.
5. **Sample construction**: define unit of observation, sample period, inclusion/exclusion rules, treatment timing, comparison group, and merge keys.
6. **Minimum viable model**: write the baseline comparison or regression in words first; formula only after the objects are clear.
7. **Table and figure plan**: decide which 3-5 tables/figures are necessary for the first version.
8. **Unsupported claims**: list causal, mechanism, policy, external-validity, and novelty claims the current design cannot yet support.
9. **Validation plan**: give 3-7 checks that can be done before committing to full data work.

## Required Tables

### Data And Variable Map

| Component | Variable | Candidate source | Unit | Years | Difficulty | Missing check |
| --- | --- | --- | --- | --- | --- | --- |
| Outcome |  |  |  |  |  |  |
| Treatment/key X |  |  |  |  |  |  |
| Mechanism |  |  |  |  |  |  |
| Controls |  |  |  |  |  |  |
| Merge keys |  |  |  |  |  |  |

### Identification Screen

| Design | Variation needed | Main assumption | Main threat | First validation |
| --- | --- | --- | --- | --- |
| DID/event study | policy timing or intensity | parallel trends / no anticipation | differential trends | pre-trend plot |
| IV | excluded source of X variation | relevance and exclusion | direct effect / weak IV | first stage and exclusion story |
| RDD | cutoff assignment | continuity near threshold | manipulation or sorting | density and balance checks |
| Shift-share | exposure times shock | shock exogeneity | endogenous exposure | pre-trend and leave-one-out checks |
| Panel FE | within-unit changes | no omitted time-varying confounder | reverse causality | placebo timing or lag structure |
| Descriptive facts | measurement variation | valid and stable measurement | composition shifts | sample audit and definitions |

## Minimum Viable Result Package

Prefer a small first version:

- Table 1: sample construction and descriptive statistics.
- Table 2: main effect or core descriptive fact.
- Table 3: robustness checks or alternative definitions.
- Table 4: mechanism or heterogeneity only if data support it.
- Figure 1: policy timeline, data distribution, map, event-study plot, or validation figure.

Avoid adding mechanism or heterogeneity tables before the outcome, key X, and main comparison are credible.

## Verdict

End with:

```text
data_gate: green / yellow / red
identification_gate: green / yellow / red
decision: proceed / refine / retrieve_sources / pivot / park
next_action:
```

Then give an iteration decision:

```text
iteration_status: continue_required / ready_to_freeze / optional_continue / stop_or_park
recommended_action:
optional_actions: review_and_refine / retrieve_and_refine / data_gate_refine / identification_refine / choose_backup / run_mcts / park / kill
user_choice_needed: yes / no
```

Only `green + green` should proceed directly to a full blueprint. Yellow requires validation. Red requires repair, downgrade, pivot, or park.

Return to `references/00_master_router.md` with: score state, data gate, identification gate, decision, next action, and whether to use a backup branch.

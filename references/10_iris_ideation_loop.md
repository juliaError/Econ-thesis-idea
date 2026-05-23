# IRIS-Style Ideation Loop

## Purpose

Use this module when a raw thesis interest needs more than a single review pass. It adapts the useful IRIS loop for economics thesis design:

```text
research goal -> brief -> review scores -> refinement actions -> idea tree -> best branch -> thesis gates
```

This is not a replacement for literature search, data access checks, identification diagnosis, advisor judgment, or empirical validation. It is a bounded exploration engine for candidate thesis directions.

## When To Use

Use this module when:

- the user's input is vague, broad, or only a personal interest;
- several plausible translations or branches exist;
- the topic is crowded and the pivot lab produces multiple nearby options;
- the user wants the AI to explore alternatives before choosing one;
- an initial branch fails and backup branches need systematic comparison.

Skip full tree search for a tiny one-off diagnosis, an urgent deadline with one obvious data path, or a case where the data or theory gate is already red.

## Brief Format

Each node should contain a compact research brief:

```markdown
# Title

## Core Question
One precise economics question.

## Proposed Design
Data, setting, comparison, model, or theory route.

## Why It Might Work
Economic intuition and why it fits the user's goal.

## Validation Plan
Literature, data, identification, measurement, or theory check.

## Main Risks
Data, identification, novelty, scope, execution, or advisor-defense risks.
```

Keep briefs useful for iteration. Do not polish them as final paper prose.

## Node State

Maintain a compact tree when using multi-round exploration:

```text
node_id | parent | action | depth | title | avg_score | visits | value | gate_status | status
```

Use short IDs:

- `n0`: user's raw interest or initial idea card;
- `n1`, `n2`, `n3`: generated or refined briefs;
- link each node to a candidate ID in the master candidate bank when it becomes viable.

Each node stores:

- `research_goal`;
- `current_brief`;
- `review_scores`;
- `review_feedback`;
- `retrieved_knowledge` if literature or data sources were checked;
- `gate_status`: crowding, data, and identification status if known;
- `depth`, `visits`, and `value`.

## Actions

Use these actions:

| Action | Use when | Output |
| --- | --- | --- |
| `generate` | starting from raw interest | first structured brief |
| `review_and_refine` | a node has weak scores but useful core | revised brief improving weakest 2-3 criteria |
| `refresh_idea` | the node is stale, crowded, or too narrow | substantially different branch preserving part of the original interest |
| `retrieve_and_refine` | literature/data grounding is needed | revised brief using inspected sources or clearly marked source tasks |
| `direct_feedback` | user chooses, rejects, or corrects a direction | child node incorporating user feedback |
| `data_gate_refine` | feasibility is weak | brief revised around obtainable data |
| `identification_refine` | effectiveness or causal credibility is weak | brief revised around usable variation or downgraded claim |

## Review Rubric

Score each node from 0 to 10:

| Criterion | Meaning |
| --- | --- |
| Novelty | Meaningfully different from obvious existing approaches; provisional until literature is checked |
| Clarity | Question, objects, mechanism, and setting are understandable |
| Feasibility | Data, model, or validation path can realistically be attempted |
| Effectiveness | Proposed design can answer the stated question |
| Impact | Result would matter for economics, policy, thesis defense, or the user's goal |

List the weakest 2-3 dimensions and choose the next action from them.

## Gate-Adjusted Reward

Use the IRIS average as the starting reward:

```text
iris_reward = average(novelty, clarity, feasibility, effectiveness, impact) / 10
```

Then adjust for thesis gates:

```text
reward = iris_reward
```

Apply caps when gate evidence is known:

| Gate result | Reward cap |
| --- | --- |
| Literature `saturated` and no new data/setting/measure/design | 0.35 |
| Data gate `red` for an empirical claim | 0.35 |
| Identification gate `red` for a causal claim | 0.45 |
| Theory gate `red` for a pure theory route | 0.35 |
| Major advisor-defense risk unresolved | 0.60 |

Yellow gates do not kill the node, but they should reduce confidence and set the next action to `retrieve_and_refine`, `data_gate_refine`, or `identification_refine`.

Never let a high IRIS score override a red thesis gate.

## Lightweight MCTS

Use MCTS only when exploring multiple branches. Keep it small by default: 2-5 iterations.

For each iteration:

1. **Select**: choose an unvisited child first. If all children are visited, choose the child with the highest UCT score.
2. **Evaluate**: score the node with the review rubric and gate-adjusted reward.
3. **Expand**: add child nodes using relevant actions, usually `review_and_refine`, `refresh_idea`, `data_gate_refine`, or `identification_refine`; add `retrieve_and_refine` when literature or data grounding is needed.
4. **Backpropagate**: increment visits and update value as a running average reward. Optionally discount parent rewards by `0.9`.
5. **Choose**: report the best current branch, backup branches, and the next recommended action.

UCT formula:

```text
UCT = value + c * sqrt(log(parent_visits + 1) / (child_visits + 1))
```

Use `c = 1.4` by default. Use a lower `c` when the user has a tight deadline and a higher `c` when exploration is the explicit goal.

## Output Template

```markdown
## IRIS-Style Idea Tree

| Node | Parent | Action | Title | Scores | Visits | Value | Gate status | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| n0 | - | raw | | N/C/F/E/I | | | | root |
| n1 | n0 | generate | | | | | | active |
| n2 | n1 | review_and_refine | | | | | | backup |

## Best Branch
- Selected node:
- Why this branch:
- Weakest remaining dimensions:
- Next gate:

## Backup Branches
- Backup 1:
- Backup 2:

## Do Not Claim Yet
- Novelty:
- Data:
- Causality:
- Mechanism:
```

After choosing the best branch, return to `references/00_master_router.md`. The selected branch must still pass the literature crowding, data feasibility, and identification gates before a full thesis blueprint.

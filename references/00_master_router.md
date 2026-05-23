# Master Router

## Purpose

Use this file as the total controller for multi-step `thesis-idea` work. It decides the current stage, what reference module to load next, which candidate branch is active, and when to stop, pivot, or return to a backup branch.

The router should keep the process ordered:

```text
raw interest -> ideation review -> IRIS tree when useful -> literature crowding gate -> pivot lab if needed -> user selection -> selected-topic refinement -> data and identification gates -> verdict -> thesis blueprint
```

## Routing Architecture

Use a star-shaped architecture:

- `00_master_router.md` owns stage order, candidate-bank state, and handoffs.
- Other reference files define local diagnostics and return a compact status.
- Do not build a mesh where every module routes to every other module.
- When a module finishes, return to the master router to decide the next step.

This keeps the skill from forgetting earlier gates or overloading the context window.

## Project State

Maintain a compact state table when the task spans more than one exchange:

```text
stage | active_candidate | selected? | crowding | data_gate | identification_gate | decision | next_route
```

Use short candidate IDs:

```text
c0 = user's raw interest
c1, c2, c3 = generated or refined candidate branches
```

Candidate records should contain:

- `raw_interest`: user's original wording;
- `academic_translation`: provisional research-language version;
- `source`: original / horizontal-X / horizontal-Y / vertical / reverse-X / reverse-Y / user feedback;
- `question`: one-sentence candidate question;
- `crowding`: low / medium / high / saturated / not checked;
- `data_gate`: green / yellow / red / not checked;
- `identification_gate`: green / yellow / red / not checked;
- `ideation_score`: average of novelty, clarity, feasibility, effectiveness, and impact when scored;
- `tree_node`: linked IRIS-style node ID if tree exploration is used;
- `visits` and `value`: lightweight MCTS state when relevant;
- `status`: active / backup / rejected / parked / killed;
- `next_action`: literature check, data check, user choice, refinement, pivot, blueprint, or stop.

## Stage 1: Raw Interest Intake

Accept rough inputs such as:

- personal interest;
- advisor direction;
- policy name;
- variable or index;
- observed phenomenon;
- vague sentence;
- several disconnected keywords.

First preserve the raw wording. Then create a provisional academic translation as an idea card:

```markdown
## Raw Interest Card
- Raw wording:
- Possible economic object:
- Possible X:
- Possible Y:
- Possible mechanism:
- Possible setting:
- Claim type: causal / descriptive / measurement / theory / unclear
- Missing key information:
```

Do not lock the final title at this stage. If the input is too vague, still produce the card and ask at most one high-impact question.

## Stage 2: Initial Ideation Review

Review the idea card before literature and data gates. Score from 0 to 10:

| Criterion | Question |
| --- | --- |
| Novelty | Is there a plausible margin beyond obvious existing work? Mark as provisional until literature is checked. |
| Clarity | Can the idea be stated as an object, relationship, or fact? |
| Feasibility | Is there a plausible path to data, model, or evidence? |
| Effectiveness | Would the design answer the user's intended question? |
| Impact | Would the answer matter for economics, policy, or thesis defense? |

Then list the weakest 2-3 dimensions and route:

| Weakest dimension | Next route |
| --- | --- |
| Clarity | refine the idea card, ask one question, or generate 2-3 candidate translations |
| Novelty | run `references/07_literature_crowding_gate.md` |
| Feasibility | run `references/03_data_feasibility.md` before blueprint |
| Effectiveness | run `references/04_identification_diagnostics.md` or downgrade claim |
| Impact | narrow the welfare object, mechanism, or setting before full design |

Do not claim true novelty without literature search.

## Stage 2b: IRIS-Style Tree Exploration

Route to `references/10_iris_ideation_loop.md` when the first review creates several plausible translations, the user wants exploration, the idea is broad, or the pivot lab produces multiple viable branches.

Use a small tree, not open-ended brainstorming:

- generate or refine research briefs;
- score each node on novelty, clarity, feasibility, effectiveness, and impact;
- use `generate`, `review_and_refine`, `refresh_idea`, `retrieve_and_refine`, `data_gate_refine`, `identification_refine`, or `direct_feedback`;
- run 2-5 MCTS/UCT iterations by default;
- track node visits and value;
- apply thesis-gate penalties when literature, data, identification, or theory gates are known.

Tree search is only a candidate-exploration method. After a best branch is chosen, return to the router and run literature, data, and identification gates before a thesis blueprint.

## Stage 3: Literature Crowding Gate

Route to `references/07_literature_crowding_gate.md` when:

- the user is in thesis rescue mode;
- the topic is a crowded China or applied-economics theme;
- the idea uses standard public data and standard panel FE/DID/mediation patterns;
- the initial ideation review suggests novelty is the binding risk.

If crowding is `low` or `medium`, continue to data and identification gates. If crowding is `high` or `saturated`, route to the pivot lab or recommend `park`/`kill`.

## Stage 4: Crowded Topic Pivot Lab

Route to `references/08_crowded_topic_pivot_lab.md` when the exact topic is crowded but the user's underlying interest is still worth preserving.

The pivot lab should generate branches from the original idea:

- horizontal from X;
- horizontal from Y;
- vertical through mechanisms;
- reverse from X adoption, diffusion, or capacity;
- reverse from Y as a cause of later behavior or policy response.

Screen each branch on literature crowding, data path, design, defense risk, and user fit. Put viable branches into the candidate bank.

## Stage 5: User Selection

When there are several viable branches, ask the user to choose one primary branch unless the best choice is obvious and low risk.

Keep other viable branches as backups:

```markdown
## Candidate Bank
| ID | Candidate | Why keep it | Current risk | Return if |
| --- | --- | --- | --- | --- |
| c1 | | primary | | |
| c2 | | backup | | c1 fails data gate |
| c3 | | backup | | c1 fails identification gate |
```

Do not refine every branch into a full blueprint. Refine only the selected branch.

## Stage 6: Selected-Topic Refinement

Route to `references/09_selected_topic_refinement.md` after the user chooses a branch.

Freeze the selected candidate. Convert it into:

- one-sentence research question;
- data and variable map;
- sample construction;
- identification or descriptive strategy;
- main regression or comparison;
- table and figure plan;
- unsupported claims;
- first validation tasks.

If data or identification becomes red, return to the candidate bank and test the next backup branch.

## Stage 7: Gates And Verdict

Use these gates before a full blueprint:

1. Data gate: `references/03_data_feasibility.md`.
2. Identification gate: `references/04_identification_diagnostics.md`.
3. Verdict rules: `references/02_verdict_rules.md`.
4. Research design patterns when useful: `references/06_research_design_patterns.md`.

Only move to a full thesis blueprint when the idea is green or repairable yellow. For red ideas, recommend pivot, park, kill, downgrade, or a strict theory route.

## Stage 8: Thesis Blueprint

Route to `references/05_output_templates.md` for:

- single idea diagnosis;
- batch screening;
- first-week validation plan;
- advisor memo;
- thesis blueprint.

The final blueprint should specify section roles, main regression or comparison, variables, data, tables, figures, unsupported claims, first-week validation tasks, advisor memo, and upgrade/downgrade paths.

## Router Output

At the end of each substantive exchange, include a compact routing state when useful:

```markdown
## Router State
- Current stage:
- Active candidate:
- Backup candidates:
- Binding risk:
- Next route:
```

Use this state to keep long conversations from drifting away from the skill.

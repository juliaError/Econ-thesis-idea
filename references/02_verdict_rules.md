# Verdict Rules

## Two-Layer Verdict

Always separate feasibility from decision.

- **Feasibility color**: `green / yellow / red`.
- **Decision**: `proceed / pivot / park / kill / upgrade / downgrade`.

Do not use a warm tone to hide a red verdict.

Candidate-branch tables may temporarily use `verify` or `refine` as workflow statuses, but the final recommendation must still map back to one of the six decisions above.

## Green

Use `green` when most conditions hold:

- the research question is clear in one sentence;
- the data path is credible;
- core variables are measurable;
- there is basic identification or a credible descriptive/factual strategy;
- the minimum version fits the user's deadline and skill level;
- positive, negative, and null results are interpretable;
- an advisor can understand the design.

Typical decision: `proceed`, sometimes `upgrade`.

## Yellow

Use `yellow` when the direction is promising but needs repair:

- topic is valuable but too broad;
- data may be obtainable but is unverified;
- identification exists but assumptions are strong;
- mechanism set is too large;
- outcome or treatment must be redefined;
- the thesis version is feasible but cannot support strong causal claims.

Typical decision: `pivot`, `downgrade`, or `park`.

## Red

Use `red` when current investment is not justified:

- key variable cannot be measured;
- data are unavailable or cleaning cost exceeds the deadline;
- the idea has broad concepts but no economics question;
- the closest literature already uses the same X, Y, data, unit, period, and method, and the student has no new data, setting, measurement, mechanism, or identification;
- identification is clearly endogenous and not repairable;
- sample is too small for the intended design;
- policy rollout is selected directly on the outcome;
- prior work already did the same thing and there is no new data, mechanism, setting, or measurement.

Typical decision: `kill` or `park`.

## Decision Definitions

| Decision | Meaning | Use when |
| --- | --- | --- |
| `proceed` | move forward | data, question, identification, and scope are basically feasible |
| `pivot` | change design but keep the useful core | mechanism matters but current data or identification fails |
| `park` | freeze for now | idea matters but data, evidence, or timing is not ready |
| `kill` | stop investing | core variable, data, or logic is not salvageable |
| `upgrade` | strengthen ambition | minimum version works and can add stronger mechanism, identification, or contribution |
| `downgrade` | lower ambition | high-end design fails but thesis version can work |

## Mode-Specific Mapping

- Thesis rescue: prefer feasible `proceed` or honest `downgrade`; avoid overbuilding.
- Research-design strengthening: use `pivot` aggressively when identification is weak.
- Top-field/top-journal: use `downgrade` when the project is feasible but lacks a sharp puzzle or generalizable insight.

## What To Say

For every verdict, include:

- one-sentence conclusion;
- the five-dimensional score state for the idea or branch being judged;
- the binding constraint;
- the smallest action that could change the verdict;
- what the user should stop assuming.

End with an iteration decision: `continue_required / ready_to_freeze / optional_continue / stop_or_park`. Ask the user to choose a next iteration action only when continuation is required or genuinely useful. If the current version is ready, recommend freezing it and moving to blueprint or first-week validation.

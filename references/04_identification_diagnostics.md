# Identification Diagnostics

## Usable Variation Search

Before naming a method, ask:

1. Is there a clear policy, shock, rule, constraint, exposure, or friction?
2. Is there variation across time, regions, cohorts, industries, firms, people, or thresholds?
3. Can treated and comparison units be defined?
4. Is treatment intensity meaningful?
5. Are there eligibility rules, boundaries, cutoffs, or staggered timing?
6. Can a first stage or behavioral response be shown?
7. Can pre-trends, placebo tests, or balance checks be visualized?
8. If not, should the project downgrade to measurement, facts, or descriptive evidence?

## Panel FE

Use only when:

- outcome and key variable vary within unit over time;
- fixed effects do not absorb the key variation;
- omitted shocks are at least partially addressable;
- the claim is framed cautiously if variation is not plausibly exogenous.

Risk: correlation is over-sold as causal evidence.

## DID And Event Study

Check:

- clear policy timing;
- treated and control groups;
- no obvious selected rollout directly driven by the outcome;
- enough pre-periods for trends;
- no major simultaneous policy confound;
- event-study/pretrend figure can be produced.

Do not say "use DID" unless these conditions are named.

## IV

Check:

- first stage has economics logic;
- exclusion restriction is plausible and attackable channels are named;
- weak-instrument risk is considered;
- first-stage figure or table is possible;
- monotonicity or interpretation is clear enough for the user's level.

If exclusion is mostly storytelling, do not recommend IV as the main design.

## RDD

Check:

- threshold genuinely determines treatment;
- running variable cannot be easily manipulated;
- enough observations near cutoff;
- covariates are continuous at cutoff;
- bandwidth sensitivity and graphical jump are feasible.

## Measurement And Facts

Use when causal identification is weak but the data can support a useful fact:

- new measure improves on old measure;
- new fact is stable and reproducible;
- figures can carry a clear empirical pattern;
- claims avoid causality unless justified;
- mechanisms are exploratory, not overclaimed.

## Theory

Use only when:

- there is a precise puzzle;
- agents, choices, constraints, timing, and friction can be stated;
- result is not simply assumed;
- propositions or comparative statics can be proved or reasoned through;
- the model differs from existing models;
- empirical or policy implications are clear.

## Policy Report

Use when the goal is not an academic causal paper:

- enough facts and data exist;
- evidence strength is clear;
- policy options are operational;
- trend, mechanism, and recommendation are separated;
- promotional cases do not replace evidence.

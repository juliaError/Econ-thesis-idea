# Data Feasibility

## Data Gate

For empirical projects, do not give `green/proceed` unless at least one credible data path exists:

- prior literature used closely related data;
- a public database contains the needed unit, years, and variables;
- local files or user materials show the data are available;
- an advisor group, library, research team, data owner, replication archive, compliant third-party service, or other authorized channel can provide access.

For China-related data, English-language China papers and Chinese economics or management journal articles are key evidence. 小红书, 微信公众号, Xiaohongshu, WeChat public accounts, and similar platforms can be used only to search or ask for data-source leads.

Informal platform replies are leads, not validated data. Before use, verify provenance, authorization, privacy risk, citation rules, reproducibility, and whether the data can be legally and ethically used in a thesis.

## Data Path Must Specify

An acceptable data path should name:

- source or paper precedent;
- unit of observation;
- time period;
- core variables;
- merge keys if multiple sources are needed;
- access status;
- likely cleaning burden.

If these are unknown, mark data status as `unverified`, not `pass`.

## Data And Variable Map

Use this structure in outputs:

| Component | Candidate variable | Data source | Difficulty | Notes |
| --- | --- | --- | --- | --- |
| Outcome | measurable result | paper/database/source | low/medium/high | unit and period |
| Treatment/key variable | policy, exposure, shock, or index | source | low/medium/high | variation source |
| Mechanism | channel proxy | source | low/medium/high | avoid outcome re-labeling |
| Controls | baseline covariates | source | low/medium/high | only useful controls |
| Unit | firm/county/person/etc. | source | low/medium/high | panel/cross-section |
| Time | year/month/day/etc. | source | low/medium/high | frequency match |

## Red Flags

- desired data are private, internal, expensive, confidential, or unavailable;
- outcome is conceptually attractive but not measurable;
- treatment exists only as a policy story without observable variation;
- merge requires identifiers that likely do not exist;
- data answer a different question from the user's idea;
- public data are too aggregated to support the proposed mechanism;
- cleaning burden exceeds the user's deadline or skill level.

## What Not To Claim

When data are weak, explicitly state what cannot be claimed:

- causal effects without credible variation;
- mechanism evidence without mechanism variables;
- micro behavior from aggregate data;
- policy evaluation without treated/control comparison or timing;
- novelty without literature checking;
- external validity beyond the sample.

## First Data Verification

The first data task should be concrete:

- find the closest paper and inspect its data section;
- open the public database and confirm variables, years, and unit;
- download a small sample or metadata file;
- check whether treatment and outcome vary over the needed dimension;
- draft a data-source paragraph for advisor review.

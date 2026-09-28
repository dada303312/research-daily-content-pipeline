# research-daily-content-pipeline

A Codex skill for a repeatable daily research-content operation:

- discover recent Q1 / CAS division-1 / flagship papers across multiple research domains;
- require a verifiable full text before writing;
- turn the paper into an evidence-grounded Chinese explainer;
- apply one consistent WeChat layout and brand signature;
- publish through the official-account workflow and record the result;
- report all `needs_pdf` candidates so the user can supply missing papers.

This repository contains the skill, its operating references, the canonical signature-bar asset, and a technical blog explaining the design.

## Install

Copy this directory into your Codex skills directory, then invoke it with:

```text
Use $research-daily-content-pipeline to run today’s literature-to-WeChat pipeline.
```

The default example is configured for three domains:

| Time (Asia/Shanghai) | Domain |
|---|---|
| 08:30 | 钝化土壤微生物 |
| 09:00 | Na 土壤生态 |
| 09:30 | 固体废物和生活垃圾碳排放 |

Adapt `references/fangcun-domains.md` when reusing the skill for another account or topic set.

## Design principles

1. **Candidate quality beats candidate volume.** Target 10–15 candidates per domain, but never lower the journal tier just to hit the number.
2. **Recency beats completeness.** Last 12 months first, then last 3 years, then 3–5 years for unusually relevant work.
3. **Full text is a gate, not a preference.** If no full text is available, mark the paper `needs_pdf` and ask the user for it. Do not write the formal article from an abstract alone.
4. **Evidence survives translation.** Preserve systems boundaries, units, CO2/CH4/N2O/CO2e/GWP wording, scenarios, statistics, and limitations.
5. **Brand is a component, not a per-article decision.** The signature bar and layout are fixed assets.

## Pages CMS

This repository includes a `.pages.yml` config. Open [app.pagescms.org](https://app.pagescms.org), sign in with GitHub, install the Pages CMS GitHub App on the `dada303312` account, and select this repository. The CMS will expose:

- `blog/` — editable blog posts;
- `docs/` — the unified research workflow document;
- `media/` — media storage.

## Files

```text
SKILL.md
agents/openai.yaml
references/fangcun-domains.md
references/workflow.md
references/quality-gates.md
assets/signature-bar.html
.pages.yml
docs/daily-workflow.md
blog/from-daily-account-to-codex-skill.md
```

## Publishing safety

The skill stops at administrator/operator scan verification and does not bypass platform safety checks. Default publishing behavior is no group notification; enable group notification only on explicit user request.

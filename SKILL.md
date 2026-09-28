---
name: research-daily-content-pipeline
description: "Run a repeatable daily research-content pipeline: discover recent Q1/top-journal papers across configured domains, require full-text verification, write evidence-grounded Chinese explainers, apply a consistent WeChat layout, publish through the official-account workflow, and record publication metadata. Use for daily literature monitoring, paper-to-WeChat drafting, multi-domain research updates, or turning an existing content operation into a reusable Codex skill. Do not use for one-off academic summaries that do not involve discovery, review, layout, or publishing."
---

# Research Daily Content Pipeline

Turn a recurring literature-monitoring operation into a deterministic, evidence-gated publishing workflow. The skill is optimized for a multi-domain account that publishes one high-quality paper explainer per domain per day.

## Operating contract

- Resolve the content workspace root before writing. Call it `CONTENT_ROOT`.
- Read `references/fangcun-domains.md` for the default three domains, schedules, output paths, journal whitelists, and topic boundaries. Adapt this file for another account or topic set.
- Read `references/workflow.md` before running the pipeline and `references/quality-gates.md` before drafting or publishing.
- Use the `gzh-design` skill for the “橄榄手记” WeChat layout when it is available.
- Use `assets/signature-bar.html` as the canonical signature bar. Copy it into the target project or use the project’s configured equivalent; never rewrite its wording, colors, spacing, radius, or internal structure.
- Publishing is an external side effect. Follow the authorization and verification rules in the project and in `references/quality-gates.md`.

## Hard gates

1. **Journal tier.** Only JCR Q1, Chinese Academy of Sciences division-1, or a domain-recognized flagship journal enters the main publishing pool. Lower-tier papers may be background sources only.
2. **Recency.** Prefer the last 12 months, including online-first and advance-access papers; then the last 3 years; then 3–5 years for unusually relevant work. Older papers are background or classics, not the routine daily selection.
3. **Full text.** The main article must be grounded in a verifiable full text. Prefer a Zotero PDF, then a legitimate publisher OA or institutional-access copy. If full text is unavailable, mark the candidate `needs_pdf`, report the exact reason, and ask the user to supply the paper. Never write the formal article from an abstract alone.
4. **Evidence.** Preserve system boundaries, functional units, CO2/CH4/N2O/CO2e/GWP wording, sample sizes, scales, statistics, scenarios, and limitations. Do not turn correlation into causation.
5. **Format.** Use the configured theme, original figure/table objects from the PDF, a square paper-information card, both 2.35:1 and 1:1 cover checks, the canonical signature bar, and the standard closing block.
6. **Publishing.** Default to no group notification. Stop and preserve the page when WeChat requires administrator or operator scan verification. Do not bypass safety checks or CAPTCHAs.

## Run sequence

1. **Configure.** Load the domain config and progress file. Set candidate target, cut-off date, journal whitelist, output path, and current queue.
2. **Discover.** Search systematically across the configured sources. Target 10–15 new or updated candidates per domain; include a dedicated scan of the last 12 months. Deduplicate by DOI, title, Zotero item key, historical drafts, and publication records.
3. **Record.** Write title, authors, year, journal, volume/issue/pages, DOI, abstract, tags, and status to Zotero and the domain progress file. Use statuses such as `queued`, `needs_pdf`, `drafted`, `reviewed`, `published`, and `skipped`.
4. **Select.** Pick one queued paper with a verifiable full text. If the best candidates lack full text, report that fact and either choose another full-text candidate or pause the main article for that domain.
5. **Extract.** Read the full text, identify the central claim and evidence chain, and extract figures/tables from the original PDF objects. Do not redraw or alter data.
6. **Draft and review.** Write the Chinese explainer in the fixed structure, then run the review gate before layout. Keep the title format “journal｜Chinese core finding”.
7. **Layout and validate.** Build the WeChat section HTML, insert the canonical signature bar, validate the HTML, and generate a local preview. Check images, captions, card bounds, title wrapping, and cover crops.
8. **Publish and record.** Create or update the official-account draft, fill the title, author, digest, cover, and body, submit publication under the configured authorization model, then record the draft ID, appmsg ID, public URL, status, preview path, and Zotero keys. Add any `needs_pdf` items to the daily report.

## Output contract

Use an independent directory per article:

```text
CONTENT_ROOT/output/<domain>/YYYY-MM-DD-journal-topic/
|-- article.md
|-- article-illustrated.md
|-- brief.yaml
|-- claims.yaml
|-- sources.yaml
|-- draft.md
|-- review-report.json
|-- figures/
|-- gzh/
```

Keep the domain-level `library-progress.md` current. A run is not complete until the publication metadata and the next candidate queue are recorded.

## References

- `references/fangcun-domains.md`: default domains, schedules, keywords, journal whitelists, and paths.
- `references/workflow.md`: full phase-by-phase operating procedure.
- `references/quality-gates.md`: candidate, full-text, evidence, writing, layout, and publishing checks.
- `assets/signature-bar.html`: canonical brand signature bar.

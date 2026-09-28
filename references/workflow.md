# Full operating workflow

## 1. Load and configure

1. Locate `CONTENT_ROOT`, the domain progress file, the current queue, and the previous publication record.
2. Read the domain configuration and the journal whitelist.
3. Determine the date window. Always run a dedicated “last 12 months” scan before falling back to older literature.
4. Prepare the candidate table with fields: title, authors, year, journal, DOI, source, OA status, full-text status, topic match, recency, and status.

## 2. Discover candidates

- Run systematic searches for the domain, then run a narrow “newest first” search.
- Target 10–15 candidates. If fewer than 10 pass the tier and relevance gates, record the search queries and explain the shortfall.
- Check Crossref/OpenAlex metadata and the publisher record.
- Prefer online-first/advance-access papers when their metadata and full text are verifiable.
- Record candidates in Zotero with tags for domain, month, daily queue, journal tier, and status.
- Deduplicate before selection. Mark already written or published items as `done`/excluded.

## 3. Select the main paper

Selection order:

1. queued item with a verified PDF;
2. newest online-first paper with legitimate full-text access;
3. recent Q1/division-1 paper with strong relevance;
4. older paper only when it is necessary background/classic and the user explicitly approves it.

If no candidate has full text:

- mark the best candidates `needs_pdf`;
- list title, journal, year, DOI, and the retrieval failure reason in the daily report;
- do not publish an abstract-only article;
- use another full-text candidate if one exists, otherwise pause the domain’s main article.

## 4. Full-text and evidence extraction

- Read the complete paper, not only the abstract.
- Identify the research question, system boundary, data, methods, main results, counterfactual/scenario assumptions, and limitations.
- Extract figures/tables from the original PDF image objects. Preserve labels and data.
- Build a claim list with evidence anchors. Separate measured values, modeled estimates, and scenario outputs.
- For carbon papers, distinguish CO2, CH4, N2O, CO2e, GWP-100, direct emissions, downstream emissions, and avoided emissions.

## 5. Draft the Chinese explainer

Use the fixed structure:

```text
文章来源
研究简介
主要图文
关键数据
研究结论与边界
论文引用
```

Title format: `journal｜Chinese core finding`.

Keep high information density. Preserve units, sample sizes, spatial/temporal scale, mechanisms, and limitations. Avoid generic transitions and unsupported causal language.

## 6. Review gate

Before layout, check:

- journal tier and publication date;
- DOI and bibliographic fields;
- full-text availability and source;
- every numeric claim against the paper;
- figure/table captions and order;
- boundary language for models, scenarios, and estimates;
- title, lead, section logic, and conclusion;
- no duplicated claim, no filler, no overstatement.

If the review fails, revise or choose another paper. Do not move a failed draft into layout.

## 7. Layout and preview

- Use the `gzh-design` “橄榄手记” theme.
- Generate the paper-information card, a wide cover, and a 1:1 crop check.
- Extract original figure/table images into the article directory.
- Insert the canonical signature bar from `assets/signature-bar.html` without modification.
- Validate the generated HTML and generate the preview page.
- Check mobile rendering: image loading, title wrapping, card bounds, table overflow, captions, and closing block.

## 8. Publish and record

- Create the official-account draft.
- Fill title, author/byline, digest, cover, body, and image captions.
- Default to no group notification and the “show on account homepage / allow recommendation” publishing path.
- If scan verification appears, stop, preserve the tab, and ask the user to scan. Do not bypass verification.
- After submission, record the draft ID, appmsg ID, public URL, status, preview path, Zotero item/attachment keys, and any blockers.
- Report `needs_pdf` candidates in the same run summary.

# Quality gates

## Candidate gate

- Journal is JCR Q1, CAS division-1, or a domain-recognized flagship.
- Publication date passes the recency priority.
- Topic is inside the configured domain boundary.
- DOI, title, authors, year, journal, and abstract are verifiable.
- Candidate is not a duplicate of an existing draft or published article.

## Full-text gate

- The main paper has a complete, verifiable full text.
- Zotero PDF is preferred; otherwise use legitimate OA, institutional access, or a lawful author-shared copy.
- If full text is unavailable, mark `needs_pdf`, report it, and ask the user to collect it.
- Abstract-only writing is not allowed for the formal article.

## Evidence gate

- Every numeric claim has a source anchor in the paper.
- The article states the system boundary, functional unit, time range, geography, and scenario assumptions when relevant.
- CO2, CH4, N2O, CO2e, GWP, direct emissions, downstream emissions, and avoided emissions are not conflated.
- Measured values, modeled values, and scenario outputs are labeled correctly.
- Correlation is not written as causation.

## Writing gate

- Main title follows `journal｜Chinese core finding`.
- Body follows the standard six-part structure.
- The lead states the paper’s actual contribution, not a generic topic sentence.
- Figures and tables are explained near their relevant claims.
- Boundaries and limitations are explicit.
- No filler, no repeated claims, no unsupported policy recommendations.

## Layout gate

- One consistent theme across all domains.
- Original PDF figure/table objects are used without redrawing or data alteration.
- Paper-information card has safe margins and no text overflow.
- Wide and square covers both render correctly.
- Canonical signature bar is inserted unchanged.
- HTML validation passes with zero errors.
- Preview renders correctly on mobile.

## Publishing gate

- Title, author, digest, cover, body, and image captions are present.
- No “image failed to load” warnings.
- Default group-notification setting is off.
- If verification is required, the run stops for user scan.
- After submission, the status, appmsg ID, public URL, and Zotero keys are recorded.
- Failures preserve the draft and report the exact blocker.

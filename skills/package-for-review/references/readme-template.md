# README Template for Review Packages

Use this template when creating the README for a review package. The README IS the proposal — the first and possibly only file a reviewer will read. Replace all `{PLACEHOLDER}` values with actual content. Remove any sections that do not apply (e.g., "Decisions We Need to Make" if there are no decisions).

---

```markdown
# {PACKAGE_TITLE}

{ONE_LINE_SUMMARY — what this package contains and why it exists}

---

## Executive Summary

{2-3 sentences: problem, solution, expected impact. This must stand alone — a reader could stop here and understand the proposal.}

---

## Customer Problem / Current State

{What pain exists today, grounded in evidence from the analysis. Narrative prose — no bullet lists. Link inline to the supporting document where evidence lives, e.g., "A [structural analysis](analysis.md) revealed..."}

---

## Proposed Solution

{What is being proposed, how it addresses the problem. Narrative prose. Link to supporting documents for details.}

---

## Evidence

{Key metrics, scenario counts, coverage percentages from the analysis. Every claim links inline to the supporting document. Example: "A [coverage analysis](coverage.md) found that 78% of enterprise scenarios are unaddressed."}

---

## Risks / Gaps

{Top 2-3 issues with mitigation. Narrative prose. Link to supporting analysis where risks are detailed.}

---

## Decisions We Need to Make

1. {Decision 1}? — see [{RELEVANT_DOC}]({RELEVANT_DOC}#section-anchor)
2. {Decision 2}? — see [{RELEVANT_DOC}]({RELEVANT_DOC}#section-anchor)
3. {Decision 3}? — see [{RELEVANT_DOC}]({RELEVANT_DOC}#section-anchor)

---

## How This Was Produced

This proposal was produced through a {BRIEF_DESCRIPTION — e.g., "structured research session analyzing X and Y"}. The full research path — what question started the work, what each step discovered, and how the findings built on each other — is in [research-path.md](research-path.md). The human-readable conversation log is in [chat-history.md](chat-history.md).
```

---

## Writing Guidelines

- **The README is the pitch**. A busy reader who opens only this file should understand: what the problem is, what is proposed, what evidence supports it, and what decisions remain. They should not need to open any other file.
- **500-700 words maximum** — must fit on one printed page.
- **Narrative prose throughout** — no bullet lists in the body sections (Executive Summary through Risks/Gaps). The Decisions section can use a numbered list.
- **Every claim links to evidence** — inline links to the supporting document where the data lives. A skeptical reader can click through to verify any claim.
- **"We" voice throughout** — decisions are framed as "Decisions we need to make", not "Decisions for you". The author is part of the team.
- **"How This Was Produced" is a footer, not the focus** — keep it to 2-3 sentences. Its job is to point curious readers to the research path and chat history, not to tell the research story (that is `research-path.md`'s job).

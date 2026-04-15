# Research Path Template

Use this template when creating the `research-path.md` file for a review package. This file is the provenance document — it tells readers how the proposal in the README was produced, where the supporting evidence lives, and what the key numbers are. Replace all `{PLACEHOLDER}` values with actual content.

---

```markdown
# Research Path

> Provenance document for [{PACKAGE_TITLE}](README.md). This explains how the proposal was produced — the research chain, the supporting evidence, and the key numbers.

---

## How We Got Here

{PARAGRAPH 1 — What question started the research. What was the initial trigger or hypothesis. Why it mattered.}

{PARAGRAPH 2 — What the first analysis found. How that finding raised the next question. What the second step discovered.}

{PARAGRAPH 3 — How the findings accumulated into the proposal. What the overall arc is. What was validated and what remains open.}

{OPTIONAL PARAGRAPH 4 — Any additional context about the research path. Only include if the chain was long enough to warrant it.}

---

## Supporting Documents

If the README raises questions, the supporting evidence is below. Each document builds on the previous one — they follow the research path that led to the proposal.

| Step | File | What It Contains | When to Read |
|---|---|---|---|
| 1 | [{FILE_1}]({FILE_1}) | {Brief description of content and key finding} | {When a reader would need this — e.g., "If you question whether X is really Y"} |
| 2 | [{FILE_2}]({FILE_2}) | {Brief description} | {When to read} |
| 3 | [{FILE_3}]({FILE_3}) | {Brief description} | {When to read} |
| ... | ... | ... | ... |

---

## Key Numbers

- **{NUMBER_1}** {what it means}
- **{NUMBER_2}** {what it means}
- **{NUMBER_3}** {what it means}
- ...

---

## Chat History

The full conversation that produced this package is logged for transparency — anyone can see what was asked, what was produced, and how the analysis evolved.

**[chat-history.md](chat-history.md)** — Condensed, readable log of the session: user requests, AI responses, and the decisions made along the way.

**[session-transcript.jsonl](session-transcript.jsonl)** — Raw Claude Code conversation log in JSONL format. Open this if you need to reconstruct the full unedited transcript.
```

---

## Writing Guidelines

- **"How We Got Here" is the centerpiece** of this document. Do not skip it or compress it to a single sentence. A reader who reads the README and then this section should understand both WHAT is being proposed and the full chain of reasoning behind WHY.
- **Research sequence, not alphabetical** — the supporting documents table follows the logical chain (Step 1, 2, 3...) so a reader who wants to go deeper can follow the same path.
- **"When to Read" column** is critical for busy readers. It tells them: "You do not need to read this unless you have this specific question." This respects their time.
- **Key Numbers** should be the 3-7 most important quantitative findings. A reader scanning this section should get a sense of scale without opening any files.
- **"We" voice throughout** — consistent with the README.

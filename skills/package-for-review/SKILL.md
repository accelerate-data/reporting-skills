---
name: package-for-review
description: Packages session research into a review-ready folder for co-founders and colleagues. Creates deliverable files (if only conversation exists), a README that IS the proposal, a research-path doc, and a chat history — whether the session produced files or only conversation. Use when the user says "package for review", "share this with the team", "make this shareable", "wrap this up for [name]", "review package", "prep for handoff", "summarize this session for others", "summarize for co-founders", "summarize for cofounders", "summarize for others", "summarize this for [name]", "create a review package", or any variation of wanting to turn session output into something others can read.
---

# Package for Review

You package the output of a research or strategy conversation into a folder of files ready to share with co-founders or colleagues who were not in the session.

---

## Hard Rules

1. NEVER write files without completing the inventory (Phase 1) and confirming the output directory with the user
2. NEVER fabricate content that was not in the session — if conversation context has been compacted and detail is missing, say so explicitly in the deliverable
3. ALWAYS produce a README as the package root — it IS the proposal, not a table of contents
4. ALWAYS include a "How This Was Produced" footer in the README linking to `research-path.md` and `chat-history.md`
5. ALWAYS surface decisions and open questions prominently in the README
6. ALWAYS create `research-path.md` with the research narrative, supporting documents table, key numbers, and chat history links
7. ALWAYS create a single `chat-history.md` that logs the full conversation chronologically, and copy the session's JSONL log as `session-transcript.jsonl`
8. ALWAYS use "we" voice for decisions — "Decisions we need to make", never "Decisions for you". The author is part of the team making the decision.
9. The README uses narrative prose (Amazon format, 500-700 words max, no bullet lists in the body sections)
10. NEVER duplicate content that already exists in a file — link to it instead

---

## Phase 0: Detect Mode

Determine what already exists before creating anything.

**Scan conversation context**: Look back through the conversation for what was discussed, what analyses were performed, what conclusions were reached, and what files were created or referenced.

**Scan filesystem**: If the user specified a directory, or if the conversation references output files, use Glob to find markdown files that look like deliverables.

**Classification**:
- **Case A** (files exist): Deliverable files are already on disk with substantive analysis
- **Case B** (conversation only): The conversation contains substantive research, analysis, or conclusions but no files were written
- **Case A+B** (hybrid): Some files exist, but the conversation also contains additional unwritten deliverables

Present the classification to the user:
- List the deliverables you found (files or conversation segments)
- State whether you classify this as Case A, B, or Hybrid
- Ask the user to confirm before proceeding

**If files are in scattered directories**: Ask the user to confirm which files belong in the package. All files should end up in a single output directory.

---

## Phase 1: Inventory

Build a manifest of what the package will contain. This is the critical planning step.

| What to Extract | Source |
|---|---|
| **Deliverables** | Existing files (Case A) or conversation segments (Case B) that contain analysis, proposals, definitions, scenarios, specifications |
| **Research chain** | The logical sequence: what question started the research, what each step found, how each step informed the next |
| **Decisions made** | Explicit decisions confirmed during the session |
| **Decisions needed** | Open questions, unresolved tradeoffs, items deferred for team input |
| **Key numbers** | Statistics, coverage percentages, counts — anything quantitative that anchors the work |
| **Conversation flow** | The chronological sequence of user requests and AI responses — what was asked, what was produced, what was refined |

Present the inventory to the user as a numbered list. Ask:
- "Does this capture everything? Anything to add or remove?"
- "Any framing or emphasis for the reader? For example, which decision is most important, or what you want the reader to focus on."

---

## Phase 2: Create Deliverables (Case B / Hybrid only)

Skip this phase entirely for Case A (all files already exist).

For each deliverable identified in the inventory that does not yet exist as a file, extract it from the conversation into a standalone markdown file. Follow the rules in [references/extraction-guide.md](references/extraction-guide.md).

**Key rules**:
- Each deliverable gets its own file with a clear title and self-contained content
- Preserve the original analysis, reasoning, and evidence — do not rewrite from scratch
- If conversation compaction removed detail, note it: "This section draws from earlier session context that has been compacted. Key conclusions are preserved but intermediate reasoning may be incomplete."
- Minimum viable deliverable: thesis + evidence + implications. Casual discussion that reached no conclusion is not a deliverable.

For 3+ deliverables, use parallel Agent subagents (one per deliverable) for speed.

---

## Phase 3: Create Chat History

Create a single `chat-history.md` file that logs the session conversation chronologically. Follow the template in [references/chat-history-template.md](references/chat-history-template.md).

The chat history captures:
- **User messages**: What the user asked, directed, corrected, or clarified — in their own words where possible
- **AI responses**: Key outputs, decisions, analyses performed, and deliverables produced — summarized, not raw transcript
- **Session arc**: The flow from initial question through intermediate steps to final outputs

**Key rules**:
- Write a clean, readable narrative log — not a raw copy-paste of the conversation
- Each exchange should be a concise summary preserving intent, substance, and sequence
- Note when the user changed direction, corrected the approach, or added new requirements
- Note when context compaction occurred and what may have been lost
- Link to deliverable files where they were produced (e.g., "Produced [scenarios.md](scenarios.md)")
- If the session used subagents, note what was delegated and what came back
- Include a "Raw Transcript" section at the bottom linking to `session-transcript.jsonl`

**Copy the JSONL log**: Locate the current session's JSONL log at `~/.claude/projects/<project-path-hash>/<session-id>.jsonl` and copy it into the package directory as `session-transcript.jsonl`. This is the raw Claude Code conversation log — anyone can reconstruct the full unedited transcript from it.

This gives reviewers two levels of transparency: `chat-history.md` for a quick human-readable overview, and `session-transcript.jsonl` for full reconstruction if needed.

---

## Phase 4: Create Research Path

Create `research-path.md` — the provenance document that tells readers how the work was produced and where to find supporting evidence.

Follow the template in [references/research-path-template.md](references/research-path-template.md).

**Structure (in this order)**:

### 1. How We Got Here

2-4 paragraphs of narrative prose telling the research PATH:
- What question started the work
- What each step discovered
- How each discovery led to the next step
- What the overall arc of the argument is

This is NOT a file list. It is the intellectual thread. A reader who reads this section should understand WHY the proposal in the README reached the conclusions it did.

### 2. Supporting Documents

Table with columns: Step | File | What It Contains | When to Read

- Ordered by the research sequence (the logical chain), not alphabetically
- "When to Read" column tells the reader under what circumstances they would need this doc (e.g., "If you question whether dbt docs are really insufficient")

### 3. Key Numbers

Bulleted list of the most important quantitative findings from the analysis. Gives the reader a quick sense of scale without opening any files.

### 4. Chat History

Link to `chat-history.md` and `session-transcript.jsonl` with a one-sentence explanation that the conversation log and raw transcript are included for transparency into how the work was produced.

---

## Phase 5: Create README

The README IS the proposal. It is the first and possibly only file a reviewer will read. Follow the template in [references/readme-template.md](references/readme-template.md).

If a one-pager or proposal already exists from the session, ask: "There is an existing proposal document. Should I use it as the basis for the README, or generate a fresh one?"

**Structure (in this order)**:

### 1. Title + one-line summary
What this package contains and why it exists, in one sentence.

### 2. Executive Summary
2-3 sentences: problem, solution, expected impact. Must stand alone — a reader could stop here and understand the proposal.

### 3. Customer Problem / Current State
What pain exists today, grounded in evidence from the analysis.

### 4. Proposed Solution
What is being proposed, how it addresses the problem.

### 5. Evidence
Key metrics, scenario counts, coverage percentages from the analysis. Every claim must link inline to the supporting document where the evidence lives (e.g., "A [structural analysis](analysis.md) identified 12 gap items").

### 6. Risks / Gaps
Top 2-3 issues with mitigation.

### 7. Decisions We Need to Make
Numbered list of open questions, linking each to the relevant section of the supporting doc. Framed as "we" — the author is part of the team making the decision.

### 8. How This Was Produced
Short paragraph (2-3 sentences) explaining that this proposal was produced through a research session, with links to the full research path and conversation log:
- Link to `research-path.md` for the research narrative, supporting documents, and key numbers
- Link to `chat-history.md` for the human-readable conversation log

**Rules**:
- 500-700 words maximum — must fit on one printed page
- Narrative prose throughout — no bullet lists in the body sections (Executive Summary through Risks/Gaps)
- Every claim must link inline to the supporting document
- Executive summary must stand alone
- Decisions section can use a numbered list

**Verification before finalizing**:
- All links in the README resolve to real files
- Every file in the directory is referenced somewhere (README or research-path.md — no orphans)
- Decisions use "we" voice throughout

---

## Phase 6: Verification

Before presenting to the user:
1. All files in the manifest exist and are non-empty
2. All cross-references (links between files) resolve
3. The README stands alone as a proposal — a reader could stop there and understand what is being proposed
4. Decisions are surfaced in the README
5. `research-path.md` links to all supporting documents and the chat history
6. No orphan files in the directory

Present the final package to the user as a file tree with a one-line description of each file.

---

## Edge Cases

| Situation | How to Handle |
|---|---|
| **Single deliverable** | Offer lightweight path: "This session produced one analysis. Do you want a full package (README + research path + chat history) or just the file with a brief README?" |
| **Very long compacted session** | Note what appears to be missing. Ask the user: "The conversation references an analysis of X but the details have been compacted. Can you confirm the key conclusions?" |
| **No decisions needed** | Omit the "Decisions We Need to Make" section. Note in the executive summary that this is informational, not a proposal requiring a decision. |
| **Files in scattered directories** | Ask user which files belong in the package. Copy them into the single output directory. |
| **Overlap between files and conversation** | Flag it: "The conversation contains analysis that overlaps with existing file X. Should I link to the existing file or extract a fresh version?" |
| **Output directory already has files** | Warn: "This directory already contains files. Should I add alongside them or create a subdirectory?" |
| **Existing one-pager from session** | Ask whether to use it as the basis for the README or generate fresh. Absorb the content into README format either way — do not keep a separate one-pager file. |

---

## Reference Files

| File | Read When |
|---|---|
| [references/readme-template.md](references/readme-template.md) | You need the full README template with placeholders |
| [references/research-path-template.md](references/research-path-template.md) | You need the full research-path template with placeholders |
| [references/chat-history-template.md](references/chat-history-template.md) | You need to create the chat history file for the package |
| [references/extraction-guide.md](references/extraction-guide.md) | You need to extract deliverables from conversation (Case B) |

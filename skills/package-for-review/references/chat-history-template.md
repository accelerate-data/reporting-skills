# Chat History Template

Use this template when creating the `chat-history.md` file for a review package. This file logs the session conversation chronologically so reviewers can see how the work was produced.

---

```markdown
# Chat History

> Session log for [{PACKAGE_TITLE}]({README_FILENAME}). This is a condensed, readable record of the conversation that produced the deliverables in this package — not a raw transcript.

---

## Session Context

- **Date**: {SESSION_DATE}
- **Starting point**: {What kicked off the session — e.g., "User wanted to evaluate whether X could replace Y"}
- **Files/context loaded at start**: {List key files or documents that were in context when work began}

---

## Conversation Log

### 1. {SHORT_LABEL_FOR_FIRST_EXCHANGE}

**User**: {Summarize what the user asked or directed. Use their exact words where available. If the original wording was lost to context compaction, note: "[Reconstructed — original wording was compacted]"}

**AI**: {Summarize what was done in response. Focus on: what analysis was performed, what was produced, what key findings emerged. Link to deliverable if one was created: "Produced [filename.md](filename.md)"}

---

### 2. {SHORT_LABEL_FOR_SECOND_EXCHANGE}

**User**: {What the user asked next, or how they responded to the prior output}

**AI**: {What was done. If subagents were used, note: "Delegated to 3 parallel agents, one per persona." Summarize the result, not the process.}

---

### 3. {SHORT_LABEL_FOR_THIRD_EXCHANGE}

**User**: {Next request, correction, or direction change. If the user changed course, flag it: "**Direction change**: User shifted from X to Y because..."}

**AI**: {What was done differently and what it produced}

---

{Continue numbering sequentially for each meaningful exchange...}

---

## Session Summary

- **Deliverables produced**: {Numbered list of files created, each linked}
- **Key decisions made during session**: {Bullet list of significant choices — e.g., "Decided to scope scenarios to enterprise personas only, excluding SMB"}
- **Open threads**: {Anything discussed but not resolved or not yet written up}
- **Context gaps**: {Note if context compaction occurred and what detail may have been lost}

---

## Raw Transcript

The full, unedited session transcript is available for anyone who needs to reconstruct the complete conversation:

**[session-transcript.jsonl](session-transcript.jsonl)** — Claude Code JSONL conversation log. Contains every message, tool call, and response from the session in machine-readable format.
```

---

## Writing Guidelines

- **Condensed, not raw**: Each exchange should be 2-5 sentences, not a full transcript. Capture the substance and intent, not every word.
- **Preserve the user's voice**: Where you have the user's exact words, use them (in quotes or as close paraphrases). Do not rewrite their requests into formal language.
- **Label direction changes**: When the user corrected course, changed scope, or rejected an approach, make it visually obvious. Use bold "**Direction change**:" or "**Correction**:" prefixes.
- **Link to outputs**: Whenever an exchange produced a deliverable file, link to it inline. The reader should be able to jump from the conversation moment to the artifact it produced.
- **Note compaction honestly**: If earlier parts of the conversation were compacted and you are reconstructing from memory, say so. Do not fabricate exchanges that you cannot verify.
- **Short labels matter**: The `{SHORT_LABEL}` for each exchange (e.g., "Initial gap analysis request", "Pivot to persona-based scenarios") lets a reviewer scan the conversation arc without reading every entry.
- **Session summary is mandatory**: Even if the log is short, always include the summary section. It is the fastest way for a reviewer to understand what happened.
- **Raw transcript link is mandatory**: Always include the link to `session-transcript.jsonl` so reviewers can access the full unedited conversation if needed.

# Routing — Vault Navigation & Scaling Rules

Last updated: 2026-04-05
Update cadence: When vault structure changes or scaling thresholds are hit

---

## Purpose

This file tells the agent (and future automation scripts) HOW to navigate
the vault, WHERE to route new information, and WHEN to split files. Think
of it as the vault's operating manual.

---

## Read Order (Agent Session Bootstrap)

When starting a new session, the agent should read files in this priority:

1. **index.md** — Current state snapshot. Read FIRST, every session.
2. **commitments.md** — Overdue items need immediate surfacing.
3. **profile.md** — Only if index.md is stale (>7 days old) or if the
   session involves identity/role/goals.
4. **relationships.md** — Only if the session involves a specific person
   or meeting prep.
5. **patterns.md** — Only if the session involves self-reflection,
   performance review, or strategic advice.
6. **decisions.md** — Only if the session references a past decision or
   requires precedent.
7. **corrections.md** — Read during weekly linting, not every session.
8. **soul.md** — Not read at runtime (Option B). The Glean background
   prompt is the canonical behavioral source.
9. **weekly/** — Read the most recent weekly file if the session requires
   last-week context.
10. **raw/** — Not read by the agent unless explicitly asked. These are
    compilation inputs, not runtime context.

---

## Routing Rules (Where New Information Goes)

When the agent extracts information from a session, route it as follows:

| Signal Type | Route To | Example |
|-------------|----------|---------|
| Promise made by Tommy | commitments.md → "I Owe" | "I'll send the recap by Friday" |
| Promise made to Tommy | commitments.md → "They Owe Me" | "Romit said he'd share the data" |
| New person of significance | relationships.md | First meaningful interaction with a skip-level |
| Relationship signal change | relationships.md → update sentiment | Response times dropping, tone shifting |
| Decision made | decisions.md | Chose vendor A over B, with rationale |
| Agent error corrected | corrections.md | Agent said X, reality was Y |
| Work pattern observed | patterns.md → "Pending Review" | Agent notices recurring behavior |
| Everything else | raw/YYYY-MM-DD.md | Session notes, discussion topics, misc |

---

## Scaling Thresholds

| File | Current Size | Split Trigger | Split Into |
|------|-------------|---------------|------------|
| relationships.md | 9 entries | >50 entries OR agent truncates on read | `relationships/firstname-lastname.md` per person |
| commitments.md | 3 entries | >100 active entries | `commitments/YYYY-QN.md` per quarter, with a `commitments/active.md` rollup |
| decisions.md | 3 entries | >75 entries | `decisions/YYYY.md` per year |
| corrections.md | 0 entries | >50 entries | `corrections/YYYY.md` per year |
| patterns.md | 3 entries | >30 approved entries | `patterns/themes/theme-name.md` per theme cluster |
| weekly/ | 0 files | >52 files (1 year) | Archive to `weekly/archive/YYYY/` |
| raw/ | 0 files | >30 unprocessed files | Something is wrong — compilation loop isn't running |

---

## File Hygiene Rules

- **Never delete completed commitments.** Move to "Completed" section.
  They become evidence for performance reflections.
- **Never delete rejected patterns.** They teach the agent what not to infer.
- **Never delete corrections.** They are the gradient descent of the system.
- **Raw files with STATUS: PROCESSED can be archived** after the weekly
  consolidation confirms their content has been absorbed.
- **index.md staleness >14 days** should trigger an alert. If the index
  is stale, the agent is starting every session from an outdated worldview.

---

## Future Automation Hooks

When the compilation loop is built (Phase 2), these are the expected jobs:

| Job | Frequency | Input | Output |
|-----|-----------|-------|--------|
| Daily session log | End of day | Agent conversation transcript | raw/YYYY-MM-DD.md |
| Weekly consolidation | Sunday evening | All raw/ files with STATUS: UNPROCESSED | weekly/YYYY-WNN.md + updates to commitments, relationships, patterns |
| Index refresh | After weekly consolidation | All vault files | Updated index.md |
| Linting pass | Weekly (during consolidation) | All vault files + corrections.md | Flag inconsistencies, propose pattern entries, detect staleness |

---

## Vault Ownership

- **Vault owner:** Tommy Magee (tmagee@rivian.com)
- **Access:** Private — only Tommy should be able to read/write these files
- **Glean visibility:** Files in this Drive folder will be indexed by Glean
  and searchable by the Chief of Staff agent running as Tommy
- **Exception:** raw/ files may be kept outside the Drive folder or tagged
  STATUS: UNPROCESSED to prevent Glean from surfacing stale transcripts
  in search results
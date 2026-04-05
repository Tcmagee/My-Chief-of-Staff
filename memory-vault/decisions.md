# Decisions

Last updated: 2026-04-05
Update cadence: When a meaningful decision is made

---

## Decision Log

### 2026-04-05 — Memory vault architecture: Google Drive + Markdown

**What was decided:** Build the Chief of Staff memory layer as a structured
folder of Markdown files in Google Drive, leveraging Glean's existing crawl
for indexing. Follows Karpathy's LLM Knowledge Base pattern.

**Why:** Glean has no native cross-session memory. The agent is ~80% accurate
but can't learn or retain corrections. Google Drive is already indexed by Glean,
requires no API setup for v1, and Markdown is the most LLM-friendly format.

**Alternatives considered:**
1. Glean Indexing API custom datasource — faster indexing but requires API token,
   admin setup (Shan), and code. Deferred to Phase 4.
2. Databricks-backed structured memory — too heavy for a solo pilot.
3. Confluence pages — possible but less LLM-friendly formatting, heavier UI.
4. No memory layer / status quo — rejected; the gap is real and limiting adoption.

**Who was involved:** Tommy Magee (decision maker), Glean Assistant (advisor)

**Outcome:** Vault folder created, seed files being drafted.
---

### 2026-03-10 — Chief of Staff agent: background prompt vs. agent builder

**What was decided:** Build the Chief of Staff agent using Glean's background
prompt tuner only — no deterministic agent builder flow (triggers, blocks, steps).

**Why:** The background prompt approach produces a better semantic agent than
trying to build a deterministic flow. The agent needs to reason across sources,
not follow a script.

**Alternatives considered:**
1. Agent builder with structured steps — tested, felt rigid and less capable
   for advisory use cases.
2. Multi-agent setup — too complex for v1.

**Who was involved:** Tommy Magee

**Outcome:** Agent launched, well-received. Showcased at AI Champions March 2026.
Users report it "sees right through them" on patterns and performance prompts.

---

### 2026-03-23 — Facilities LLM Context Guide: publish as standalone doc

**What was decided:** Create a comprehensive Markdown context guide for the
Facilities department that any LLM, agent, or gem can load for full
organizational understanding.
**Why:** LLMs frequently misattribute scope to Facilities (confusing Jimmy Knauf's
org with Vince Falzetta's plant ops, or Marketing's Brand Experience team).
A canonical context doc prevents these errors.

**Alternatives considered:**
1. Embed context directly in each agent's prompt — doesn't scale, duplicates effort.
2. Rely on Glean's organic indexing — too noisy, no disambiguation.

**Who was involved:** Tommy Magee, Travis Munson (reviewer)

**Outcome:** v1.4 published. Travis noted it might be "too detailed" but agreed
the depth is valuable for edge cases.
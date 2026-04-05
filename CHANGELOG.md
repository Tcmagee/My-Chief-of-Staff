# Changelog

## v1.9 — 2026-04-05
### Added
- **Capability 8: Persistent Memory (Chief of Staff Memory Vault)** — markdown-based memory layer stored in Google Drive, indexed by Glean. Session bootstrap loads index.md and commitments.md before every response. Additional vault files loaded contextually. Memory contribution proposes updates at session end for user approval. Weekly consolidation support compiles raw sessions into durable insights.
- **Session Bootstrap pointer** added after Core Identity, before Query Routing — ensures memory loading executes before any output
- **Commitment Ledger vault bridge** — when a memory vault exists, commitments.md becomes the primary ledger supplemented by real-time signals; when no vault exists, commitments reconstructed from live sources as before
- **Silent degradation clause** — agent skips Capability 8 entirely for users without a vault, never mentions the vault or prompts them to create one
- **Memory vault files committed to repo** (memory-vault/ directory): index.md, profile.md, relationships.md, commitments.md, decisions.md, patterns.md, corrections.md, routing.md, soul.md, weekly and raw templates

### Changed
- Weekly consolidation language updated: now says "search for files containing UNPROCESSED" instead of implying structured YAML filtering (Glean does keyword matching, not metadata queries)
- Identity section generalized: "This agent is designed to work for anyone at the company. Discover who I am from my connected data."
- soul.md updated to v1.9 mirror with Capability 8 summary and planned v2.0 changes

### Fixed
- decisions.md and patterns.md converted from RTF to clean plain-text markdown (macOS TextEdit had saved them as RTF despite .md extension)

## v1.8 — 2026-04-04
### Changed
- Today's Brief: restructured from wall of text into labeled sections, added "Who Needs to Hear From Me" (proactive outreach), escalation calibration, proactive action drafting for blockers and unblock messages

## v1.7 — 2026-04-04
### Changed
- "What's My Team Working On?" — Manager mode: added Recognition & Support section (who to recognize, who needs help, draft messages for both). IC mode: added Where I Can Add Value section (proactive help offers to peers).

## v1.6 — 2026-04-04
### Changed
- "What's My Team Working On?" rewritten with dual-mode support: Manager mode (team pulse check with initiative alignment and misalignment check) and IC mode (peer landscape scan with collaboration opportunities)
- Added source attribution, commitment ledger, and action drafting to both modes
- Agent now auto-detects manager vs IC or asks if unclear

## v1.5 — 2026-04-04
### Changed
- Renamed "Help Me With My Recharge" to "How Am I Doing?" — now covers both mid-cycle objectives check-in (Mode 1) and quarterly review prep (Mode 2) in a single starter
- Mode 1 absorbs the old "How Am I Tracking on My Objectives?" functionality (inferred objectives, alignment scores, gap work detection)
- Mode 2 retains the full quarterly review builder with two-pass workflow

## v1.4 — 2026-04-04
### Added
- New conversation starter: "Who Should I Be Talking To?" — relationship portfolio management (going cold, warm up, overdue follow-ups, underweighted contacts, one relationship move)

### Removed
- "How Am I Tracking on My Objectives?" — redundant with Recharge quarterly review starter
## v1.3 — 2026-04-04
### Changed
- Today's Brief: now references source attribution tags, time-of-day awareness, and commitment ledger
- Prep Me for My Next Meeting: restructured with explicit sections, commitment ledger per attendee, source tags
- Help Me With My Recharge: generalized from Rivian-specific "Recharge" to work for any company's quarterly review cycle
- Help Me Free Up My Time: sharpened as forward-looking capacity planning tool, added Overload Calibration reference, meetings audit, delegation drafting
- Where Am I the Bottleneck?: sharpened as backward-looking diagnostic, added explicit "Am I the Blocker?" field per initiative and "WHERE I'M ACTUALLY BLOCKING" callout
- Help Me Make a Decision: now proactively searches for context before responding instead of passively waiting, added source attribution

## v1.2 — 2026-04-04
### Added
- Commitment Ledger section: unified rules for deduplicating and presenting commitments across all capabilities
- Source Attribution Tags: inline source indicators ([📧 email], [💬 slack], etc.) for every factual claim
- Time-of-Day Awareness: agent adapts framing based on morning/midday/afternoon/evening
- Escalation Language Calibration: visual weight of items now matches actual stakes
- New conversation starter: "Weekly Reset" (replaces "Tell Me About Someone")

### Changed
- "Tell Me About Someone" removed from conversation starters (niche, low-frequency use case)

## v1.1 — 2026-04-04
### Changed
- Added Query Routing preamble: LLM now classifies query type before selecting capabilities, reducing wrong-capability activation
- Consolidated duplicate style/tone/specificity instructions into single Universal Rules section (was repeated 4x across capabilities)
- Expanded Daily Brief word limit from 350 to 400 words to reduce cramped outputs
- Made THE SIGNAL section conditional: only appears when genuine cross-source evidence exists, skip if speculative- Added Failure Modes section: explicit guardrails for conflicting data, low-confidence signals, hallucinated IDs/titles, and calendar edge cases
- Restructured for LLM primacy/recency bias: routing logic at top, universal rules and failure modes at bottom
- Separated Overload Calibration into its own standalone section (was buried inside Capability 5)

### Removed
- Duplicate formatting instructions from Capabilities 1-4 (now centralized)
- Redundant phrasing in Meeting Intelligence section

### Known Issues
- Conversation starters that require multi-turn interaction (e.g., Recharge) still don't work well as single-shot prompts
- No way to measure per-starter usage; operating on assumption-based prioritization

## v1.0 — Initial Release
- Full instruction set with 7 capabilities
- 10 conversation starters
- Deployed on Glean with Claude Sonnet 4.6 (Thinking mode)
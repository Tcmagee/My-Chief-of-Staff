# Changelog

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
- Made THE SIGNAL section conditional: only appears when genuine cross-source evidence exists, skip if speculative
- Added Failure Modes section: explicit guardrails for conflicting data, low-confidence signals, hallucinated IDs/titles, and calendar edge cases
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

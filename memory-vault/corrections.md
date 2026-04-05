# Corrections

Last updated: 2026-04-05
Update cadence: Whenever the agent gets something meaningfully wrong

---

## How This File Works

This is the agent's error log. When the Chief of Staff agent produces output
that is factually wrong, misreads a relationship, gives bad advice, or makes
a category error — log it here. Each entry captures:

- **Date:** When the error occurred
- **What the agent said:** The specific claim or recommendation
- **What was actually true:** The correct information
- **Category:** [Factual | Relationship | Org Structure | Prioritization | Tone | Other]
- **Why it matters:** What would have gone wrong if uncorrected
- **Corrective rule:** What the agent should do differently next time

The agent should read this file during weekly linting passes to avoid
repeating the same category of errors. Over time, patterns in this file
may trigger updates to soul.md (the behavioral spec) or profile.md.

---

## Error Log

### SEED ENTRY — Known Category Risks (Pre-Vault)

These are error categories observed before the memory vault existed,
based on Tommy's assessment that the agent is "about 80% accurate."

| Category | Known Risk | Example |
|----------|-----------|---------|
| Org Structure | Confuses Facilities (Jimmy Knauf / CFO org) with Manufacturing plant ops (Vince Falzetta / Ops & Manufacturing org) | Attributing Normal plant maintenance to Facilities |
| Org Structure | Includes Marketing/Brand Experience people (Liz Guerrero, Jenna Lutwin, Max Wong) as Facilities team members because Workday department tag says "Facilities" | Profile cards showing wrong org membership |
| Relationship | Over-infers relationship strength from calendar co-occurrence without checking RSVP status | Concluding strong working relationship from Maybe/Declined meetings |
| Prioritization | Tends to flag too many items as URGENT | Brief had 5+ urgent items when realistically 1-2 were genuine |
| Factual | Occasionally hallucinates specific ticket IDs or dates when Jira data is sparse | Referenced a ticket that didn't exist |

---

## Active Corrections

*No active corrections logged yet. First entries expected after initial
vault-powered sessions in W15.*
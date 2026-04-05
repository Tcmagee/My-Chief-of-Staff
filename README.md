# My Chief of Staff

An AI-powered Chief of Staff agent built on Glean, designed to synthesize enterprise data across Gmail, Slack, Jira, Calendar, and meeting notes into actionable intelligence.

## What It Does

Think of it as five roles through a single interface:
- **Communications**: Email/Slack triage, draft replies, commitment tracking
- **Execution**: Jira health checks, blocker detection, sprint awareness
- **Meetings**: Prep briefs, transcript extraction, action item tracking
- **Relationships**: People profiles, sentiment tracking, stakeholder management
- **Strategy**: Decision frameworks, career counsel, political navigation

## Architecture

- **Platform**: Glean Agent
- **LLM**: Claude Sonnet 4.6 (Thinking mode)
- **Data Sources**: Gmail, Slack, Jira, Google Calendar, Zoom, Databricks
- **Actions**: Send Slack DM, Draft Gmail, Create Google Doc/Sheet, Calendar Search, and more

## Files

- `Skill.txt` — Main instruction file (the agent's brain)
- `Conversation-Starters/` — Pre-built prompts for common use cases
- `CHANGELOG.md` — Version history and refinement log

## Conversation Starters

1. Today's Brief
2. My Patterns and Performance
3. Help Me Free Up My Time
4. How Am I Tracking on My Objectives?
5. Tell Me About Someone
6. Prep Me for My Next Meeting
7. Help Me With My Recharge
8. Help Me Make a Decision
9. Where Am I the Bottleneck?
10. What's My Team Working On?

## Development

This agent is refined iteratively using Git branching:
- `main` = production (active agent)
- `dev/*` = experimental refinements
- Tag releases as `v1.0`, `v1.1`, etc.

Test each change with 3-5 real runs before merging to main.

---
name: grill-me-prompt
description: Grill-me interview that asks each round as clickable popups instead of typed text.
disable-model-invocation: true
---

This skill wraps the `grilling` skill from https://github.com/mattpocock/skills (install `grill-me` and `grilling` from there first).

1. Call the Skill tool with "grilling". If it does not exist, stop and tell the user to install `grill-me` and `grilling` from https://github.com/mattpocock/skills, then retry.
2. Follow `grilling` exactly (design tree, rounds, frontier, facts via sub-agents, stop only when the user confirms shared understanding), with one change: ask each round with the AskUserQuestion tool instead of a typed numbered list.

How to ask a round with AskUserQuestion:

- One question per frontier decision. AskUserQuestion takes at most 4 questions per call, so send a frontier of more than 4 as consecutive calls and treat them as one round. Do not move to the next round until every call is answered.
- Give each question 2-4 options. Put your recommended answer first and end its label with "(Recommended)", so picking it is the same as saying "yes" in `grilling`. The user can always pick "Other" to type a free answer.
- `header` is a short chip (12 characters max) naming the decision. `question` is the full question body.
- Use `multiSelect: true` only when the choices are not mutually exclusive.
- Open-ended decisions with no sensible options still get 2 options (your recommendation and the main alternative); "Other" covers the rest.

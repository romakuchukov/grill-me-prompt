# grill-me-prompt

A Claude Code plugin that adds `/grill-me-prompt`: the [grill-me](https://github.com/mattpocock/skills/tree/main/skills/productivity/grill-me) interview, but each round is asked as clickable popups (with a recommended answer first and an "Other" box) instead of a typed numbered list.

## Requirement

This plugin does **not** include the interview itself. It wraps Matt Pocock's `grilling` skill, so you must install these two skills from [mattpocock/skills](https://github.com/mattpocock/skills) first:

- `grill-me`
- `grilling`

Without `grilling`, `/grill-me-prompt` stops and tells you to install it.

## Install

```
/plugin marketplace add romakuchukov/grill-me-prompt
/plugin install grill-me-prompt@grill-me-prompt
```

## Use

Run `/grill-me-prompt:grill-me-prompt` (Claude Code namespaces plugin skills; typing `/grill-me-prompt` autocompletes to it), then describe the plan, decision, or idea to stress-test.

## Start with a spec

Bring a rough spec: a few lines or a file path covering the goal, the constraints you already know, and what "done" looks like. For example: `/grill-me-prompt:grill-me-prompt ./docs/plan.md`.

The more the model can read up front, the more its questions target your actual gaps and the fewer generic ones it asks. With no spec, round one is spent on basics (what are we building, for whom) and the popups can't offer sharp options. A one-line idea still works, but expect more rounds.

## How it works

The skill calls `grilling`, follows it unchanged, and swaps only the output format: each round goes through the `AskUserQuestion` tool (max 4 questions per call, 2-4 options each, recommended option first).

## Credit

The interview method belongs to [Matt Pocock's skills](https://github.com/mattpocock/skills) (MIT). This repo only changes how the questions are shown.

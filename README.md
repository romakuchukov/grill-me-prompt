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

## How it works

The skill calls `grilling`, follows it unchanged, and swaps only the output format: each round goes through the `AskUserQuestion` tool (max 4 questions per call, 2-4 options each, recommended option first).

## Credit

The interview method belongs to [Matt Pocock's skills](https://github.com/mattpocock/skills) (MIT). This repo only changes how the questions are shown.

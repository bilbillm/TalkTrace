---
description: Use TalkTrace workflow for chat reply drafting and local relationship notes.
globs:
  - "**/*.md"
alwaysApply: false
---

# TalkTrace Cursor Rule

When the user asks how to reply to a chat, analyzes a chat object, initializes an alias, updates relationship notes, or reviews a sent reply, treat this repository as a TalkTrace workspace.

Read `AGENTS.md` before working. Use `me/` for global user style and `people/<alias>/` for object-specific files. Create new aliases from `people/_template/` or with `scripts/new-person.ps1 -Alias <alias>`.

Keep private chat data local. Do not save raw full chat logs by default, do not diagnose or manipulate people, and do not copy relationship judgments between aliases unless the user explicitly asks.

# TalkTrace for Claude Code

This repository is a local-first TalkTrace workspace template and agent workflow.

When the user asks for help with chat replies, chat screenshots, relationship notes, object/person aliases, persona/style updates, or post-reply review, read `AGENTS.md` first and follow it as the source of truth.

Core rules:

- Keep TalkTrace as a local private workspace. Do not put real chat records into the public template clone.
- Use `me/` for global user style and relationship patterns.
- Use `people/<alias>/` for one isolated chat object. Do not transfer judgments across aliases unless the user explicitly asks.
- For a new alias, copy `people/_template/` to `people/<alias>/`, or run `scripts/new-person.ps1 -Alias <alias>` on Windows.
- Draft short reply options by default: safest, closer, shortest/ending.
- Persist only confirmed or useful observations, and avoid raw full chat logs.
- Do not diagnose, manipulate, pressure, or pathologize anyone.

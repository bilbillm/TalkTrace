---
name: talktrace
description: Local-first chat relationship memory and reply drafting workflow. Use when the user pastes chat records or screenshots, asks how to reply, wants to analyze a chat object/person, initialize or maintain TalkTrace relationship files, update persona/style/cases notes, or review feedback after a sent reply.
---

# TalkTrace

## Overview

Use TalkTrace as a trigger layer for a local private workspace. The skill should help the agent enter the TalkTrace workflow from any conversation, while all long-term private data remains in the user's local `TalkTrace-workspace`.

## Workspace Resolution

Find the TalkTrace workspace before drafting relationship analysis:

- Prefer the current directory when it contains `AGENTS.md`, `me/`, and `people/`.
- Otherwise check `TALKTRACE_WORKSPACE`, then common local paths such as `~/Documents/TalkTrace-workspace` and `~/TalkTrace-workspace`.
- If no workspace exists and the user asked to install or initialize TalkTrace, use the repository install scripts when available:
  - Windows: `powershell -ExecutionPolicy Bypass -File scripts/install-talktrace.ps1 -Destination "$HOME\Documents\TalkTrace-workspace"`
  - macOS/Linux: `bash scripts/install-talktrace.sh "$HOME/TalkTrace-workspace"`
- Do not store real chat records inside the public template clone. Use the generated local workspace for private notes.

## Core Workflow

After locating the workspace:

1. Read the workspace `AGENTS.md` first and follow it as the source of truth.
2. Identify the chat object alias. If it is missing, ask for the alias or whether to create a new one.
3. Read global files: `me/profile.md`, `me/style.md`, and `me/unconscious.md`. Read `me/cases.md` only when cross-object history matters.
4. Read object files: `people/<alias>/profile.md`, `persona.md`, `unconscious.md`, and `style.md`. Read `cases.md` when historical feedback matters.
5. Analyze only from provided chat text, screenshots, confirmed history, and the user's current reply goal. Mark uncertainty explicitly.
6. Draft 2-3 directly sendable replies by default: safest, closer, and shortest/ending.
7. Update files only when the user confirms an outcome, asks to record an insight, or provides feedback that changes the relationship/persona/style/case notes.

## New Object Initialization

When the user provides a new alias, create `people/<alias>/` from `people/_template/`:

- Prefer `scripts/new-person.ps1 -Alias <alias>` on Windows.
- Prefer `bash scripts/new-person.sh <alias>` on macOS/Linux.
- Use aliases rather than real names.
- Replace `<alias>` placeholders in the copied files.

## Output Shape

For normal reply help, keep output short:

```text
我判断：[一句话说明对方状态/意图，保留不确定性]

别这样回：[1-3 个明显踩雷点]

可以发：
1. 稳妥版：“...”
   效果：...
2. 拉近版：“...”
   效果：...
3. 收尾版：“...”
   效果：...
```

Use fuller analysis only when the user asks for detailed analysis.

## Boundaries

- Do not diagnose, pathologize, or essentialize anyone.
- Do not use TalkTrace for manipulation, coercion, PUA, or pressure.
- Do not save complete raw chat logs by default; summarize selected cases.
- Do not transfer intimacy level, successful phrasing, or relationship judgment from one object to another unless the user explicitly asks.
- Keep real names, account IDs, screenshots, raw exports, addresses, and identifying media out of public repositories.

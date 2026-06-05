# Website Copy

## Title

Furhatling

## Tagline

A tiny social robot pet for watching coding agents work.

## Short Description

Furhatling is a Petdex desktop companion that turns Codex and Claude Code activity into small ambient animations: working, waiting, reviewing, failing, and finishing.

## Project Summary

Furhatling started as a playful side project around a serious workflow problem: agentic coding work often happens in the background, and it is easy to lose track of whether the agent is running tools, waiting for approval, reviewing code, or done.

The pet sits on the desktop as a small animated robot presence. It reacts to local Petdex hooks from Codex and Claude Code, showing state changes through a compact sprite animation and short status bubbles.

Visually, it is inspired by warm social robots: a smooth white head, a softly projected face, and small curious movements instead of a generic robot mascot.

## What I Built

- A custom Petdex pet called `furhatling`
- A full 8 by 9 animation atlas with Petdex/Codex states
- Runtime packaging with `pet.json` and `spritesheet.webp`
- Preview GIFs for every animation state
- Install instructions for Petdex, Codex, and Claude Code hook usage
- A small workflow for switching between custom pets from the terminal

## Tech

- Petdex Desktop
- Petdex CLI
- Codex hooks
- Claude Code hooks
- Local sidecar on `127.0.0.1:7777`
- WebView/CSS sprite rendering
- Animated WebP spritesheet

## How It Works

Petdex installs local hooks into supported coding agents. When Codex or Claude Code starts work, runs a tool, waits for input, or finishes a task, the hook sends a local state update to Petdex. Petdex then changes the floating pet's animation and can show a short status bubble.

The pet itself is intentionally simple: one manifest file and one spritesheet. The intelligence is not in the pet. The pet is a small ambient display for agent state.

## Suggested Project Page Layout

1. Hero: Furhatling name, short tagline, animated `previews/idle.gif` or `previews/running.gif`.
2. Why: a short paragraph about making agent work more visible.
3. How it works: Petdex hooks, local sidecar, sprite states.
4. Tech stack: Petdex, Codex, Claude Code, WebView, WebP atlas.
5. Install: link to the GitHub repo or release zip.
6. Gallery: contact sheet or several preview GIFs.

## Button Labels

- Download Furhatling
- View on GitHub
- View install guide
- See animation states

## Caption Ideas

- `idle.gif`: Resting on the desktop until the agent starts working.
- `running.gif`: Active tool execution or background agent work.
- `waiting.gif`: Waiting for approval, credentials, or a user decision.
- `review.gif`: Reading, checking, or reviewing output.
- `failed.gif`: Something needs attention.

## Credit / Note

A personal side project by Leo Gardberg, inspired by social robotics and warm conversational robot design. Built with rights-cleared visual references.

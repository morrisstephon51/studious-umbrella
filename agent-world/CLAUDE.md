# Agent World — CLAUDE.md

Sims-style gamified dashboard for all Plug AI agents.

## What This Is

A visual, interactive dashboard where each AI agent appears as an animated Sim character in their own room. Thought bubbles show their current task. XP, levels, achievements, and streaks are all visible at a glance. Click any agent to open their full profile.

## Stack

- Single `index.html` — React 18 via CDN, all CSS inline
- No build step. No dependencies. No paid services.
- Deploy with Vercel: just point to the `agent-world/` directory

## Agent Registry

All agents are defined in the `AGENTS` array inside `index.html`. Each agent has:

| Field | Description |
|---|---|
| `id` | Unique identifier |
| `name` | Display name |
| `role` | Agent function |
| `emoji` | Avatar character |
| `color` / `accent` / `text` | Color scheme |
| `repo` / `repoUrl` | GitHub repo |
| `entity` | `Plug AI`, `BigHeart`, or `Personal` |
| `status` | `working`, `thinking`, `idle`, `sleeping`, `blocked`, `done` |
| `xp` / `level` | Gamification stats |
| `done` | Tasks completed count |
| `streak` | Day streak count |
| `achievements` | Array of unlocked achievements |
| `task` | Current task shown in thought bubble |
| `skills` | Array of skill tags |

## Updating Agent Status

Edit the agent's `status` and `task` fields in `AGENTS`. Redeploy.

Future: connect to a Supabase table and poll every 30s for live updates.

## Adding a New Agent

Add an entry to `AGENTS` following the same shape. Pick a unique `color` from the Tailwind palette.

## XP System

- Levels 1–9+: each level requires 400 XP
- `level` × 400 = XP needed for next level
- Progress bar = `(xp - (level-1)*400) / 400 * 100`
- Titles: Apprentice (1-2) → Agent (3-4) → Senior (5-6) → Principal (7-8) → Director (9+)

## Visual Reference

Inspired by The Sims:
- Isometric grid floor animation
- Animated emoji avatars (walk / think / sleep)
- Thought bubbles with circular tail (classic Sims style)
- Green plumbob diamond above selected agent
- Status dots with glow
- Dark cyberpunk color palette

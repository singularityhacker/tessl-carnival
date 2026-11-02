# Tessl Carnival — Justice's workshop fork

Workshop repo for **"Build your own software factory with context"** (Tessl, AI Native DevCon NYC, Nov 2–4 2026). Upstream: [tesslio/tessl-carnival](https://github.com/tesslio/tessl-carnival). Original README: [README.upstream.md](README.upstream.md).

## What it is
- **The carnival:** a small browser game (Vite/Node). A midway you walk around, with one game booth, the **water cannon**. Every merge to `main` redeploys it to GitHub Pages.
- **The point:** build a *software factory* on this repo — loops where an AI agent does a job on its own when something happens, following a written **skill**, and an independent reviewer checks it before you merge.

## How it works
1. **Tessl** is a platform for "context" for coding agents: skills (`SKILL.md` files describing how to do a job) plus project rules (`AGENTS.md`, the carnival's house rules).
2. **Factory setup** (`tessl` CLI + its setup skill) links the repo to Tessl, creates a cloud environment per automation, adds a `tessl` label, and installs two GitHub Apps: the **Tessl GitHub App** (does the work) and **Tessl Review** (reviews it, so the factory never grades its own work).
3. **Shipping a change without writing code:** write an issue with a "Done when", add the `tessl` label → the factory writes code and opens a PR → Tessl Reviewer reviews → an "answer reviews" loop fixes what review flags → you merge → Pages redeploys.
4. **Tracks (optional):** teach review the house rules, add a scheduled maintenance loop that files issues, run several issues at once, or factory-ify your own repo.

## Setup
Needs git, Node ≥ 22.13, `gh` (logged in), a coding agent, and the Tessl CLI:
```bash
curl -fsSL https://get.tessl.io | sh   # not npm; package is deprecated
tessl login
gh repo fork tesslio/tessl-carnival --clone
cd tessl-carnival && npm ci && npm run dev   # http://localhost:5173
```
Then tell your agent: **"Check I'm ready for the workshop"**, then **"Set up my fork"** (enables Issues/Actions/Pages), then **"Read workshop/agent.md and take me through the core path, one step at a time."** Full guide: [workshop/agent.md](workshop/agent.md).

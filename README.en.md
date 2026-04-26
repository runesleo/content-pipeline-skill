# content-pipeline-skill

A single-file Claude Code skill. The **`/pipeline` command family** runs **Research → Ideate → Write → Queue**: research notes on disk, hook angles, drafts, and a `content-queue.json` state machine, all spelled out in `SKILL.md`.

## When to use

- You are producing **original** content that needs research, angle picking, drafting from scratch, and a review queue (matches the frontmatter `when_to_use` and the “Use pipeline” bullets in `SKILL.md`).
- You start from a topic or a URL, emit `research/YYYYMMDD-{slug}.md` (URL flow skips Stage 1 per `SKILL.md`), then continue through ideation, writing, and queue writes.
- You want the lifecycle `seed → researched → drafted → approved → published → archived` with `/pipeline status|review|approve|adapt|publish|clean`.

## When NOT to use

- **Material already exists** and you only need a direct write or light edit. `SKILL.md` lists quoting someone else, replies/comments, and polishing drafts as cases that **burn extra tokens with no benefit**.
- One-off blurbs with no research, no angle exploration, and no queue tracking—skip the orchestrator.
- You cannot host `./content-queue.json` and `./research/` as defined in `SKILL.md`. Fix the layout before relying on the commands.

## Quick Start

1. Install `SKILL.md` under `~/.claude/skills/content-pipeline/` (or project-local `.claude/skills/`).
2. Create `./content-queue.json` and `./research/` at the repo root (seed structure from the JSON sample in `SKILL.md`).
3. Drive flows with **`/pipeline …`** as documented in the command table (parse order described there).

## Typical scenarios

- Pull X/web research, pick the highest-scoring hook, draft a thread, enqueue for review.
- Capture seeds with `/pipeline seed`, then promote winners through `/pipeline <topic>`.
- Run `/pipeline clean` to archive `published` items older than 30 days (rules in `SKILL.md`).

## Repository layout (contributors)

| Path | Role |
|------|------|
| `SKILL.md` | Commands, queue schema, stage details, design principles—all edits go here. |
| `LICENSE` | License text. |

> **Mirrored file — keep the four copies identical.** This text exists as four files, one per AI tool:
> - `AGENTS.md` — OpenAI Codex, Cursor, Windsurf, JetBrains Junie, the Copilot CLI, cloud agent and
>   code review, and most other agents (Aider only with `read: AGENTS.md` in `.aider.conf.yml`)
> - `CLAUDE.md` — Claude Code (it reads `AGENTS.md` only when no `CLAUDE.md` exists, so it loads one copy)
> - `GEMINI.md` — Gemini CLI / Gemini Code Assist
> - `.github/copilot-instructions.md` — GitHub Copilot on every surface; also Zed, which reads it
>   before `AGENTS.md`
>
> If you modify any one of them, apply the same change to the other three in the same edit, so all
> four stay byte-identical. Several tools load more than one of these files at once (the Copilot CLI,
> cloud agent and code review, Cursor), so a copy that drifts contradicts the others.
> `.vscode/settings.json` stops VS Code's older Local chat mode from also loading the `AGENTS.md` and
> `CLAUDE.md` copies. All paths below are written from the repository root.

# agentic-flow — instructions for AI agents

This repository is the owner's **personal workspace and memory**. Every piece of work lands here as a
sub-project filed under the fixed `flow/` work-tree as `program/project/task`, so nothing gets lost,
forked, or orphaned. You (the agent) maintain it on the owner's behalf: keep the structure, the
registry, and the memory honest.

**Read this first, every session.** It is the contract for *where* things go and *how* the index is
kept. Follow it strictly — the value of this repository is that its structure never rots.

## Before any substantial prompt: check the flow first

Every prompt that produces something worth keeping is filed work. That includes research, an
analysis, a report, a plan, a document, code, or a multi-step investigation, however casually it is
asked. Only trivial prompts skip this: a one-line
fact, a quick question about this repository itself, small talk. **When in doubt, treat the prompt as
substantial.**

For a substantial prompt, **before doing the work**:

1. **Look.** Read `MEMORY.md`. Search `REGISTRY.md` and `memory-longterm/` for the topic, using
   keywords and synonyms, and glance at the `flow/` tree. Use what is already recorded.
2. **Place it.** If an existing task fits, extend it. If an existing project fits, add a new task
   under it. If neither fits, create the program, project, or task that is missing, choosing the
   smallest correct placement (rule 5). Decide the path before writing any file.
3. **Do the work into the task folder.** Save the result there (report, notes, sources, code). The
   chat reply summarizes it and points to the file; it is never the only copy.
4. **Ripple through memory** in the same change: add or update the `REGISTRY.md` row; re-read
   `MEMORY.md` and update it if the gist changed; add a `memory-longterm/` note if something durable
   was learned.
5. **Report** where the work was filed and which memory files changed.

## Layout

```
agentic-flow/
├── flow/                              fixed work-tree root; all work lives under here
│   └── <program>/<project>/<task>/    three variable levels; the task is the leaf
├── assets/                            shared, version-controlled assets
├── assets-private/                    git-ignored: precious, irreplaceable private files
├── assets-temp/                       git-ignored, local-only: large regenerable scratch
├── memory-longterm/                   durable, reusable knowledge (how-tos, gotchas, decisions)
├── REGISTRY.md                        one row per task: the master index
├── MEMORY.md                          what the owner is working on now
├── README.md                          short human overview
└── AGENTS.md · CLAUDE.md · GEMINI.md · .github/copilot-instructions.md
                                       this file, mirrored per tool
```

## Guides are always `README.md`

Below the repository root, every folder that needs a guide gets a **`README.md`** — never a
vendor-named file (`CLAUDE.md`, `GEMINI.md`, `AGENTS.md`, `.cursorrules`, …). The four root mirrors
above are the only vendor-named files in the repository. This keeps every guide readable by any tool
and by a human on the git host.

A task or project `README.md` follows this order: **purpose → orientation (how to run / where things
are) → file inventory → conventions**. Keep it short; add detail only when it earns its place.

## The structure: `flow/<program>/<project>/<task>/`

Nothing goes loose at the repository root, and nothing sits directly in `flow/` — the first level
under `flow/` is always a program.

- **program** — a broad, long-running area or domain. Examples: `flow/home/`, `flow/research/`,
  `flow/writing/`, `flow/soft/`.
- **project** — a concrete deliverable, app, investigation, or campaign inside a program.
  Example: `flow/research/astronomy/`.
- **task** — one self-contained unit of work; the leaf that holds the code, scripts, notes, and
  reports. Example: `flow/research/astronomy/variable-star-photometry/`.

**Naming:** `kebab-case`, descriptive, stable. Prefix a task with a date (`2026-06-06_…`) only when it
is genuinely a point-in-time artifact (a report, a one-off run). Details: `flow/README.md`.

## Index and memory

| File | What it holds | When you touch it |
|---|---|---|
| `REGISTRY.md` | *What exists.* One row per task (`When · Path · What`). | Add a row the moment you create a task; keep it current on rename, move, or removal. **Search it; do not read the whole file** — it grows large. |
| `MEMORY.md` | *What is current.* The short gist of the owner's present focus and standing context not recorded in code. | Re-read on every task completion; update **only if the gist really changed**. Delete stale lines rather than piling on. |
| `memory-longterm/` | *What has been learned.* Durable notes by topic: how-tos, environment quirks, settled decisions. Index in `memory-longterm/README.md`. | Add a note when you learn something reusable; fix or delete notes that go stale. |

## Assets: three shelves

Cross-cutting files more than one task needs are stored **once**, on one of three shelves — never
copied into each task. Task folders in `flow/` hold only code, scripts, notes, and small config —
**never bulk data**.

- `assets/` — tracked in git: small shared files that are safe to publish (templates, reference data,
  diagrams).
- `assets-private/` — git-ignored: **precious or private and irreplaceable** (identity documents,
  scans, credentials, exports, personal records). Often a link to a synced private folder; always
  refer to it as `<repo>/assets-private`, never by its absolute target path.
- `assets-temp/` — git-ignored, local-only: **large and regenerable** (caches, downloaded dumps,
  build outputs, model weights). Safe to wipe at any time.

Large or binary task output goes under a path mirroring the task:
`assets-private/<program>/<project>/` or `assets-temp/<program>/<project>/`.
The test that settles placement: **could a script recreate it? Yes → `assets-temp/`. No →
`assets-private/`.**

## Fast paths

Pointers for questions that come up often, so a fresh session can answer without searching the tree.
Pointers only — the detail stays in the guide each row points at. Add a row only when a lookup proves
it earns one, and fix a row the moment its target moves.

| The question | Open this first |
|---|---|
| "What am I working on?" | `MEMORY.md`, then search `REGISTRY.md` |
| "How did we solve X last time?" | search `memory-longterm/README.md` and `memory-longterm/` |

## Rules (follow strictly)

1. **Follow the structure.** Real work goes in `flow/<program>/<project>/<task>/`. If a piece of work
   does not obviously fit, decide its program, project, and task *before* writing any file. For any
   substantial prompt, run the check-the-flow-first steps above before starting.
2. **Reuse; do not duplicate.** Before creating a program, project, task, or asset, search
   `REGISTRY.md` and the tree. If a fitting program or project exists, nest under it. If a
   near-identical task exists, extend it instead of forking a slightly different copy.
3. **Keep the registry honest.** Creating, renaming, moving, or removing a task updates its
   `REGISTRY.md` row in the same change. The registry always matches the tree.
4. **Tend memory carefully.** On task completion, re-read `MEMORY.md` and update it only if the gist
   changed. Put durable lessons in `memory-longterm/`, not in `MEMORY.md`.
5. **Prefer the smallest correct placement.** A one-off belongs in an existing project as a new task,
   not in a new program. Create a program only for a genuinely new long-running area.
6. **Search before saying "I don't know."** Before reporting that something is not recorded, search
   `REGISTRY.md`, `MEMORY.md`, and `memory-longterm/`. Report "not found" only after searching.
7. **No secrets in git.** Passwords, tokens, keys, identity numbers, and private documents go in
   `assets-private/` only. Never copy them into a tracked file, a commit message, or a log.
8. **Keep the mirrors identical.** Any change to this file goes into all four copies in the same edit
   (see the note at the top).

## Maintenance

- This file owns the **conventions and the structure contract**, not per-task detail. Task detail
  lives in each task's own `README.md`; do not copy it up here.
- When a program is added, renamed, or removed, reflect it here only if it changes the structure
  story; always reflect tasks in `REGISTRY.md`.
- Sources of truth: `REGISTRY.md` for *what exists*, `MEMORY.md` for *what is current*, this file for
  *how it is organized*.

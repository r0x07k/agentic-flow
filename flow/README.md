# flow

The **work tree**. Every piece of work lives here as `flow/<program>/<project>/<task>/`. Nothing sits
directly in `flow/` — the first level is always a program. The structure contract is in
[../AGENTS.md](../AGENTS.md); the index of every task is [../REGISTRY.md](../REGISTRY.md).

## The three levels

| Level | What it is | Examples |
|---|---|---|
| **program** | a broad, long-running area | `home`, `research`, `learning`, `soft`, `finance`, `writing` |
| **project** | a concrete deliverable inside a program | `home/garden`, `research/astronomy`, `soft/web` |
| **task** | one self-contained unit of work — holds the files | `home/garden/irrigation-controller` |

## Creating a task

1. Search [../REGISTRY.md](../REGISTRY.md) and this tree. If a fitting task exists, extend it.
2. Pick the program and project; reuse existing ones before creating new ones.
3. Create the task folder (`kebab-case`; a date prefix `YYYY-MM-DD_` only for point-in-time work
   such as a report or a single tax year).
4. Add its row to [../REGISTRY.md](../REGISTRY.md) in the same change.
5. Add a `README.md` once the task has more than a file or two (template below).

## What a task folder holds

Code, scripts, notes, reports, and small config — **never bulk data**. Large or binary output goes to
`../assets-private/<program>/<project>/` (irreplaceable) or `../assets-temp/<program>/<project>/`
(regenerable). Shared reusable files go to `../assets/` once, not into each task.

## Task `README.md` template

```markdown
# <task name>

<One or two sentences: what this is for and its current state.>

## How to run / where things are
<Commands, entry points, where the data and outputs live (by repo-relative path).>

## Files
| File | What it is |
|---|---|

## Conventions
<Anything a future session must know before changing this task.>
```

Guides are always `README.md` — never vendor-named files such as `CLAUDE.md` or `GEMINI.md` below
the repository root.

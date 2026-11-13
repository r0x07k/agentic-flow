# memory-longterm

**Long-term memory**: durable, reusable knowledge that stays useful across tasks and programs —
how-tos, environment quirks, gotchas, settled decisions, reference notes. Write here anything a future
session would otherwise waste time rediscovering.

> **Where it sits among the memory surfaces** (rules in [../AGENTS.md](../AGENTS.md)):
> - [../REGISTRY.md](../REGISTRY.md) — *what exists* (the task index).
> - [../MEMORY.md](../MEMORY.md) — *what is current* (short-term; changes as focus moves).
> - `memory-longterm/` (here) — *what has been learned* (does not change with the current task).

## Layout

```
memory-longterm/
├── README.md        this guide + the index of every note (below)
└── <topic>/         a stable area: git/, windows/, python/, esp32/, …
    └── <note>.md    one focused, self-contained note
```

Reuse an existing topic before inventing a new one.

## When to write a note

When you hit something **durable and reusable**: a fix that took real effort, a non-obvious
environment quirk, a decision worth keeping. Current-task status goes to [../MEMORY.md](../MEMORY.md);
task files go to `flow/`.

## Conventions

- **One note, one subject.** Lead with the symptom or the question it answers, then the steps or
  facts.
- **Keep it true.** When a note goes stale, fix or delete it. Cross-link related notes; do not
  duplicate.
- **Date time-sensitive facts** ("as of 2026-11", versions, prices) so staleness is visible.
- Tracked in git — **never put secrets here**; those belong in `../assets-private/`.
- **Search the index below before adding a note**, and add or update its row in the same change.

## Index

| Note | Answers |
|---|---|

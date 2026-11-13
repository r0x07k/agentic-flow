# Registry

One row per task — the master, searchable index of every unit of work under `flow/`.

> **Maintenance rule:** add a row the moment a task folder is created; keep its *What* current;
> update the row when a task is renamed, moved, or removed. This table must always match the tree on
> disk. **Search this table before creating anything new** — extend an existing task rather than
> forking a near-copy. The structure contract is in [AGENTS.md](AGENTS.md).

**Columns**

- **When** — creation time, `YYYY-MM-DD HH:MM` (local).
- **Path** — the task folder, `flow/<program>/<project>/<task>`.
- **What** — one line: what the task is and its current state. Rewrite it when the state changes.

**Example row** (not a real task):
`| 2026-03-14 18:20 | flow/home/garden/irrigation-controller | ESP32 drip timer on soil sensors; firmware done, enclosure open |`

| When | Path | What |
|---|---|---|

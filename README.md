# agentic-flow

A personal workspace that doubles as a memory. Every piece of work — a script, an investigation, a
small app, a write-up — gets a permanent, predictable home, and a few plain Markdown files keep track
of what exists, what is current, and what has been learned. It works the same with any AI coding
agent (Claude Code, Codex, Gemini, GitHub Copilot, Cursor, …) or with none at all.

## The scheme

**1. Work — `flow/<program>/<project>/<task>/`**

Three levels, always. A *program* is a broad area, a *project* is a concrete deliverable inside it, a
*task* is one unit of work and holds the actual files.

```
flow/
├── home/
│   ├── garden/irrigation-controller/          ESP32 drip timer driven by soil sensors
│   └── network/dns-ad-blocking/                Pi-hole setup notes and blocklists
├── research/
│   └── astronomy/variable-star-photometry/     light curves from a backyard telescope
├── learning/
│   └── koine-greek/vocabulary-deck/            spaced-repetition cards built from a word list
├── soft/
│   └── web/choir-rehearsal-scheduler/          small web app for rehearsal sign-ups
└── finance/
    └── taxes/2026-return/                      checklist and calculations for one tax year
```

**2. Memory — three files and one folder**

| | Answers | Example line |
|---|---|---|
| [REGISTRY.md](REGISTRY.md) | *What exists?* One row per task. | `2026-03-14 · flow/home/garden/irrigation-controller · ESP32 drip timer; wiring + firmware` |
| [MEMORY.md](MEMORY.md) | *What am I doing now?* A short, current gist. | "Irrigation controller: firmware works, waterproof enclosure still open." |
| [memory-longterm/](memory-longterm/README.md) | *What have I learned?* Durable notes by topic. | `memory-longterm/esp32/deep-sleep-wakeup.md` |

**3. Assets — three shelves**

| Shelf | In git? | What goes there | Example |
|---|---|---|---|
| [assets/](assets/README.md) | yes | small, shareable, reused files | a letterhead template, a parts list |
| [assets-private/](assets-private/README.md) | no — keep it backed up | private or irreplaceable | scanned tax forms, the raw telescope frames |
| [assets-temp/](assets-temp/README.md) | no — local only | large and regenerable | calibrated image stacks, downloaded datasets |

The test for the last two: *could a script recreate it?* Yes → `assets-temp/`. No → `assets-private/`.

## AI agents

The rules agents follow are in [AGENTS.md](AGENTS.md), kept as four identical copies so each tool
finds its own file:

| File | Read by |
|---|---|
| `AGENTS.md` | OpenAI Codex, Cursor, Windsurf, JetBrains Junie, the Copilot CLI, cloud agent and code review, and most other agents (Cline, Amp, Kiro, opencode, Warp, …); Aider with `read: AGENTS.md` in `.aider.conf.yml` |
| `CLAUDE.md` | Claude Code; also the Copilot CLI, cloud agent and code review, Cursor, and Windsurf |
| `GEMINI.md` | Gemini CLI and Gemini Code Assist; also the Copilot CLI, cloud agent and code review |
| `.github/copilot-instructions.md` | GitHub Copilot in every editor, the CLI, and on github.com; also Zed, which reads it before `AGENTS.md` |

Claude Code reads `AGENTS.md` only when there is no `CLAUDE.md`, so it loads one copy. In VS Code's
older Local chat mode, Copilot Chat would load three copies;
[.vscode/settings.json](.vscode/settings.json) turns two of them off there. Amazon Q Developer and Continue read none of these files; they use their own rules
folders.

Change one, change all four. To check they still match:

```
git diff --no-index AGENTS.md CLAUDE.md
git diff --no-index AGENTS.md GEMINI.md
git diff --no-index AGENTS.md .github/copilot-instructions.md
```

No output means identical. Every other guide in the repository is a plain `README.md`.

## Get your own private copy

Your copy will hold your notes and memory, so keep it private. **Do not use GitHub's Fork button:**
a fork of a public repository is always public. Make a separate private repository instead.

With the [GitHub CLI](https://cli.github.com/) (`gh`), in a terminal (`gh auth login` is needed only
once per machine):

```
gh auth login
git clone https://github.com/r0x07k/agentic-flow.git my-flow
cd my-flow
git remote rename origin upstream
gh repo create my-flow --private --source=. --remote=origin --push
```

Without the CLI: on github.com choose **New repository**, name it, select **Private**, and leave
*Add a README*, *.gitignore* and *license* unset (the repository must be empty). Then run, with
`<your-user>` replaced by your GitHub user name:

```
git clone https://github.com/r0x07k/agentic-flow.git my-flow
cd my-flow
git remote rename origin upstream
git remote add origin https://github.com/<your-user>/my-flow.git
git push -u origin main
```

`my-flow` is only an example name.

**Taking later improvements to this skeleton.** The `upstream` remote points here. To see what
changed and merge it:

```
git fetch upstream
git log --oneline main..upstream/main
git merge upstream/main
```

If the merge reports conflicts:
- `AGENTS.md` and its mirrors: resolve `AGENTS.md`, then copy it over `CLAUDE.md`, `GEMINI.md` and
  `.github/copilot-instructions.md` so the four stay identical.
- `MEMORY.md` and anything else that is yours: keep your version with `git checkout --ours <file>`.

Then `git add` the files and `git commit`. If you don't want updates, remove the remote with
`git remote remove upstream`.

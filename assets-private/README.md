# assets-private

**Git-ignored storage for precious, private, irreplaceable files**: identity documents, scans,
financial and medical records, credentials, personal exports, original photos or recordings, and
task output that must not be published. Only this `README.md` is tracked (see `../.gitignore`);
everything else stays off the git host.

> **Back it up.** Git does not protect anything here.
> - **Windows:** make this folder a junction to a synced private folder (OneDrive or another cloud
>   drive). From the repository root, in `cmd`:
>   1. `mkdir <synced-folder>\assets-private` (skip if it already exists)
>   2. `move assets-private\README.md <synced-folder>\assets-private\`
>   3. `rmdir assets-private`
>   4. `mklink /J assets-private <synced-folder>\assets-private`
>   5. `git status` must show no changes. Deleting a file here then deletes it from the cloud copy too.
> - **macOS / Linux:** keep this a real folder and point a backup or sync tool at it (Time Machine,
>   restic, rclone, Syncthing). Do not replace it with a symlink: git would see the README as deleted,
>   and committing the link would publish the absolute path of your cloud folder.

## Rules

- Refer to it as `<repo>/assets-private/...` (a repository-relative path) — **never hard-code the
  absolute target**, so scripts keep working if the link moves.
- Mirror the work tree: `assets-private/<program>/<project>/` for output of a task under
  `flow/<program>/<project>/`.
- Never copy anything from here into a tracked file, a commit message, or a log.
- Large but **regenerable** files do not belong here → [../assets-temp/](../assets-temp/README.md).
  The test: *could a script recreate it?* If yes, it goes to `assets-temp/`.

# assets-temp

**Git-ignored, local-only scratch** for large **regenerable** files: caches, downloaded datasets,
build outputs, intermediate results, sandbox databases, model weights. Only this `README.md` is
tracked (see `../.gitignore`). Nothing here is precious — it may be wiped at any time and is not
backed up.

## What belongs here

Anything a script can **recreate**: re-downloadable data, processed or calibrated copies of
originals, generated reports that can be re-run.

## What does not belong here

- Originals and anything irreplaceable → [../assets-private/](../assets-private/README.md).
  Example: raw telescope frames go to `assets-private/`; the calibrated stacks made from them go here.
- Small shareable files → [../assets/](../assets/README.md).

## Layout

Mirror the work tree when it helps: `assets-temp/<program>/<project>/<task>/`. No index — if a file
feels like it needs one, it probably belongs in `assets-private/`.

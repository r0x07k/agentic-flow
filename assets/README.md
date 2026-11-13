# assets

**Shared, version-controlled assets** — small files that more than one task uses and that are safe
to publish: templates, reference data, diagrams, logos, parts lists. Stored here **once**; tasks refer
to them by path instead of copying them.

## Layout

Group by kind or by area, whichever is clearer: `assets/templates/`, `assets/reference/`,
`assets/<program>/`. Each file name should say what it is.

## What does not belong here

- Anything private, personal, or irreplaceable → [../assets-private/](../assets-private/README.md).
- Anything large or regenerable → [../assets-temp/](../assets-temp/README.md).
- Files only one task uses → that task's folder under `../flow/`.

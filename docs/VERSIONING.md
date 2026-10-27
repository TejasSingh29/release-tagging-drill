# Versioning Policy

## 1. Semantic Versioning

All production releases follow `MAJOR.MINOR.PATCH`.

- **MAJOR:** Increment for incompatible API or behavior changes. Example: `v1.4.2` → `v2.0.0`.
- **MINOR:** Increment for backward-compatible functionality. Example: `v1.4.2` → `v1.5.0`.
- **PATCH:** Increment for backward-compatible bug fixes. Example: `v1.4.2` → `v1.4.3`.

After a major or minor increment, reset the lower-order components to zero as appropriate.

## 2. Tag Naming Convention

Production tags must use the exact format `vMAJOR.MINOR.PATCH`.

Example: `v1.5.0`.

Use lowercase `v`, numeric version components, and periods as separators. Do not use underscores, spaces, or informal labels such as `final` in stable release tags.

## 3. Annotated Release Tags

All production releases must use annotated Git tags. Annotated tags store a tagger, date, and release message, providing better auditability than lightweight tags.

Create a release tag with:

```bash
git tag -a v1.5.0 -m "Release 1.5.0: describe the shipped changes"
```

Verify the tag and its target commit with:

```bash
git show v1.5.0
git cat-file -t v1.5.0
```

The second command should report `tag` for an annotated tag.

## 4. Pre-release Convention

Release candidates and beta versions must include a pre-release suffix, such as `v1.5.0-beta.1` or `v1.5.0-rc.1`.

Pre-releases are ordered before their corresponding stable release. For example, `v1.5.0-rc.1` precedes `v1.5.0`. Increment the pre-release identifier for subsequent candidates, such as `v1.5.0-rc.2`.

Pre-release tags must not be treated as stable production releases unless explicitly approved by the release process.

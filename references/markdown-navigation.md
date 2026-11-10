# Markdown navigation

Mechanics for §6 of `AGENT.md`: Contents, Quick links, and anchors that work on GitHub without extensions.

## Contents vs. Quick links

- `Contents`: numbered list of main sections plus nested bullets for key subsections. Belongs near the top of substantial pages.
- `Quick links`: single pipe-separated line of the most-visited sections. Belongs after the intro on long pages. Complements Contents, never replaces it.

```markdown
## Contents
1. [Configuration sources](#configuration-sources)
2. [Loading order](#loading-order)
3. [Available options](#available-options)
   - [Output settings](#output-settings)
4. [Examples](#examples)

## Quick links
[Sources](#configuration-sources) | [Loading order](#loading-order) | [Options](#available-options) | [Examples](#examples)
```

## GitHub anchor slugs

GitHub derives the `#fragment` from the heading text:

1. Lowercase the heading.
2. Remove punctuation (keep letters, numbers, spaces, hyphens, underscores).
3. Replace spaces with hyphens.

| Heading | Anchor |
|---|---|
| `## Configuration sources` | `#configuration-sources` |
| `### Environment variables` | `#environment-variables` |
| `## API v2 (beta)` | `#api-v2-beta` |

Duplicate headings on one page get `-1`, `-2` suffixes — avoid duplicates instead of relying on this.

## The three link directions

```markdown
[Loading order](#loading-order)
[Architecture](architecture.md)
[Loading order](configuration.md#loading-order)
[CLI reference](reference/cli.md)
```

From inside `docs/reference/`, go up one level: `[Usage](../usage.md)`.

## Rules that prevent dead links

- Relative paths only; never hard-code the repository URL for internal pages.
- After renaming a heading, grep the repo for the old fragment and update every hit in the same change.
- After moving a file, grep for its old path and update the root README, the index, and all cross-page links.
- Meaningful labels (`[Loading order](…)`), never `here` or `click here`.

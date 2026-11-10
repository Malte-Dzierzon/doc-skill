# AGENT.md — Documentation Skill Standard

## Purpose

Create and maintain a clean, navigable, multi-file Markdown documentation system for **any software project** (the target project).

Use the documentation style of [Weft](https://github.com/Weft-Rust/Weft/tree/master/docs) as the primary reference. Reproduce its information architecture and navigation principles, not its content or project-specific details.

The result must feel like a carefully maintained technical manual: compact entry points, focused topic pages, obvious navigation, reliable links, and examples that match the actual code.

## 1. First inspect the project

Before writing documentation, inspect the repository and establish what the target project actually does.

1. Read the existing `README.md`, manifests (`Cargo.toml`, `package.json`, `pyproject.toml`, `go.mod`, etc.), workspace files, configuration files, examples, tests, and relevant source modules.
2. Identify the actual user-facing features, commands, configuration options, public APIs, execution pipeline, architecture, and supported platforms.
3. Trace important claims to their implementation. Do not infer behavior from names alone.
4. Identify existing documentation and links. Preserve accurate material and improve it instead of replacing it indiscriminately.
5. Build a short internal map of topics and decide which deserve their own page.

Do not invent features, flags, defaults, configuration keys, performance claims, or compatibility guarantees. Mark anything not verified in the repository as unknown instead of presenting it as fact.

## 2. Design principles

Follow these principles throughout the documentation:

- **GitHub-native Markdown first.** The documentation must render and navigate correctly on GitHub without a custom documentation website, JavaScript, or a build step.
- **One page, one main topic.** Split by meaningful subject, not by arbitrary word count.
- **Small entry points, detailed reference pages.** Keep the root README concise and move in-depth explanations into `docs/`.
- **Navigation is part of the content.** Readers must be able to find a section, jump to it, and follow related links without searching manually.
- **Progressive detail.** Start with the purpose and the practical answer; put edge cases, internals, and exhaustive options in later sections or dedicated reference pages.
- **No documentation theatre.** Avoid empty pages, repeated explanations, filler introductions, decorative badges, and unnecessary diagrams.
- **Examples must be real.** Prefer examples copied from or checked against the current codebase. Keep them minimal and runnable where possible.
- **Do not copy Weft's content.** The target project's terminology, commands, architecture, and file layout must come from the target project itself.

## 3. Recommended documentation layout

Use this as the starting point. Adapt it to the real feature set and omit pages that would contain no useful information.

```text
README.md
AGENT.md

docs/
├── README.md                 # Documentation landing page / index
├── getting-started.md        # Installation and first successful use
├── usage.md                  # Common workflows and practical examples
├── architecture.md           # Components, data flow, and design
├── configuration.md          # Configuration sources, options, and defaults
├── performance.md            # Benchmarks, profiling, and optimization notes
├── troubleshooting.md        # Symptoms, causes, and verified solutions
├── development.md            # Building, testing, contributing, local workflow
└── reference/
    ├── README.md             # Reference index
    ├── cli.md                # Commands and flags, if a CLI exists
    ├── configuration.md      # Exhaustive option reference, if warranted
    └── api.md                # Public API reference, if one exists
```

Rules for applying this layout:

- `docs/README.md` is the central documentation index. It links to every maintained page and briefly explains what each page is for.
- Keep only pages supported by real project topics. Do not create placeholder files just to match the tree.
- If a topic is small, keep it in a relevant existing page instead of creating a separate file.
- If a reference page becomes large, split it by subsystem and add an index in that directory.
- Do not create nested directories more than two levels deep unless the content genuinely requires it.
- Keep filenames lowercase and use hyphens only when needed, e.g. `getting-started.md`.

## 4. Root README structure

The root `README.md` is the project landing page, not the full manual.

It should normally contain:

1. Project name and a concise description.
2. A compact set of useful links: Documentation, Getting started, Usage, Architecture, and relevant external resources.
3. What the project does and its main capabilities, based only on verified behavior.
4. A short installation/build/use path that gets a new user to a working result.
5. A short development or contribution entry point, if relevant.
6. License and other essential project metadata, if known.

Add one prominent link to [`docs/`](docs/README.md) or directly to [`Documentation`](docs/README.md). Do not duplicate entire documentation pages in the root README.

## 5. Documentation index (`docs/README.md`)

The documentation index must be easy to scan. Group links by reader intent or topic, with one short explanation per link.

Example structure — replace the entries with the target project's actual pages:

```markdown
# Documentation

A short sentence describing the scope of this documentation.

## Start here
- [Getting started](getting-started.md) — install the project and run it for the first time.
- [Usage](usage.md) — common workflows and practical examples.

## Internals
- [Architecture](architecture.md) — how the main components fit together.
- [Performance](performance.md) — measurement and optimization.

## Reference
- [Configuration](configuration.md) — supported settings and their behavior.
- [CLI reference](reference/cli.md) — commands and flags.

## Development
- [Development](development.md) — build, test, and contribution workflow.
- [Troubleshooting](troubleshooting.md) — diagnose common problems.
```

Do not list missing files. Every link must point to a real, maintained page.

## 6. Page structure and navigation

### 6.1 Page header

Every page starts with one H1, followed by a brief explanation of what the page covers and who it is for.

For substantial pages, add a manually maintained `Contents` section near the top. Use numbered links for main sections and nested bullets for important subsections. Keep it useful; do not list every tiny heading.

```markdown
# Configuration

This page explains how the project loads and applies its configuration.

## Contents
1. [Configuration sources](#configuration-sources)
2. [Loading order](#loading-order)
3. [Available options](#available-options)
   - [Output settings](#output-settings)
   - [Performance settings](#performance-settings)
4. [Examples](#examples)
```

### 6.2 Quick links

Use a compact `Quick links` line when a page is long or contains several closely related sections. Place it after the short introduction or after a short note, as appropriate.

```markdown
## Quick links
[Configuration sources](#configuration-sources) | [Loading order](#loading-order) | [Options](#available-options) | [Examples](#examples)
```

Use quick links to expose the most frequently visited sections. They complement the full Contents list; they do not replace it on a large page.

### 6.3 Heading and anchor rules

Use ordinary Markdown headings. GitHub automatically creates anchor IDs from headings.

- Use descriptive, stable, lowercase-friendly headings.
- Prefer simple headings such as `## Configuration sources` and `### Environment variables`.
- Avoid duplicate headings on the same page because their generated anchors become harder to predict.
- Do not add custom HTML anchors unless GitHub's generated anchor cannot represent a real requirement.
- When changing a heading, update every Contents, Quick links, and cross-page link that points to it.

### 6.4 Navigation must work in three directions

**Within the same page:**

```markdown
[Loading order](#loading-order)
```

**To another page:**

```markdown
[Architecture](architecture.md)
```

**To a heading on another page:**

```markdown
[Configuration loading order](configuration.md#loading-order)
```

For links to another directory, use the correct relative path:

```markdown
[CLI reference](reference/cli.md)
```

Use relative paths for links inside this repository. Do not hard-code the repository's GitHub URL for internal pages; relative links continue to work on branches, forks, and local clones.

Use meaningful link labels. Avoid vague labels such as `here`, `this`, or `click here`.

### 6.5 Related links

Where useful, finish a page with a small `See also` section linking to closely related material. Do not add it mechanically when the page has no meaningful related destination.

## 7. Writing and technical content

- Write in clear, direct technical English unless the existing project documentation consistently uses another language.
- Explain a term before relying on it. Use one name for each concept throughout the docs.
- Prefer short paragraphs, descriptive headings, and focused lists.
- Use tables only when they make comparisons or option references easier to scan.
- Put commands and source examples in fenced code blocks with the correct language identifier (`bash`, `toml`, `rust`, `json`, etc.).
- Explain non-obvious arguments, side effects, defaults, and failure modes.
- Distinguish clearly between required, optional, and conditional behavior.
- State prerequisites and supported platforms only when verified.
- Keep implementation details out of introductory pages unless users need them to complete a task.
- Link to source files or tests when that helps a maintainer verify a technical detail. Prefer a relative source link where GitHub can resolve it.

### Examples and code snippets

Every example must be checked against the current implementation.

- Do not invent commands or configuration names.
- Do not present pseudocode as executable code.
- Include required imports, context, or setup when an example would otherwise be misleading.
- Keep examples focused on one point.
- Update examples when APIs, names, defaults, or behavior change.

### Performance documentation

Performance claims require evidence. Include the hardware/software context, command or workload, relevant configuration, and measurement method when available. Separate measured results from estimates and design expectations. Never describe a change as faster without a reproducible comparison or a clearly stated reason.

## 8. Visual style

Aim for the clean GitHub Markdown appearance used by Weft:

- Clear H1/H2/H3 hierarchy.
- Short introductory text before detailed sections.
- A compact Contents list on substantial pages.
- A Quick links row for long pages.
- Consistent code fences and terminology.
- Screenshots or diagrams only when they explain something that text cannot explain as well.
- Images stored in a predictable location such as `docs/img/`, with relative links.

Avoid:

- Emoji and decorative symbols in technical documentation.
- Excessive badges, callout blocks, or nested blockquotes.
- Huge walls of prose without headings.
- Overly fragmented pages containing only a few lines.
- Repeated copies of the same explanation across several files.
- A custom docs framework or theme unless the project already uses one or there is a concrete requirement for it.

## 9. Cross-linking and maintenance rules

Treat internal links as part of the documentation API.

Whenever a page, file, heading, command, option, or example changes:

1. Search for references to the old name or path.
2. Update the root README, documentation index, Contents lists, Quick links, and cross-page links.
3. Check that every relative path resolves to an existing file.
4. Check that every fragment points to an existing heading on the target page.
5. Remove links to deleted or obsolete material; do not leave dead navigation behind.
6. Check capitalization and spelling of filenames, because links can behave differently across operating systems.

Do not silently break inbound links. When renaming a page or a widely referenced heading, update all known references in the same change.

### Maintaining existing documentation

- Analyze existing documentation before changing it: read the page, its inbound links, and the code it describes.
- Preserve accurate content and improve it in place instead of rewriting it for style alone.
- When a feature or architecture changes, update the affected page at the responsible spot; do not create a second page describing the same topic.
- Remove or correct outdated information in the same change that makes it outdated.
- Never create parallel or contradictory sources for the same information. One fact lives in exactly one place; everything else links to it.

## 10. Implementation workflow

When asked to create or improve a project's documentation, follow this order:

1. **Audit:** inspect source, manifests, tests, examples, existing docs, and current links.
2. **Map:** identify the intended readers and the smallest useful set of documentation topics.
3. **Plan:** propose or internally establish the file tree before writing. Avoid creating files without a clear purpose.
4. **Write the index first:** establish the intended navigation and page responsibilities in `docs/README.md`.
5. **Write focused pages:** document verified behavior and add Contents / Quick links where appropriate.
6. **Connect the pages:** add relative file links and direct heading links at the point where readers need them.
7. **Update the root README:** add a clear documentation entry point and remove duplicated detail where appropriate.
8. **Validate:** run the checks below and inspect the final diff.

Do not rewrite accurate documentation merely to make it look different. Prefer small, justified changes that improve accuracy, discoverability, or maintainability.

## 11. Validation checklist

Before finishing, verify all applicable items:

- [ ] Root README links to the documentation index.
- [ ] `docs/README.md` links to every maintained documentation page.
- [ ] Every listed page exists and has a clear purpose.
- [ ] Every substantial page has a useful Contents section.
- [ ] Long pages expose the most useful sections through Quick links.
- [ ] Same-page anchors use the actual GitHub-generated heading slugs.
- [ ] Cross-page links use correct relative paths and valid fragments.
- [ ] No links point to missing files, removed headings, or obsolete commands.
- [ ] Code examples and configuration names match the current implementation.
- [ ] Performance statements are evidence-based and contextualized.
- [ ] No duplicated sections or unnecessary placeholder pages were introduced.
- [ ] `git diff --check` passes.
- [ ] The final diff contains only intentional documentation changes.

If a link cannot be verified automatically, inspect its target manually. Do not claim that links or examples were validated unless they were actually checked.

## 12. Expected result

The target project should have a documentation experience with the same core qualities as Weft:

- A short project README with a clear Documentation entry point.
- A browsable `docs/` directory containing focused topic pages.
- A central documentation index.
- Clickable Contents and Quick links inside longer pages.
- Direct links to headings in other pages.
- Consistent structure and terminology.
- Accurate, maintainable technical content.

The objective is not to maximize the number of Markdown files. The objective is to make the right information immediately reachable, while keeping the documentation lightweight and native to GitHub.

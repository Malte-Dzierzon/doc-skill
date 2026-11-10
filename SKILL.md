# doc-skill

An agent skill for creating, improving, and maintaining professional technical documentation for any software project.

## When to use this skill

Use this skill when the user asks you to:

- Create documentation for a software project from scratch.
- Improve, restructure, or clean up existing documentation.
- Add a new documentation page to an existing `docs/` system.
- Fix documentation navigation, links, or outdated content.
- Review documentation quality against a defined standard.

Do not activate this skill for writing a project README alone — that is covered by a readme template, not by this skill.

## Binding rules

The binding documentation standard is [`AGENT.md`](AGENT.md). Follow it in full. Nothing in this file or in `references/` overrides it; on conflict, `AGENT.md` wins.

## Operating loop

1. **Audit** the target project: source, manifests, tests, examples, existing docs, current links. Trace claims to implementation.
2. **Map** readers and topics; decide the smallest useful set of pages.
3. **Plan** the file tree before writing; skip pages with no real content.
4. **Write** the documentation index (`docs/README.md`) first, then focused pages with Contents and Quick links where appropriate.
5. **Connect** pages with relative links and heading anchors; update the root README entry point.
6. **Validate** with the checklist in `AGENT.md` §11 plus [`references/quality-checklist.md`](references/quality-checklist.md).

## References

Consult as needed; each covers one operational detail:

- [`references/documentation-structure.md`](references/documentation-structure.md) — which pages to create, merge, or omit.
- [`references/markdown-navigation.md`](references/markdown-navigation.md) — Contents, Quick links, and anchor mechanics.
- [`references/quality-checklist.md`](references/quality-checklist.md) — copy-paste verification checklist.

## Rules

- GitHub-native Markdown only: no docs framework, no build step, no custom site.
- Document verified behavior only. Never invent flags, defaults, keys, or performance claims.
- One fact lives in exactly one place; everything else links to it.
- Preserve accurate existing content; improve in place instead of rewriting for style.

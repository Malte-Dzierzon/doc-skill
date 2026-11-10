# Documentation structure

Decision aid for §3 of `AGENT.md`. It adds no new rules; it helps you choose the smallest useful page set.

## Start from the default tree

```text
docs/
├── README.md              # index, always required
├── getting-started.md     # installation + first success
├── usage.md               # common workflows
├── architecture.md        # components, data flow
├── configuration.md       # options and defaults
├── troubleshooting.md     # symptoms → verified fixes
├── development.md         # build, test, contribute
├── performance.md         # only with real measurements
└── reference/             # only if exhaustive detail is warranted
```

## Create, merge, or omit

| Project reality | Decision |
|---|---|
| CLI with flags | Keep `reference/cli.md`; merge small config into `configuration.md`. |
| Library with public API | Keep `reference/api.md`; merge usage examples into `usage.md`. |
| Single config file, few keys | No `reference/` directory; one `configuration.md` is enough. |
| No measurable perf work | Omit `performance.md` entirely, including from the index. |
| Small project (< 3 topics) | Document in root README + one or two `docs/` pages; skip the rest. |
| Large subsystem (auth, plugins) | New focused page (e.g. `authentication.md`), linked from the index. |

## Smells

- A page under ~15 lines that will never grow → merge it into its neighbor.
- Two pages answering the same question → keep one, link from the other.
- A `reference/` directory with a single short file → fold it into the parent page.
- Nesting deeper than `docs/reference/*.md` → flatten unless the content genuinely requires it.

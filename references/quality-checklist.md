# Quality checklist

Copy-paste verification for §11 of `AGENT.md`. Check all applicable items before finishing documentation work.

## Navigation

- [ ] Root README links to the documentation index.
- [ ] `docs/README.md` links to every maintained page, with one-line purpose each.
- [ ] Every listed page exists; no links to missing files or removed headings.
- [ ] Substantial pages have a Contents section; long pages add Quick links.
- [ ] Same-page anchors match GitHub-generated slugs; cross-page links use correct relative paths and valid fragments.

## Content

- [ ] Each page has one H1, a scope sentence, and exactly one main topic.
- [ ] Examples and configuration names verified against current source, tests, or manifests.
- [ ] No invented flags, defaults, keys, platforms, or compatibility claims.
- [ ] Performance statements carry hardware context, workload, and method; estimates labeled as estimates.
- [ ] Terminology consistent across pages; terms explained before use.
- [ ] No duplicated explanations, placeholder pages, or filler sections.

## Maintenance

- [ ] Existing accurate content preserved and improved in place.
- [ ] Changed headings, files, commands, or options updated in README, index, Contents, Quick links, and cross-page links.
- [ ] No parallel or contradictory sources for the same fact.
- [ ] `git diff --check` passes; diff contains only intentional documentation changes.

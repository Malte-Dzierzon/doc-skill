<div align="center">

# doc-skill

**documentation · navigation · maintainability**

![](https://img.shields.io/github/last-commit/Malte-Dzierzon/doc-skill?style=flat-square&color=16242d&labelColor=070e15)
![](https://img.shields.io/badge/skill-agent--ready-0e0e43?style=flat-square&labelColor=070e15)
![](https://img.shields.io/badge/docs-weft--style-16242d?style=flat-square&labelColor=070e15)

</div>

---

Agent skill that teaches an AI agent to create, improve, and maintain professional technical documentation for any software project.

## Skill stack

| Layer | Software |
|---|---|
| Entry point | [`SKILL.md`](SKILL.md) |
| Binding standard | [`AGENT.md`](AGENT.md) |
| Navigation mechanics | [`references/markdown-navigation.md`](references/markdown-navigation.md) |
| Structure decisions | [`references/documentation-structure.md`](references/documentation-structure.md) |
| Verification | [`references/quality-checklist.md`](references/quality-checklist.md) |

---

## Quick start

Point your agent at `SKILL.md` and give it a documentation task for any project.

```bash
git clone https://github.com/Malte-Dzierzon/doc-skill.git
```

Special cases:

- No install step exists: the skill is markdown only, the agent reads it directly.
- Pin a version by checking out a tag or commit hash before use.

---

## Using the skill

<details>
<summary><b>Create docs</b></summary>

- Agent audits source, manifests, tests, and examples, then writes `docs/README.md` first and focused topic pages after — see [`AGENT.md`](AGENT.md#10-implementation-workflow).

</details>

<details>
<summary><b>Maintain docs</b></summary>

- Agent analyzes existing pages before changing them, updates links in the same change, and never creates parallel sources — see [`AGENT.md`](AGENT.md#9-cross-linking-and-maintenance-rules).

</details>

---

## References

<details>
<summary><b>Reference files</b></summary>

- `references/` — one operational detail per file: structure decisions, anchor mechanics, verification checklist.

</details>

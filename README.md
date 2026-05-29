# pya

`pya` is a lightweight collection of Codex-compatible skills for frontend design, browser automation, program planning, and web application testing.

This repository is intended to keep reusable skill instructions organized, reviewable, and easy to install selectively. Each skill lives in its own directory and should be loaded only when it is relevant to the current task.

## Skills

| Skill | Purpose |
| --- | --- |
| `frontend-design` | Guides production-grade frontend interface design with strong visual direction and polished implementation details. |
| `playwright` | Provides CLI-first browser automation workflows using Playwright for navigation, interaction, screenshots, and UI debugging. |
| `pya-is-skills` | Helps turn rough software ideas into practical program designs, architectures, modules, workflows, and implementation plans. |
| `webapp-testing` | Supports local web application testing with Playwright scripts, screenshots, browser logs, and server lifecycle helpers. |

## Repository Structure

```text
.
|-- frontend-design/
|   |-- SKILL.md
|   `-- LICENSE.txt
|-- playwright/
|   |-- SKILL.md
|   |-- agents/
|   |-- assets/
|   |-- references/
|   `-- scripts/
|-- pya-is-skills/
|   |-- SKILL.md
|   `-- agents/
|-- webapp-testing/
|   |-- SKILL.md
|   |-- examples/
|   `-- scripts/
`-- README.md
```

## Usage

Clone the repository:

```bash
git clone https://github.com/ppppp-2005/pya.git
```

Then copy or link only the skill directories you want to use into the skill directory supported by your local environment. Review each `SKILL.md` before enabling it so you understand when it should be applied and what assumptions it makes.

## Maintenance Guidelines

- Keep each skill focused on one clear workflow or domain.
- Update the relevant `SKILL.md` when behavior, prerequisites, or usage patterns change.
- Keep examples and helper scripts close to the skill that depends on them.
- Avoid adding broad instructions that affect unrelated tasks.
- Review included license and notice files before redistributing skill content.

## Contributing

Issues and pull requests are welcome. For larger changes, describe the use case, expected behavior, affected skill directory, and any compatibility concerns.

## License

Some skill directories include their own license or notice files. Review the files in each directory before reuse or redistribution.

# AI Agents

Experienced AI Agents at Code Quality Review and Code Security Review for using in Cursor IDE.

## 💡 Overview

This repository is a Cursor project: agents, skills, rules, and commands for reviewing other codebases and for writing the root `README.md`. The public repository is [eduBortotowski/ai_agents](https://github.com/eduBortotowski/ai_agents).

The principal author is [Eduardo Bortowski](https://github.com/eduBortotowski).

It also includes a documentation agent. `technical-docs-writer` creates or updates only the root `README.md`, using `.cursor/skills/readme-generation/references/readme-template.md`.

## ✨ Features

- **Security review** (`security-reviewer`, read-only). Follows `project-recon`, `secrets-and-repo-hygiene`, and `vulnerability-review`. Reports vulnerabilities, secrets, environment values fixed in code, files that should stay out of Git, and risks in Docker and CI/CD. Checklists live under `.cursor/skills/vulnerability-review/references/` (frontend, backend/API including Django/DRF, microservices/Docker/CI/CD) and follow the OWASP Top 10.
- **Code quality review** (`code-quality-reviewer`, read-only). Follows `project-recon` and `code-quality-review`. References under `.cursor/skills/code-quality-review/references/` cover Python/Django, TypeScript/Angular, SQL, and other languages.
- **README generation** (`technical-docs-writer`). Writes only `/README.md` at the project root.
- **Slash commands** in `.cursor/commands/`: `/security-review` and `/generate-readme`.
- **Rules** in `.cursor/rules/`: security baseline (always on), README conventions, Python/Django, TypeScript/Angular, and Docker/CI/CD.

## 👩‍💻 Tech Stack

Cursor project configuration only. The tree contains Markdown skills, `.mdc` rules, and agent and command definitions. There is no dependency manifest, Dockerfile, Compose file, or CI workflow in this repository.

Python, Django, TypeScript, Angular, SQL, Docker, and CI/CD appear as review targets inside the skills and rules. They are not runtimes of this repository.

## 📦 Getting Started

Open this repository in Cursor. The files under `.cursor/` are then available as agents, skills, rules, and commands.

### 🚀 Prerequisites

- Cursor IDE

## 📖 Usage

### `/security-review`

Defined in `.cursor/commands/security-review.md`. Starts `security-reviewer` and `code-quality-reviewer` in parallel. The scope is the folder, module, or diff given after the command; with no scope, the command uses the whole project. It does not change files. The result is one report: executive summary, security findings, secrets and repository hygiene, quality findings, and a prioritized action list.

### `/generate-readme`

Defined in `.cursor/commands/generate-readme.md`. Starts `technical-docs-writer` to create or update the root `README.md`. No other file is changed.

### Agents

| Agent | File | Writes |
|---|---|---|
| `security-reviewer` | `.cursor/agents/security-reviewer.md` | No (`readonly: true`) |
| `code-quality-reviewer` | `.cursor/agents/code-quality-reviewer.md` | No (`readonly: true`) |
| `technical-docs-writer` | `.cursor/agents/technical-docs-writer.md` | Root `README.md` only |

### Skills

| Skill | Path |
|---|---|
| `project-recon` | `.cursor/skills/project-recon/SKILL.md` |
| `secrets-and-repo-hygiene` | `.cursor/skills/secrets-and-repo-hygiene/SKILL.md` |
| `vulnerability-review` | `.cursor/skills/vulnerability-review/SKILL.md` |
| `code-quality-review` | `.cursor/skills/code-quality-review/SKILL.md` |
| `readme-generation` | `.cursor/skills/readme-generation/SKILL.md` |

### Rules

| Rule | When it applies |
|---|---|
| `.cursor/rules/security-baseline.mdc` | Always (`alwaysApply: true`) |
| `.cursor/rules/readme-conventions.mdc` | `**/README.md` |
| `.cursor/rules/python-django-quality.mdc` | `**/*.py` |
| `.cursor/rules/angular-typescript-quality.mdc` | `**/*.ts`, `**/*.html` |
| `.cursor/rules/docker-infra-security.mdc` | `Dockerfile`, Compose files, `.github/workflows/**` |

## 📜 License

Personal use and study. There is no `LICENSE` file in the repository.

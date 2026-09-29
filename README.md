# rbt-devops-l1 — DevOps Engineer track (OPS-L1)

My work for the BISTEC Academy role-based training **DevOps Engineer** track: six modules, each a
self-contained project built spec-first with [specclaw](https://github.com/Jayzilva/specclaw)
(teaching mode on), shipped as one reviewed pull request, and written up publicly.

Carry-through app: BISTEC Mart (extended across modules).

## Modules

| ID | Module | Scheduled | Headline target | Status | PR | Video | Site |
|---|---|---|---|---|---|---|---|
| OPS-L1-M01 | Linux, Git & CI | Sun 11 Oct 2026 | green CI pipeline | Not started | – | – | – |
| OPS-L1-M02 | Containerization with Docker | Wed 14 – Thu 15 Oct 2026 | small, scanned images | Not started | – | – | – |
| OPS-L1-M03 | Kubernetes Fundamentals | Wed 21 – Thu 22 Oct 2026 | Helm release | Not started | – | – | – |
| OPS-L1-M04 | Infrastructure as Code | Mon 26 – Tue 27 Oct 2026 | multi-env IaC | Not started | – | – | – |
| OPS-L1-M05 | Observability | Mon 2 – Tue 3 Nov 2026 | dashboards + alerts | Not started | – | – | – |
| OPS-L1-M06 | End-to-End CI/CD (capstone) | Mon 9 – Tue 10 Nov 2026 | canary + rollback | Not started | – | – | – |

A module is done only when its PR is approved. Status values: Not started, Ready, Studying, Building,
Verifying, In review, Approved. A title becomes a link when its folder is created.

## How this repo works

- **One folder per module**, created on its start day with `node tools/start-module.mjs mNN`
  (or `/start-module mNN` in Claude Code at the repo root). Each folder has its own `CLAUDE.md`,
  `.claude/` rules and skills, `memory/`, `.specclaw/` and docs, so it works on its own:
  `cd mNN-* && claude`.
- **Spec-driven**: propose → teach → plan → build → verify → pr, one specclaw change per module.
- **Learning first**: teaching mode briefs unfamiliar concepts and hands design decisions to me.
- **Review**: PR titled `<MODULE-ID> <Title>`, self-scored against the rubric; reviewer: To confirm.
  After approval: merge, tag `<module-id>-v1`.

## Connected content

**Site: <https://jayzilva.github.io/rbt-devops-l1/>**, published from `main` by `.github/workflows/pages.yml`.

Every module links three ways: code and PR here ↔ its page on the site (write-up, build log,
study notes, syllabus guide) ↔ a NotebookLM video on YouTube. Links live in the table above and
in each module's README.

## Publishing

Academy material is confidential and never committed (`.academy/` and `*/academy/` are
gitignored). Only what each module's `mkdocs.yml` publishes (write-up, build log, notes, resources, syllabus)
is public; the Pages workflow runs the confidentiality check before every build.

- [ ] Written OK from the academy owner to publish build logs and videos (date, who):

## Setup after a fresh clone

    ACADEMY_PASSWORD=... node tools/fetch-academy.mjs      # decrypt track pages into .academy/
    node tools/start-module.mjs m01 --refresh-academy     # restore a module's academy/ files

Requires Node 18+. Pandoc is optional (better Markdown). Claude Code picks up the specclaw
plugin from each module's `.claude/settings.json`.

Preview the site locally:

    pip install mkdocs-material
    node tools/build-site.mjs              # whole track into site/
    cd m01-* && python -m mkdocs serve     # one module, live reload

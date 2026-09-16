# Codex Local Skills

A curated collection of Codex skill definitions adapted for practical software
engineering workflows. The repository focuses on reusable guidance for clear
communication, complete deliverables, collaborative development, expressive
frontend work, minimal safe changes, and authorized security-analysis routing.

## Included skills

- **caveman** — optional response compression that preserves technical detail,
  evidence, uncertainty, and safety information.
- **full-output-enforcement** — keeps requested deliverables complete without
  replacing implementation with placeholders or fabricated progress.
- **gpt-taste** — supports distinctive marketing and portfolio interfaces with
  editorial typography and purposeful motion when the brief calls for it.
- **multi-agent-team** — coordinates bounded parallel work and integrates
  results without inventing agents or review outcomes.
- **ponytail** — favors the smallest safe implementation while preserving
  validation, accessibility, security, and error handling.
- **reverse-skill-router** — routes authorized reverse-engineering and
  security-analysis work to an appropriate specialist workflow.

Each skill is available under `skills/<skill-name>/SKILL.md`.

## Design principles

- Follow the user's intent, the existing architecture, and the project's
  established conventions.
- Prefer simple, maintainable changes, but do not remove necessary validation,
  accessibility, security controls, or error handling.
- Keep claims evidence-based: do not fabricate tool output, agent activity,
  test results, or project metrics.
- Treat security-related guidance as authorization-bound and scope-sensitive.
- Keep machine-specific state, credentials, logs, and local backup files out of
  the repository.

## Usage

Use a selected `SKILL.md` as a Codex skill entrypoint and install it through the
skill loader supported by your Codex-compatible environment. The skills are
intended to be composable: use only the guidance relevant to the current task
and let explicit user requirements take precedence.

## Project status

This is a newly published collection of locally maintained adaptations. Public
usage metrics are not yet established; the initial release is intended to make
the workflow guidance transparent, reviewable, and reusable.

## Scope and attribution

These files are community-maintained adaptations and are not an official
OpenAI product. Review the licensing and attribution requirements of any
upstream material before redistributing or modifying the skills further.

Only the current `SKILL.md` files and this README are included. Local backup
files and machine-specific state are intentionally excluded.

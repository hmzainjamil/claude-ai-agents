# Claude AI Agents

A library of agent role definitions for Claude Code workflows. The repository's `main` tree checked on 2026-10-02 contains 210 agent definition files: 209 Markdown files and one YAML file. These are instruction files, not 210 independently running services or verified autonomous agents.

## At a glance

| Item | Evidence |
|---|---|
| Content | Role and workflow instruction files at the repository root |
| Inventory | 210 definition files in the checked Git tree on 2026-10-02 |
| Runtime | Not included or verified by this repository |
| Setup | No repository-wide installer or package manifest found in the inspected tree |
| Verification | No agent execution or tests were run for this documentation update |

## Browse and use

Agent files are named by role, for example `engineering-code-reviewer.md`, `design-ux-researcher.md`, and `testing-api-tester.md`. Browse the [repository file list](https://github.com/hmzainjamil/claude-ai-agents) and open the individual definition that fits your task.

Read the complete instruction file before adopting it. Check any named tools, models, MCP servers, skills, paths, and external services against your environment. A role file can describe a workflow without implementing or enabling it.

For navigation and maintenance guidance, see the [documentation index](docs/README.md).

## Scope and limits

This repository contains role prompts and related instruction text. It does not establish that:

- a named agent runtime is installed or callable
- a listed tool or integration is available
- parallel execution, routing, memory, or automation is configured
- any output has passed tests or a domain review

Do not infer performance, cost, safety, or production claims from the number of files.

## Safe adaptation

Copy or adapt only reviewed definitions into a compatible Claude Code setup. Back up existing configuration first. Keep credentials and personal settings outside the repository. Before enabling automation, review its tool permissions and external side effects.

## Maintenance

Update this README when file format or repository purpose changes. If changing the file inventory count, derive it from the Git tree and include the checked date. Record validation only after running it in a named environment.

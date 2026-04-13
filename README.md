# ultradev

Practical skills that help developer agents do high-quality software work.

Works with Claude Code, Codex, Cursor, and any agent that reads SKILL.md.

## Install

```bash
npx skills add cosmtrek/ultradev
```

To install a single skill instead of all:

```bash
npx skills add cosmtrek/ultradev/simplify-changes
```

## Skills

| Skill | Description |
|-------|-------------|
| [simplify-changes](simplify-changes/) | Review changed code for reuse, quality, and efficiency, then fix issues found |

## Usage

After installation, invoke a skill by name in your agent:

```
/simplify-changes
```

Or ask the agent to use it:

> run simplify-changes on my current changes

## Repository Structure

Each skill lives in its own directory with a `SKILL.md` file:

```text
ultradev/
  <skill-name>/
    SKILL.md
```

## Scope

This repository is focused on skills for software development work, including:

- code quality and cleanup
- implementation workflows
- debugging and verification
- refactoring and maintainability
- testing and release readiness

Each skill should be narrowly scoped, operational, and useful in real
development workflows. If a proposed skill does not clearly improve software
quality or developer effectiveness, it probably does not belong here.

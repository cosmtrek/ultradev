# ultradev

`ultradev` is a repository of skills focused on helping developer agents do
high-quality software work.

The goal of this repo is not to collect generic prompts. It is to curate
practical, reliable skills that help agents:

- make better engineering decisions
- simplify and strengthen existing code
- validate changes before claiming completion
- build and ship higher-quality software

Each skill should be narrowly scoped, operational, and useful in real
development workflows. Prefer skills that improve correctness, maintainability,
testing discipline, and delivery quality.

## Scope

This repository is focused on skills for software development work, including:

- code quality and cleanup
- implementation workflows
- debugging and verification
- refactoring and maintainability
- testing and release readiness

## Structure

This is a multi-skill repository.

Each skill lives in its own directory and is defined by a `SKILL.md` file:

```text
ultradev/
  <skill-name>/
    SKILL.md
```

## Repository Direction

Skills in this repository should help developer agents produce software that is:

- correct
- maintainable
- well-verified
- production-ready

If a proposed skill does not clearly improve software quality or developer
effectiveness, it probably does not belong here.

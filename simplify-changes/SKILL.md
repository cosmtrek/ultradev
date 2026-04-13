---
name: simplify-changes
description: >
  Review the current task's code changes for reuse, code quality, and
  efficiency. Fix worthwhile issues directly, then run appropriate verification.
---

# Simplify Changes

Review the current task's code changes for reuse, code quality, and
efficiency. Fix worthwhile issues directly, then run appropriate
verification.

## When to use

Use this skill only when the user explicitly asks for `simplify-changes`,
asks to use this exact skill, or invokes `/simplify-changes`.

Do not use this skill for:

- generic requests like "simplify this" or "clean this up" unless the user
  explicitly names this skill
- first-pass implementation of a feature
- broad architectural redesign unrelated to the current task
- code review requests where the user wants findings only and does not want edits

## Instructions

### Phase 1: Determine review scope

Identify the review scope before doing anything else.

1. If the current task already established which files were changed, review
   only those files.
2. Otherwise, inspect git state and use the smallest relevant diff:
   - if there are staged changes, review staged changes and unstaged
     changes in the same files
   - if the task scope is unclear, review all current local changes
3. If there are no git changes, ask the user which files to review.

Rules:

- prefer the smallest valid review scope
- do not clean up unrelated dirty-worktree files
- before launching reviewers, form a short internal summary of:
  - changed files
  - main purpose of each change
  - any files that appear unrelated and should be skipped

### Phase 2: Launch reviewers

Launch up to three review agents in parallel if that is available and
worthwhile. If parallel agents are unavailable, or the diff is small
(three or fewer files, under ~200 lines), do the review yourself in one
pass.

Give each reviewer:

- the scoped file list
- a concise summary of the change intent
- only the relevant diff or file excerpts they need

Do not blindly send the full diff to every reviewer if the change is large.

#### Reviewer 1: Reuse

Look for places where new code should reuse existing helpers, utilities,
abstractions, shared types, constants, or adjacent patterns.

Flag:

- duplicated helper logic
- hand-rolled utilities that already exist
- new types or constants that overlap existing ones
- local one-off code that should call a shared function instead

#### Reviewer 2: Quality

Look for maintainability and design problems.

Flag:

- redundant or derivable state
- parameter sprawl
- copy-paste variants that should be unified
- abstraction leaks
- stringly-typed logic where structured types or constants already exist
- unnecessary wrapper layers (e.g. JSX wrappers, redundant containers,
  pass-through functions)
- comments that explain obvious WHAT instead of non-obvious WHY

#### Reviewer 3: Efficiency

Look for performance and execution-cost issues.

Flag:

- repeated work or duplicate I/O
- missed concurrency opportunities
- hot-path bloat
- unconditional no-op state or store updates
- existence pre-checks before doing the real operation
- memory leaks or missing cleanup
- overly broad reads or scans

### Phase 3: Normalize findings

Aggregate all findings before editing.

For each finding:

- include file and line reference when possible
- state the concrete issue in one sentence
- skip duplicates
- skip weak or low-value findings without debate
- order remaining findings by impact: bugs first, then correctness issues,
  then clarity improvements

Only fix issues that are both:

- likely correct
- worth the added code churn

Prefer small, local improvements over speculative refactors.

### Phase 4: Apply fixes

Make the fixes directly.

Rules:

- preserve existing behavior unless the finding is a real bug
- do not refactor unrelated code
- prefer existing local patterns over introducing new abstractions
- if multiple findings suggest the same fix, implement it once cleanly
- do not commit changes — leave them for the user to review

### Phase 5: Verify

Run the narrowest appropriate verification for the files you changed.

Prefer:

- targeted tests first
- then lint or typecheck for affected code if appropriate

Do not claim verification ran if it did not. If no meaningful verification
exists, say so explicitly.

If verification fails on code you changed, fix the issue and re-verify.
If verification fails on code you did not change, report the failure but
do not attempt to fix it.

### Phase 6: Report

Briefly summarize:

- what was fixed
- what was intentionally skipped
- what verification ran
- any remaining risk

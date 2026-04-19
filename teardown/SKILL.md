---
name: teardown
description: >
  Read an unfamiliar project and produce three ASCII diagrams — system
  context, system container, and a main-flow sequence — with enough inner
  detail to show the important modules, not just the top-level framework.
---

# Teardown

Read the project, then produce three ASCII diagrams that show how it is
structured and how it works. Include the important inner detail — not
just top-level boxes and arrows.

## When to use

Use this skill only when the user explicitly invokes `/teardown`, asks to
use this exact skill, or names it directly.

## Instructions

### Phase 1: Scope

Default target is the current working directory. If the user points
elsewhere, use that. If the target is not a recognizable project, ask
what to map.

### Phase 2: Read the project

Read enough to understand how the project is put together — both its
top-level shape and the important modules inside it. Cover the README,
package manifests, directory tree, entry points, and any infrastructure
signals. Go deeper into the areas that matter for the diagrams.

Do not draw yet.

### Phase 3: Draw the three diagrams

Use free-form ASCII. Draft sequentially.

#### Diagram 1: System context

The project in the center with its core components visible inside,
surrounded by the users and external systems it actually interacts
with. Label arrows with direction and purpose.

#### Diagram 2: System container

Zoom into the project and show its internal structure in enough depth
that the reader understands the anatomy — major pieces, significant
modules inside them, and how they communicate.

#### Diagram 3: Main-flow sequence

Pick one end-to-end flow that best represents what the project does.
Trace the real path across the participants with the substantive
steps — not a single arrow from entry to exit.

### Phase 4: Deliver

Output the three diagrams in order, each with a short caption. Briefly
note what was deliberately left out.

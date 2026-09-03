# Skill Template

Copy this as a starting point for new skills. Replace all `[bracketed]` content.

```markdown
---
name: [skill-name-in-kebab-case]
description: [What this skill does] and [when to use it]. Use when [specific trigger phrases, file types, contexts]. Also triggers for [adjacent use cases that should match].
metadata:
  traits: [pipe-separated technology tags, e.g. .NET|CSharp|VisualBasic|DotNetCore]
  discovery: [optional: "lazy" for on-demand loading]
---

# [Skill Title]

## Overview

[1-2 sentences: what this skill enables and the core approach. Only add context Claude doesn't already have.]

## Quick Start

[Minimal working example — the fastest path to a useful result.]

```[language]
[code or instructions]
```

## Workflow

[Steps for the main use case. Use imperative form.]

1. [First step]
2. [Second step]
3. [Third step]

[For complex workflows, include a progress checklist:]

```
Task Progress:
- [ ] Step 1: [description]
- [ ] Step 2: [description]
- [ ] Step 3: [description]
```

## [Domain/Feature Section]

[Add sections as needed for distinct features or domains.]

[If content grows beyond ~100 lines for a section, move to a reference file:]
**[Advanced topic]**: See `references/topic.md` for details

## Cross-Project / Cross-Task Handoff

[Include only if this skill's change can require a follow-up in a different file, project, or
task that is out of this skill's own scope — e.g. a library change that needs a call added at a
consuming application's composition root, entry point, or config, which may be handled by an
earlier, later, or already-completed task.]

- If the follow-up location is inside the current task's scope, wire it in directly and verify
  it (e.g. grep to confirm the call site actually exists, not just declared).
- If it is out of scope, do not guess at editing another project/task. Record a durable note
  instead so it survives after this task's context ends:
  - If the host's upgrade workflow tracks a shared ledger (e.g. `pending-registrations.md`),
    append an entry there with the exact call and the project that must add it.
  - Otherwise, note it explicitly in the task's progress record (e.g. `progress-details.md`)
    under a clearly-labeled follow-up heading.

## Common Patterns

[Include 1-3 input/output examples if output quality depends on seeing the style.]

**Example 1:**
Input: [realistic input]
Output: [expected output]

## Troubleshooting

[Common issues and their solutions. Only include if the skill has known gotchas.]
```

## Directory structure template

- `[skill-name]/`
  - `SKILL.md` — Main instructions (<500 lines)
  - `references/` — Detailed docs (loaded on demand). .NET published skills use `ref/`.
    - `[domain].md` — One file per domain or feature
  - `scripts/` — Executable utilities
    - `[helper].py` — Pre-made scripts for deterministic tasks
  - `templates/` — Output format templates (if needed). .NET published skills use `tmpl/`.

## Frontmatter rules reminder

- `name`: lowercase, hyphens, numbers only. ≤64 chars. No "anthropic"/"claude". **Start with a gerund verb** (`migrating-`, `converting-`, `managing-`).
- `description`: ≤1024 chars. Third person. Include triggers. Be specific.
- `metadata`: optional project-specific block. `traits` = pipe-separated tech tags; `discovery` = loading strategy (e.g., `lazy`).

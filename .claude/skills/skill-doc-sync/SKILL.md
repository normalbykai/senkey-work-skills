---
name: skill-doc-sync
description: Sync a concise Markdown catalog entry whenever a project skill is added or materially changed. Use when creating, editing, reviewing, or packaging project skills; do not use for unrelated documentation work.
---

# Skill Documentation Sync

When the task adds a skill or materially changes an existing skill, update the project’s external Markdown documentation in the same task so users can discover what the skill is for.

## Documentation Target

- Use the Markdown file explicitly named by the user when one is provided.
- Otherwise, use the repository’s skill catalog or README if it already lists project skills. In this repository, the default target is `README.md`.
- If no suitable catalog exists, ask the user where the external documentation should live rather than creating an unrelated document.

## Required Update

For each affected skill, add or revise one concise catalog entry that states:

- the skill name;
- its high-level purpose and intended trigger or use case;
- any material activation boundary that prevents misuse, such as explicit-only invocation or an implementation restriction.

Keep the documentation user-facing. Describe the capability and outcome rather than copying the full workflow or internal instructions. Update directory examples only when they would otherwise become misleading.

## Consistency Check

Before finishing, verify that the documented name, purpose, and activation boundary agree with the final `SKILL.md` and host-specific metadata. Do not report the skill change as complete until the documentation update is included in the reviewed change set.

---
name: solution-fit-review
description: Independently assess whether a requested technical or product solution fits the actual goal and current system before implementing it, then keep plans, summaries, and review documents focused on the final adopted solution. Use when a user proposes replacing an architecture, technology, workflow, data model, or implementation approach, or asks for documentation after such a change. Do not trigger for simple factual edits with no meaningful solution choice.
---

# Solution Fit Review

Treat the user's desired outcome as authoritative, but treat a proposed implementation method as a hypothesis to evaluate rather than an automatically approved decision.

## Before Changing the Solution

Identify the actual goal, the current approach, and the constraint or failure motivating the change. Inspect available code, configuration, documentation, and operational context before deciding when those artifacts are accessible.

Evaluate the proposed approach against the factors that materially affect this case, such as:

- whether the current approach already satisfies the requirement;
- concrete benefit compared with the current approach;
- compatibility with the existing architecture and team conventions;
- migration, rollback, data, operational, security, and maintenance costs;
- whether a smaller or more direct change achieves the same outcome.

Do not invent objections merely to appear independent. Reach a position supported by evidence from the current system and the stated requirement.

## Responding to a Proposed Approach

- If it fits, proceed and state the decisive reason briefly. Do not echo the user's proposal as though repetition were validation.
- If it is viable but inferior, recommend the better approach and explain only the tradeoff that changes the decision.
- If it conflicts with the goal, architecture, or unacceptable risk, do not start the replacement. State the conflict, give the preferred alternative, and request a decision only when the remaining choice materially changes the result.
- If evidence is insufficient, perform safe inspection first. Ask the user only for information that cannot be inferred or inspected and is necessary to choose safely.

Examples such as changing a database engine are context, not fixed rules. A database migration may be correct, unnecessary, or harmful depending on required capabilities, compatibility, data volume, downtime, deployment environment, and rollback needs.

## Implementation Output

When replacing an approach, make the resulting code and configuration express the adopted approach cleanly. Remove obsolete branches, comments, placeholders, and duplicated abstractions that exist only for the discarded approach, unless backward compatibility or a staged migration genuinely requires them.

Do not add comments that narrate the conversation or explain that an old proposal was rejected. Comments should explain enduring constraints or non-obvious behavior in the final implementation.

## Documentation Output

Default to a clean-state document suitable for implementation and review:

- describe the final adopted architecture, behavior, interfaces, constraints, and verification;
- omit rejected proposals, conversational backstory, and lengthy justification for why sections were changed;
- replace superseded content directly instead of appending correction notes;
- avoid headings such as "Problems with the Previous Approach," "Why This Changed," or "Before and After" unless the user explicitly requests analysis of those topics;
- keep rationale only when it records an enduring constraint or helps reviewers evaluate a real tradeoff.

Include alternatives, decision history, migration narrative, or before/after comparisons only when the requested artifact is explicitly an ADR, feasibility analysis, review response, migration guide, incident report, or change log, or when auditability requires it.

## Completion Check

Before delivering, verify that:

1. the chosen solution satisfies the goal in the actual project context;
2. the response distinguishes evidence from assumptions;
3. no obsolete solution remains without a compatibility reason;
4. the document reads as the final specification, not as a transcript of how the decision evolved.

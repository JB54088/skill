---
name: skill-productizer
description: Turn a workflow, SOP, code repository, or rough brief into a focused, safe, reusable SKILL.md package with clear inputs, outputs, boundaries, and examples; use when a user wants to create or improve an AI Skill, not for ordinary coding or generic prompting.
---

# Skill Productizer

Turn a real piece of work into a Skill that another AI agent can use reliably. The goal is a small, discriminating instruction package—not a long essay, generic prompt, or copy of an entire manual.

## Start with the target job

Before writing, identify:

- the user or team who will invoke the Skill;
- the concrete job it should complete;
- the input artifacts it needs;
- the output or decision it must produce; and
- the closest requests that must *not* activate it.

If the request already provides enough context, infer sensible defaults and proceed. Ask only when a missing choice would change the Skill's purpose or create a meaningful safety or ownership risk.

## Inspect before drafting

When the user supplies a repository, document, SOP, or existing Skill:

1. Inspect the actual files and identify the authoritative source of truth.
2. Preserve useful domain terms, schemas, examples, and constraints.
3. Separate hard requirements from suggestions and historical anecdotes.
4. Flag missing, contradictory, or unsupported claims instead of inventing details.

Never treat an empty repository as a complete Skill. Stop and request source material, or create new content only when the user explicitly authorizes you to define the Skill's purpose.

## Write the Skill

Create a root `SKILL.md` with valid YAML frontmatter containing lowercase hyphenated `name` and a concise, discriminating `description`. The body should contain only guidance that changes the agent's decisions or improves the result.

Use this order when it fits the task:

1. **Purpose and activation** — what the Skill does and when it applies.
2. **Inputs and assumptions** — required artifacts, optional context, and defaults.
3. **Workflow** — the smallest reliable sequence of decisions and actions.
4. **Output contract** — exact deliverables, format, and completion criteria.
5. **Safety and boundaries** — privacy, permissions, destructive actions, and when to stop.
6. **Examples** — only examples that clarify a non-obvious decision.

Prefer precise verbs and observable outcomes. Keep room for judgment where multiple valid implementations exist. Put large schemas, provider-specific procedures, or mode-specific details in focused `references/` files and link them from `SKILL.md`; do not add resource folders just for appearance.

## Quality rules

- Do not restate the model's general capabilities or universal engineering advice.
- Do not turn one incident into a rule for every task.
- Do not fabricate APIs, credentials, data, policies, test results, or business facts.
- Do not expose secrets found in source files; describe the issue and rotate or redact it when authorized.
- Do not broaden a user's authorization. External writes, deployments, messages, and destructive actions require explicit scope.
- Keep the Skill's description narrower than “helps with anything.” Add exclusions only when they prevent likely misrouting.
- Make the happy path, empty state, error state, and stopping condition clear when they matter.

## Validate the package

Before delivery:

1. Verify the frontmatter, name, links, and referenced files.
2. Remove scaffold placeholders, duplicated prose, and unsupported claims.
3. Check that a realistic request would activate this Skill but an adjacent request would not.
4. Run the available Skill validator, such as `quick_validate.py`, when present.
5. Report what was created, what was validated, and any remaining human decision.

When packaging or uploading, include only files that directly support the Skill. Do not include `.git`, local environment files, credentials, build caches, or unrelated project history.

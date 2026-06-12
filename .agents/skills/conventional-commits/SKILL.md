---
name: conventional-commits
description: Propose English Conventional Commit messages following the official Conventional Commits 1.0.0 specification. Use when the user asks for commit names, commit proposals, commit messages, Conventional Commits, or wants commit wording adapted to another active skill or project area.
---

# Conventional Commits

Use this skill when the user asks for commit message proposals, commit names, commit titles, Conventional Commits, or commit wording related to work done through another skill.

All proposed commit messages must be in English, even when the conversation, source files, or project documentation are in another language.

## Source of Truth

Follow the official Conventional Commits 1.0.0 specification:

`https://www.conventionalcommits.org/en/v1.0.0/`

The required base format is:

```text
<type>[optional scope][optional !]: <description>

[optional body]

[optional footer(s)]
```

## Required Rules

- A commit must start with a type, followed by an optional scope, an optional `!`, then `: `, then a short description.
- Use `feat` when the commit adds a feature.
- Use `fix` when the commit fixes a bug.
- Use a scope when it adds useful context. The scope must be a noun in parentheses after the type.
- Put the short description immediately after the colon and space.
- Add a body only when the short description is not enough to explain the change.
- Put the body one blank line after the description.
- Add footers one blank line after the body, or one blank line after the description when there is no body.
- Use `BREAKING CHANGE: <description>` in the footer, or add `!` before the colon, when the change breaks an expected contract or established behavior.
- Keep `BREAKING CHANGE` uppercase when used as a footer token.
- Treat `BREAKING-CHANGE` as equivalent to `BREAKING CHANGE` when used as a footer token.

## Preferred Types

Use these types unless the repository clearly follows a different local convention:

| Type | Use for |
| --- | --- |
| `feat` | New user-facing or developer-facing behavior |
| `fix` | Bug fixes |
| `docs` | Documentation-only changes |
| `style` | Formatting or style changes that do not affect behavior |
| `refactor` | Code changes that neither fix a bug nor add a feature |
| `perf` | Performance improvements |
| `test` | Adding or correcting tests |
| `build` | Build system or dependency changes |
| `ci` | CI configuration or workflow changes |
| `chore` | Maintenance work that does not fit another type |
| `revert` | Reverting previous commits |

If a change fits more than one type, prefer separate commits when possible. If only one commit is requested, choose the type that describes the most user-visible or semantically important effect and include alternatives.

## Scope Selection

Infer a concise scope from the most specific stable context:

1. The active skill name, when the task is skill-driven.
2. The changed top-level area, directory, module, or package.
3. The domain of the work, such as `skills`, `plans`, `docs`, `notebooklm`, `solar`, `git`, or `latex`.
4. Omit the scope when it would be vague, redundant, or misleading.

When another skill is active, adapt the scope or description to that work:

| Related skill | Suggested scopes |
| --- | --- |
| `spec-driven-development` | `spec`, `planning`, `skills` |
| `prd-to-plan` | `plans`, `planning` |
| `write-a-prd` | `prd`, `planning` |
| `nlm-skill` | `notebooklm`, `automation` |
| `doc_tecnica_solar_hibrida` | `solar`, `docs` |

Do not edit other skills just to integrate this one unless the user explicitly asks for cross-references.

## Proposal Workflow

When asked for commit proposals:

1. Inspect the user's stated intent.
2. If working in a repository, inspect Git context with:

   ```powershell
   git status --short
   git diff --stat
   git diff --name-only
   ```

3. Classify the change using the official Conventional Commits rules.
4. Select a scope from the active skill, changed files, or project area.
5. Return one recommended commit message first.
6. Add alternatives when type, scope, or wording is ambiguous.
7. Explain briefly why the recommended type and scope were selected.

## Output Format

For simple requests, use:

```text
Recommended:
docs(skills): add conventional commit guidance

Alternatives:
feat(skills): add commit proposal skill
docs(git): document conventional commit workflow
```

For breaking changes, use either:

```text
feat(auth)!: change authentication token format
```

or:

```text
feat(auth): change authentication token format

BREAKING CHANGE: authentication tokens now use the new signed payload format.
```

For commits with body and footers:

```text
fix(sync): prevent stale source imports

Track the latest import request and ignore older responses when multiple syncs run.

Refs: #123
```

## Quality Bar

- Use imperative, concise English descriptions.
- Keep the subject focused on what changed, not how much work was done.
- Do not end the subject with a period.
- Avoid implementation noise such as temporary file names, local absolute paths, or tool chatter.
- Prefer lowercase types and scopes for consistency.
- Do not invent issue numbers, reviewers, or footers.
- Do not claim a commit was created unless the Git command actually succeeded.
- Ask before staging, committing, pushing, rebasing, or rewriting history.

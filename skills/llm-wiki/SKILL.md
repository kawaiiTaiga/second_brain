---
name: llm-wiki
description: Create, initialize, expand, publish, or clean up a persistent Markdown wiki shared between a user and an LLM agent. Use when Codex needs to scaffold a project knowledge repo, add status/map/skills/knowledge pages, record durable decisions and edge cases, maintain index/log pages, preserve project-subproject hierarchy, or turn an ad hoc notes folder into an LLM-operable wiki.
---

# LLM Wiki

## Overview

This skill exists to give future LLM sessions durable project knowledge they would not otherwise have.

Use this skill to build and maintain a Markdown repository that preserves project context across LLM sessions.

Keep the wiki focused on information the model cannot know by default: project status, decision history, folder maps, working conventions, edge cases, and durable operational knowledge.

## Core Workflow

1. Inspect the current repository or notes folder.
2. Decide whether the task is:
   - initializing a new wiki,
   - updating an existing wiki,
   - filing newly learned information, or
   - cleaning up stale wiki structure.
3. Keep the pattern document separate from live project state when both exist.
4. Update the smallest set of pages needed.
5. Register new pages in `index.md`.
6. Append meaningful milestones to `log.md`.
7. If the wiki should live in git, initialize git when missing, commit meaningful milestones, and push promptly when the user wants the remote updated.

## Default Structure

Use this layout unless the user already has a better-established structure:

```text
wiki/
  index.md
  log.md
  shared/
    skills/
    knowledge/
  projects/
    <project-name>/
      status.md
      map.md
      skills/
      knowledge/
```

If the user wants the wiki at repo root instead of under `wiki/`, preserve the same concepts and page roles.

If the user's work is hierarchical, preserve that hierarchy in the wiki instead of flattening it.

Example:

```text
wiki/
  projects/
    <project-name>/
      status.md
      map.md
      subprojects/
        <subproject-name>/
          status.md
          map.md
          skills/
          knowledge/
```

## Page Roles

- `status.md`: current state, next actions, and important decisions
- `map.md`: folder layout, key files, environments, deployment notes
- `skills/`: how the agent should work in this project
- `knowledge/`: learned behavior, edge cases, workarounds, research findings
- `index.md`: discovery layer for the wiki
- `log.md`: append-only dated milestone history

Read [references/templates.md](./references/templates.md) when creating pages from scratch or normalizing inconsistent ones.

## Read Order

Treat the wiki as a staged reading system for LLMs instead of a pile of Markdown files.

1. Read `wiki/index.md` first.
2. From the index, choose the matching parent project or subproject entry point.
3. Read that project's `status.md` before reading deeper pages.
4. Use `map.md`, `skills/README.md`, and `knowledge/README.md` as hubs for deeper navigation.
5. Read leaf knowledge pages only after the hub pages indicate they are relevant.

Do not expect a new session to read the whole wiki. The index and hub pages should narrow the search space quickly.

## Index-First Rules

Use `index.md` as the canonical top-level navigation page.

- Every new project must be registered in `wiki/index.md`.
- Every new subproject must be registered in `wiki/index.md` under its parent project.
- Root `wiki/index.md` should list entry points, not every deep note.
- Deep pages should be discoverable from the nearest hub page such as `knowledge/README.md` or `skills/README.md`.
- If a section becomes crowded, create or expand a local hub page instead of bloating the root index.
- When editing the wiki, update the relevant index or hub page in the same pass.

The goal is simple: a fresh LLM session should be able to open `wiki/index.md`, choose one branch, and become productive without reading unrelated documents.

## Document Separation Rules

Keep instruction pages and knowledge pages distinct.

- Put operating rules, workflows, conventions, commit habits, sync steps, and "how to work" guidance in `skills/`.
- Put repository facts, GitHub URLs, remote names, branch names, deployment locations, solved bugs, and durable findings in `knowledge/`.
- Do not hide repository location details only inside a skill page when they matter as project facts. Record them in `knowledge/` too.
- Use `status.md` to summarize current state, but store durable repository metadata in a dedicated knowledge page such as `knowledge/repository-hosting.md`.
- When both a skill page and a knowledge page mention the same system, keep the skill page procedural and keep the knowledge page factual.

Example split:

- `skills/README.md`: "Pull before editing, commit after meaningful wiki changes, push to origin main."
- `knowledge/repository-hosting.md`: "Remote is origin, branch is main, repo URL is https://github.com/kawaiiTaiga/second_brain."

## Git Workflow

When the user wants the wiki tracked remotely:

1. Check whether the folder is already a git repository.
2. If not, run `git init` and create an initial commit after scaffolding the wiki.
3. If the user wants GitHub publication, create or connect the remote and push the default branch.
4. After meaningful wiki updates, add, commit, and push them instead of leaving the repo ahead locally.
5. Record repository URL, visibility, branch, and remote details in the wiki's knowledge pages when they matter operationally.

Do not wait for a later reminder if the user explicitly asked for git publication or push.

## Hardcoded GitHub Defaults

Use these defaults for the user's second-brain wiki unless the user explicitly overrides them:

- GitHub owner: `kawaiiTaiga`
- Repository name: `second_brain`
- Repository URL: `https://github.com/kawaiiTaiga/second_brain`
- Clone URL: `https://github.com/kawaiiTaiga/second_brain.git`
- Remote name: `origin`
- Default branch: `main`
- Visibility target for first publication: `public`

When operating on the user's second-brain wiki, assume `origin` should point to `https://github.com/kawaiiTaiga/second_brain.git`.

## Sync Rules

Keep the wiki synchronized with the GitHub remote instead of letting local-only state drift.

1. Before editing an already-published wiki, inspect git state and sync from `origin/main` when it is safe to do so.
2. After meaningful wiki changes, run `git add`, create a focused commit, and push to `origin main`.
3. If the remote is missing but this is the second-brain wiki, connect it to `https://github.com/kawaiiTaiga/second_brain.git`.
4. Keep repository metadata up to date in `knowledge/repository-hosting.md` or the closest equivalent page.
5. If visibility, branch, remote URL, or tracking behavior changes, update the wiki record in the same pass.

Prefer an immediate push after each meaningful wiki maintenance task when the user has already approved GitHub usage for that repository.
Do not leave a completed wiki update only in local git state when this repository is meant to stay synced to GitHub.

## Location Writing Rules

When writing wiki pages, prefer explicit, copyable GitHub locations over vague references or local-only paths.

- Write the full GitHub repository URL, not just the repo name.
- Write the clone URL when git usage matters.
- Name the remote explicitly, for example `origin`.
- Name the tracked branch explicitly, for example `main` or `origin/main`.
- Prefer GitHub URLs over local filesystem paths when documenting repository location.
- Use a local path only when filesystem location itself is operationally important.
- When relevant, include exact deployment targets or service URLs.
- If a subproject has its own repository or deployment target, record that exact location in that subproject's knowledge page.

Bad:

- "the repo is on GitHub"
- "push to the main repo"
- "local folder is C:\\some\\path\\repo"

Good:

- "Repository URL: https://github.com/kawaiiTaiga/second_brain"
- "Clone URL: https://github.com/kawaiiTaiga/second_brain.git"
- "Push updates to origin/main"
- "GitHub location: https://github.com/kawaiiTaiga/second_brain"

## Hierarchy Rules

Preserve the user's real operating hierarchy.

- Keep parent project context at the parent project level.
- Put subproject-specific state, maps, workflows, and learnings inside that subproject's folder.
- Use parent `status.md` and `map.md` to summarize how subprojects relate to each other.
- Reflect the hierarchy in `index.md` so future sessions can discover both the parent and the child pages quickly.
- Avoid flattening unrelated subprojects into one shared status page unless the user explicitly wants that simplification.
- Keep repository-sync notes at the matching hierarchy level when a subproject has its own remote or deployment flow.
- Keep exact repository or deployment locations at the same hierarchy level they belong to.

## Filing Rules

Record information where future sessions will look first:

- Put current progress and next steps in `status.md`.
- Put physical layout and file-role information in `map.md`.
- Put repeatable working rules in `skills/`.
- Put solved bugs, vendor quirks, and durable lessons in `knowledge/`.
- Put cross-project items in `shared/` instead of duplicating them.
- Put new navigation links in `index.md` or the nearest hub page at the same time you create the page.

Do not store obvious general knowledge just because it is true. Prefer information that is specific to the user's work.

## Maintenance Rules

When asked to clean up the wiki:

1. Remove ambiguity before removing content.
2. Merge duplicate pages when they overlap heavily.
3. Update stale summaries rather than rewriting everything.
4. Ensure `index.md` matches the actual file set.
5. Add or refresh `log.md` entries for meaningful structural changes.
6. Preserve or improve the project-subproject hierarchy rather than collapsing it.
7. Compress overloaded indexes so they point to hubs and entry points instead of turning into exhaustive dumps.

## Output Expectations

When you use this skill, leave the wiki in an operable state:

- every important page exists,
- `index.md` points to what matters,
- `index.md` is the first place a fresh LLM session can use,
- `status.md` can restore project context quickly,
- new learnings are filed into a durable location,
- project and subproject relationships are explicit,
- git state is current when the user asked for publication or push,
- the second-brain wiki stays aligned with `https://github.com/kawaiiTaiga/second_brain`,
- repository location is documented with GitHub URLs first, not local paths,
- completed wiki work is pushed when this repo is supposed to stay synced,
- deep pages are reachable through hub pages instead of only through brute-force search.

# LLM Wiki
A pattern for building a shared knowledge store between you and your LLM agent, designed for solo entrepreneurs running multiple projects.

## Core Idea

When you work on projects with an LLM agent, knowledge gets created and lost every session. Edge cases you discovered, architecture decisions you made, conventions you established — all gone the next time you start a conversation. This pattern fixes that.

You maintain a shared markdown repository where **project status, decision history, project structure, work conventions, and hard-won knowledge** accumulate over time. The agent doesn't need to reload the entire wiki every session. You point it to the relevant pages for the current task, and it picks up where things left off.

This isn't about storing general knowledge the LLM already has. It's about capturing **what the LLM can't know** — your project's quirks, the workarounds you found, your users' behavior patterns, why you chose this stack over that one. This knowledge isn't static. It evolves: "this API seems weird" → "it breaks under this condition because of X" → "here's how to work around it." The wiki is where that evolution is preserved.

Context management is the human's job. The agent doesn't need to know everything at once — you decide what's relevant per task. The agent executes the work and records what it learns. You direct; the agent documents.

## Structure

```
wiki/
  index.md
  log.md
  shared/
    skills/
    knowledge/
  projects/
    product-a/
      status.md
      map.md
      skills/
      knowledge/
    branding/
      status.md
      knowledge/
```

### Per-Project Space

**status.md** — Where the project stands right now. What's done, what's next, and why decisions were made. The agent should be able to read this single file and regain full context after days away.

**map.md** — The physical layout of the project. Folder structure, key file roles, environment config, deployment setup. The agent's reference for "where is this?" questions.

**skills/** — How the agent should work on this project. Commit conventions, code style, testing approach, deployment steps, tool usage. Project-specific skills live here; cross-project skills go in shared/skills.

**knowledge/** — What you've learned together by working on this project. API edge cases, library gotchas, performance fixes, user behavior patterns. Starts as rough notes, matures as experience accumulates.

### Shared Space

**shared/skills/** — Conventions and workflows that apply across all projects. Git workflow, code review habits, documentation standards, preferred tools.

**shared/knowledge/** — Lessons that aren't tied to one project. Cross-cutting technical knowledge, patterns you've seen repeat, general operational learnings.

### Meta Files

**index.md** — A catalog of every page in the wiki. Organized by project and category, each entry with a one-line summary. The agent starts here when looking for relevant pages. As the wiki grows, split into per-project sub-indexes.

**log.md** — Chronological record of what happened and when. Append-only. Use a consistent format so it's parseable:
```
## [2026-04-13] product-a | Completed payment API integration
- Stripe webhook setup, found 3 edge cases → knowledge/stripe-webhooks.md

## [2026-04-13] branding | Launched Twitter campaign
- First week results logged → knowledge/twitter-launch-results.md
```

## Operations

### Writing
When something new is learned or decided, it goes into the wiki.

- **New project** → Create folder under projects/, initialize status.md and map.md
- **Task completed** → Update status.md, optionally log in log.md
- **Bug or edge case solved** → Record in knowledge/, update related pages if they exist
- **New convention decided** → Add to skills/ (project-level or shared)
- **Project structure changed** → Update map.md

The agent can write these, or you can write them directly. Either works.

### Reading
When giving the agent a task, point it to the relevant pages. The agent can also search index.md on its own to find what it needs. No need to load everything — just what's relevant to the task at hand.

### Maintenance
Periodically, have the agent tidy up:
- Update stale status.md files
- Merge duplicate knowledge pages
- Verify index.md matches current state
- Add missing links between related pages

One message: "clean up the wiki" — and the agent handles it.

## Infrastructure

**Storage**: GitHub private repo. Markdown is text — negligible storage. Clean diffs, full history, easy rollback.

**Editing**: Any editor works. If the wiki grows large and you want a visual overview of connections, Obsidian's graph view can help. Easy to connect later since an Obsidian vault is just a folder.

**Search**: index.md is enough at first. If pages reach the hundreds, add a search tool (e.g., qmd for hybrid BM25/vector search over markdown).

**Agent access**: Codex reads GitHub repos directly. Claude Code reads local files. Any agent that can access the repo works.

**Your access**: Browse on GitHub web, clone locally and pull/push, or sync with Obsidian Git — whatever feels natural. Figure this out as you go.

## Tips

- Each page should be self-contained. Reading one page should be enough to understand that topic.
- If you're unsure where something belongs, just put it somewhere and register it in index.md. The index is how things get found, not the folder.
- Start things in a project folder. If a pattern repeats across projects, promote it to shared/.
- Don't over-engineer the structure upfront. Let it evolve as you work.
- The wiki is a git repo — branch off to experiment with restructuring.
- Branding, marketing, growth — these are their own project, not a subfolder of a product. They have their own status, their own knowledge.

## Why This Works

Running a solo business means every context lives in your head. Take a few days off and you forget where you left off. Use an LLM agent and it's worse — every session starts from zero.

This wiki is the **persistent shared context** between you and your agent. You direct, the agent documents, and knowledge compounds. As projects accumulate, shared/ grows thicker, and new projects benefit from everything you've already learned. The maintenance cost is near zero because the agent does the filing.

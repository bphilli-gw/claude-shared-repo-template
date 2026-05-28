# Claude Shared Repo Template

A starter for shared GitHub repos where multiple people contribute via [Claude Code](https://claude.com/claude-code). Drops in a lightweight git workflow (branch-per-task, PR to default branch, owner approves merges) along with rules that Claude reads so contributors don't have to type git commands directly.

Designed for small teams (2–5 people) doing collaborative work — research projects, internal tools, data pipelines — where the contributors are not full-time engineers and the repo benefits from light-touch coordination.

## What's in here

| File | Purpose |
|---|---|
| `CONTRIBUTING.md` | Human-facing guide. Names the maintainer, gives contributors a 5-phrase Claude cheat sheet, and lists what not to commit. |
| `.github/CODEOWNERS` | Auto-requests review from the named owner on every PR. |
| `CLAUDE.md` | Project-level Claude instructions. Customize the top section for your project; keep the "Git workflow (shared repo)" section as-is. |
| `.claude/commands/done.md` | A `/done` slash command. Run it at the end of a session — commits WIP, pushes the branch, opens or updates a PR. Stops short of merging (owner's call). |

## How to use

1. Click **"Use this template"** at the top of this page to create a new repo from these files.
   - **Where to create it**: if this is a standardized artifact your organization depends on (a skill staff are told to use, a shared data pipeline, an internal tool), create the repo in your **GitHub organization** so ownership isn't tied to a personal account. If it's informal — your own experiment, a one-off — your personal account is fine.
2. In the new repo, edit:
   - `CONTRIBUTING.md` — replace the maintainer block.
   - `.github/CODEOWNERS` — replace `@OWNER-GITHUB-USERNAME`.
   - `CLAUDE.md` — replace the project description; leave the git workflow section.
3. Commit and push.
4. Add your collaborators on GitHub (Settings → Collaborators).
5. **Turn on merge settings** (one-time):
   - Settings → General → check "Allow squash merging" and "Automatically delete head branches"
   - Settings → Branches → branch protection on the default branch → check "Require linear history"

That's it. Contributors clone the repo, open it in Claude Code, and use the cheat sheet in `CONTRIBUTING.md`.

## The workflow it sets up

1. **Pull before you start.** Claude does this automatically at session start.
2. **Branch per task.** Contributors branch off the default branch with a task-named branch (e.g. `add-extractor`, not `mark-changes`).
3. **PR to default branch.** When ready, Claude opens a PR. CODEOWNERS auto-requests review from the owner.
4. **Owner squash-merges.** Linear history is enforced; the branch is auto-deleted on merge. Non-owners do not merge their own PRs.
5. **End sessions with `/done`.** Commits WIP, pushes, opens or updates the PR. Keeps work from being abandoned in closed Claude windows.
6. **After merge, clean up locally.** Switch back to the default branch, pull the squashed commit, delete the merged local branch, start the next task fresh.

## Background

This template came out of [GiveWell's](https://www.givewell.org/) Claude Code rollout — researchers (not engineers) collaborating on shared repos for data pipelines and writing tools. The rules are deliberately light: enough ceremony to prevent contributors stepping on each other's work and to keep the default branch deployable, light enough not to slow down 1–2 person projects.

## License

MIT — copy, adapt, share. See `LICENSE`.

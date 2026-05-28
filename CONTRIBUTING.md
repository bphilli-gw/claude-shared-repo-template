# Contributing

This file is the canonical guide for collaborating in this repo — for both humans driving git through Claude and for Claude itself. Claude reads it at session start and follows the rules; humans can use it as a cheat sheet for what to ask Claude to do.

## Maintainer

- **Owner**: [NAME] (@[GITHUB-USERNAME]) — approves merges to the default branch

Slack the owner with questions; open a GitHub issue for proposed changes.

## Workflow

### Start of session

Pull the latest from the default branch (`git pull --rebase`). For non-trivial work, create a branch named after the task (`add-data-source`, `fix-rendering-bug`), not the contributor.

### During the work

Commit at natural checkpoints with imperative messages ("Add data source"). Push the branch early (`git push -u origin <branch>`) so collaborators can see WIP.

### End of session

Run `/done`. It commits WIP, pushes the branch, and opens or updates a PR. Don't leave work abandoned in a closed Claude window.

### Reviewing

Open a PR against the default branch with what changed, why, and how to verify. PRs auto-request review from CODEOWNERS. Ask Claude to summarize the diff in plain English if you didn't author the work.

### Merging (owner only)

**Squash and merge**, then **delete the branch.** Branch protection on the default branch requires **linear history** (no merge commits), so one PR = one commit on the default branch and `git log` reads as a clean list of PRs. If you're not the owner, tag the owner for review instead of self-merging.

One-time repo setup (owner): Settings → General → enable "Allow squash merging" and "Automatically delete head branches"; Settings → Branches → branch protection on the default branch → enable "Require linear history".

### After your PR is merged

Before starting your next task on this repo:

- Switch to the default branch (`git checkout main`)
- Pull the squashed commit (`git pull --rebase`)
- Delete the merged local branch (`git branch -D <branch>`)

Don't keep working on a branch that's already been merged — start a fresh branch from the updated default.

### Conflicts

If `git pull --rebase` or merging produces conflicts, stop. Explain the conflicting hunks in plain English; let the maintainer decide. Don't auto-resolve.

## Cheat sheet (what to tell your Claude)

| Stage | Say to Claude |
|---|---|
| Starting | "Pull the latest and start a branch for [what I'm doing]." |
| Mid-work | "Commit my changes." |
| Done for the session | "Run `/done`." (Or: "Push the branch and open a PR.") |
| Reviewing | "Summarize the changes in this PR in plain English." |
| Merging (owner only) | "Squash, merge, and delete the branch." (Otherwise: "Tag the owner for review.") |

## Coordinate before big work

For schema changes, new features, or anything that touches a shared interface — open a GitHub issue (or message the owner) before starting. Saves you from doing work that gets rejected at PR time.

## Don't

- Commit secrets (API keys, tokens, `.env` contents). If one's already in history, flag for rotation.
- Commit large data files or generated outputs. Add patterns to `.gitignore`.
- *Edit* Excel/Word/PowerPoint in the repo — git can't merge them, so one person's changes disappear. Reference-only copies are fine; collaborative editing is not. Use markdown/CSV/YAML for live work.
- Force-push (`--force`, `--force-with-lease`) unless the maintainer explicitly requests it.
- Skip hooks (`--no-verify`) unless the maintainer explicitly requests it.
- Commit directly to the default branch.
- Merge your own PR if you're not the owner.

## If something looks weird

Ask Claude to explain before doing anything destructive. Or ping the owner.

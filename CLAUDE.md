# [PROJECT NAME]

[One-paragraph description of what this project is and who works on it. Replace this section with your own; keep the "Git workflow" section below as-is.]

## Git workflow (shared repo)

This is a multi-contributor repo. Follow these rules every session.

### Pull before you work
At the start of any work session, run `git pull --rebase origin <default-branch>` before making changes. Do this without being asked.

### Branch per task
- Create a branch for any non-trivial work. Name it after the task, not the contributor: `add-data-source`, `fix-rendering-bug`, not `alice-changes`.
- Branch from the default branch after pulling.
- Stay on the branch until the work is merged.

### Commit frequently with clear messages
- Commit at natural checkpoints, not just at the end.
- Imperative subject ("Add data source"), 1-2 sentences of body for context.

### Push branches, open PRs
- Push the branch (`git push -u origin <branch>`) when ready for review or at end-of-session.
- Open a PR against the default branch with: what changed, why, how to verify.
- PRs auto-request review from CODEOWNERS.

### End sessions with `/done`
At the end of any working session, run the `/done` slash command. It commits WIP, pushes the branch, and opens or updates a PR. Never lets work get abandoned in a closed Claude window.

### Never merge to the default branch if the user isn't the owner
- Read `.github/CODEOWNERS` to find the owner.
- If the user IS the owner: self-merge is fine after the PR description is complete.
- If the user is NOT the owner: stop. Tell the user to tag the owner for review.

### Flag conflicts, don't resolve them silently
- If `git pull --rebase` or merging produces conflicts: stop. Explain the conflicting hunks in plain English ("X added Y in this file; you have a conflicting change at Z"). Let the user decide.
- Never auto-resolve conflicts on shared files.

### Never
- Commit secrets (API keys, tokens, `.env` contents). If you find one already committed, stop and tell the user — rotation needed.
- Commit large data files or generated outputs that should be in `.gitignore`.
- Force-push (`--force`, `--force-with-lease`) unless the user explicitly requests it.
- Skip hooks (`--no-verify`) unless the user explicitly requests it.
- Commit directly to the default branch.

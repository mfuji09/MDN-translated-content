---
name: mdn-ja-pr-update
description: "Use when preparing Japanese MDN article updates for commit: find modified files matching a reference sourceCommit, stage only those updates, derive the English source date in JST, create a branch from upstream/main, and commit."
---

# MDN Japanese Article Update

Use this workflow to stage and commit updates to existing Japanese MDN articles without including unrelated worktree changes.

## Procedure

1. **Identify the reference article and repository**
   - Read the supplied article or `file_index.md` frontmatter for `slug` and `sourceCommit`.
   - In `slug`, use the final path component, lowercased, for the branch name.
   - Work in the `translated-content` repository. Confirm the repository root, current branch, remotes, and `git status --short`.
   - Never edit read-only attachments.

2. **Find only matching updated Japanese files**
   - Search `files/ja` for the exact `sourceCommit` value.
   - Compare matches with `git status --short` and include only existing, tracked files marked modified (`M`), staged or unstaged.
   - Do not include added, untracked, deleted, or renamed files, other locales, or unrelated modified files. Do not use `git add -A`.
   - If unrelated changes are already staged, stop and ask how the user wants them handled.
   - Stage the explicit matching modified paths with `git add -- <paths>`.
   - Verify `git diff --cached --name-status` contains only the intended modified (`M`) files and run `git diff --cached --check`. Leave unrelated changes untouched.

3. **Determine the English source date in JST**
   - In the English `content` repository, read the source commit's committer timestamp (including its timezone), for example with `git show -s --format=%cI <sourceCommit>`.
   - Convert that instant to `Asia/Tokyo` and use the resulting calendar date, formatted `YYYY/MM/DD`. Do not use the UTC date if it differs.
   - Use this commit message: `YYYY/MM/DD 時点の英語版に基づき更新`.

4. **Create a branch from upstream/main**
   - Use today's date in `Asia/Tokyo`, formatted `YYMMDD`, followed lowercased the slug and `-1`, e.g. `YYMMDD-typedarray-1`.
   - Check local and remote branch names first. If the requested name exists, try the next numeric suffix until an available name is found.
   - Fetch `upstream/main` and create/switch to the new branch directly from it. Do not merge `main` into the branch just to update it; do not base the branch on a previous feature branch.
   - Preserve staged and unstaged worktree changes while switching. If Git cannot switch safely, stop and explain the blocker rather than discarding or stashing user changes without permission.

5. **Commit only the intended staged files**
   - Recheck the branch, staged name-status, and `git diff --cached --check`.
   - Commit using the message from step 3, explicitly setting the Git author and committer to `mfuji09 <mfujimot@gmail.com>` (for example, use `git -c user.name='mfuji09' -c user.email='mfujimot@gmail.com' commit ...`). Do not rely on ambient Git identity configuration.
   - Do not include unrelated staged or unstaged changes. Stop if unexpected paths are staged.
   - Do not push or open a pull request unless the user asks.

6. **Undo only on explicit request**
   - Before undoing a commit, verify it is the exact latest local commit created for this workflow and has not been pushed.
   - If confirmed, `git reset --soft HEAD^` keeps the commit's changes staged. Never use a hard reset or remove files to undo this workflow.

7. **Report the result**
   - Report the branch, commit hash and message, and any unrelated worktree changes left untouched.

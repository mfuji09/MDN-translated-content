---
name: mdn-ja-pr-new
description: "Use when preparing a Japanese MDN translation for commit or pull request: identify new files by sourceCommit, stage only newly created files, derive dates in JST, create a branch from upstream/main, commit, push to origin, and open a PR."
---

# MDN Japanese Translation Pull Request

Use this workflow to stage and submit newly translated Japanese MDN articles without including unrelated worktree changes.

## Procedure

1. **Identify the reference article and repository**
   - Read the supplied article or `file_index.md` frontmatter for `slug` and `sourceCommit`.
   - In `slug`, use the final path component for the branch name.
   - Work in the `translated-content` repository. Confirm the repository root, current branch, remotes, and `git status --short`.
   - Never edit read-only attachments.

2. **Find only matching new Japanese files**
   - Search `files/ja` for the exact `sourceCommit` value.
   - Compare matches with `git status --short` and include only files that are newly created: staged additions (`A`) or untracked files (`??`).
   - Do not stage tracked files marked modified (`M`), deleted files, files in other locales, or unrelated untracked files. Do not use `git add -A`.
   - Add the explicit matching new-file paths with `git add -- <paths>`.
   - Verify `git diff --cached --name-status` contains only the intended new (`A`) files and run `git diff --cached --check`. Leave all unrelated changes untouched.

3. **Determine the English source date in JST**
   - In the English `content` repository, read the source commit's committer timestamp (including its timezone), for example with `git show -s --format=%cI <sourceCommit>`.
   - Convert that instant to `Asia/Tokyo` and use the resulting calendar date, formatted `YYYY/MM/DD`. Do not use the UTC date if it differs.
   - Use this commit message: `YYYY/MM/DD 時点の英語版に基づき新規翻訳`.

4. **Create a branch from upstream/main**
   - Use today's date in `Asia/Tokyo`, formatted `YYMMDD`, followed by the slug's final component and `-1`, e.g. `YYMMDD-column-rule-inset-cap-1`.
   - Check local and remote branch names first. If the requested name exists, try the next numeric suffix until an available name is found.
   - Fetch `upstream/main` and create/switch to the new branch directly from it. Do not merge `main` into the branch just to update it; do not base the branch on a previous feature branch.
   - Preserve staged and unstaged worktree changes while switching. If Git cannot switch safely, stop and explain the blocker rather than discarding or stashing user changes without permission.

5. **Commit only the intended staged files**
   - Recheck the branch, staged name-status, and `git diff --cached --check`.
   - Commit using the message from step 3, explicitly setting the Git author and committer to `mfuji09 <mfujimot@gmail.com>` (for example, use `git -c user.name='mfuji09' -c user.email='mfujimot@gmail.com' commit ...`). Do not rely on ambient Git identity configuration.
   - Include the required `Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>` trailer.
   - Do not include unrelated staged or unstaged changes. If other changes are staged, stop and ask how the user wants them handled.

6. **Undo only on explicit request**
   - Before undoing a commit, verify it is the exact latest local commit created for this workflow and has not been pushed.
   - If confirmed, `git reset --soft HEAD^` keeps the commit's changes staged. Never use a hard reset or remove files to undo this workflow.

7. **Push to origin and create the PR**
   - Inspect the worktree and branch commits ahead of `upstream/main`. If uncommitted changes remain, ask whether to exclude them or commit them; never include them implicitly.
   - Push the feature branch to the fork's `origin`, not to `upstream/main`: `git push --set-upstream origin <branch>`. If desired, set the branch's `pushRemote` to `origin`, but remember that this setting alone does not publish the branch.
   - If authentication fails, stop and report that the branch has not been published. Do not try pushing the feature branch to `upstream/main`.
   - Once the branch exists on `origin`, create a non-draft PR from that branch to `main` in the fork repository. Use a concise title and summarize that the Japanese translations are based on the stated English source date.
   - Report the branch, commit, PR URL, and any unrelated worktree changes left untouched.

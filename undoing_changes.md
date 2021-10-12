1. Undo the latest/unstaged changes. It reverts changes to modified files before they are staged.
```bash
$ git checkout all_checks.py
```
2. Unstage changes
```bash
$ git add *
$ git reset HEAD output.txt
$ git status
On branch linux
Your branch is ahead of 'origin/linux' by 6 commits.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   advance_git_interaction.md
        modified:   all_checks.py
        new file:   undoing_changes.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        output.txt
```
or
```bash
$ git restore --staged output.txt
```
3. 
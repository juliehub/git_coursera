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
3. Amending commits (modify and add changes to the most recent commit)
(Should not use it on public commits. Meaning, those that have been pushed to a public or shared repository. This is because using --amend rewrites the git history removing the previous commit and replacing it with the amended one. This can lead to some confusing situations when working with other people and should definitely be avoided. So remember, fixing up a local commit with amend is great and you can push it to a shared repository after you fixed it. But you should avoid amending commits that have already been made public.)
```bash
$ touch auto-update.py
$ touch gather-information.sh
$ git add auto-update.py 
$ git commit -m "Add two new scripts"
[linux efa6b24] Add towo new scripts
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 auto-update.py
$ git add gather-information.sh 
$ git commit --amend
[linux 01318e0] Add two new scripts.
 Date: Tue Oct 12 21:06:52 2021 +1100
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 auto-update.py
 create mode 100644 gather-information.sh
```
4. Rollbacks

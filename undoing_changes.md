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
3. Revert changes (create new commit with inverse changes)
```bash
git commit -a -m 'Add call to disk_full function'
[linux 60c9655] Add call to disk_full function
 2 files changed, 22 insertions(+), 1 deletion(-)
$ ./all_checks.py 
Traceback (most recent call last):
  File "./all_checks.py", line 19, in <module>
    main()
  File "./all_checks.py", line 13, in main
    if disk_full():
NameError: name 'disk_full' is not defined
$ git revert HEAD
[linux 4c5c5f5] Revert "Add call to disk_full function"
 2 files changed, 28 insertions(+), 49 deletions(-)
 rewrite undoing_changes.md (62%)
$ git status
On branch linux
Your branch is ahead of 'origin/linux' by 3 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```
4. View the last 2 entries in the log
```bash
$ git log -p -2
% git log -p -2
commit 4c5c5f5c47d4f22dd04ce9231078c7e77c26c30a (HEAD -> linux)
Date:   Tue Oct 12 21:40:40 2021 +1100

    Revert "Add call to disk_full function"
    
    This reverts commit 60c965517f3ac9843e1237fd7b745420deaae113.

diff --git a/all_checks.py b/all_checks.py
index 0550b18..e953e4b 100755
--- a/all_checks.py
+++ b/all_checks.py
@@ -10,9 +10,6 @@ def main():
     if check_reboot():
         print("Pending Reboot.")
         sys.exit(1)
-    if disk_full():
-        print("Disk Full.")
-        sys.exit(1)
     print("Everything ok.")
     sys.exit(0)
```
5. SHA1 hash numbers provide the consitency that is critical for distributed systems sush as Git.
They are created using the commit message, date, author, and the snapshot taken of the working tree.
They are composed of 40 characters. Git can identify a commit using the first few has numbers
as long as there is only one matching possibility.
```bash
$ git log -2
$ git show 4c5c5f5c47d4f22dd04ce9231078c7e77c26c30a
$ git revert 4c5c5f5c47d4f22dd04ce9231078c7e77c26c30a
```
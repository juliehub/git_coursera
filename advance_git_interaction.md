1. Skipping the stating area and adding short comment for small changes with "-m"
```bash
$ git commit -a -m "Call check_reboot from main, exit with 1 on error"
[linux bf0564c] Call check_reboot from main, exit with 1 on error
 1 file changed, 4 insertions(+), 1 deletion(-)
```
2. Git uses the HEAD alias to represent the currently checked out snapshot of your project.
3. Getting more information about our changes
```bash
$ git log -p
commit d436385f1b3fab0e97585599b08212399ed6f52e
Date:   Thu Oct 7 21:18:32 2021 +1100

    add to linux branch

diff --git a/Diffing_Files.md b/Diffing_Files.md
index d238fd7..829d3a3 100644
--- a/Diffing_Files.md
+++ b/Diffing_Files.md
@@ -1,6 +1,6 @@
 1. Use the below commands in Linux
-- diff
-- diff -u
+- diff 
+- diff -u : Output NUM (default 3) lines of unified context.
 - wdiff
 - meld
 - KDiff3
```
4. Display the information about the commit and the patch using commit id
```bash
$ git log 
$ git show bf0564cb887a2e775d5f9b6b5b16c2117d7c5b14
```
5. Show some stats about the changes in the commit uing "--stat"
```bash
$ git log --stat
commit bf0564cb887a2e775d5f9b6b5b16c2117d7c5b14 (HEAD -> linux)
Date:   Mon Oct 11 19:18:55 2021 +1100

    Call check_reboot from main, exit with 1 on error

 all_checks.py | 5 ++++-
 1 file changed, 4 insertions(+), 1 deletion(-)
```
6. "git diff" is equivalent to the "diff -u" output
```bash
$ git diff
diff --git a/all_checks.py b/all_checks.py
index 827f339..c37ef18 100755
--- a/all_checks.py
+++ b/all_checks.py
@@ -10,5 +10,7 @@ def main():
     if check_reboot():
         print("Pending Reboot.")
         sys.exit(1)
-
+    print("Everything ok.")
+    sys.exit(0)
+    
 main()
"
```
7. Review changes before adding them by using the "-p" flag
```bash
git add -p
diff --git a/all_checks.py b/all_checks.py
index 827f339..c37ef18 100755
--- a/all_checks.py
+++ b/all_checks.py
@@ -10,5 +10,7 @@ def main():
     if check_reboot():
         print("Pending Reboot.")
         sys.exit(1)
-
+    print("Everything ok.")
+    sys.exit(0)
+    
 main()
(1/1) Stage this hunk [y,n,q,a,d,e,?]? 
```
8. Review changes that are staged but not committed
```bash
$ git diff --staged
$ git commit -m 'Add a message when everything is ok'
```
9. Remove a file
```bash
$ git rm process.py
$ git status
On branch linux
Your branch is ahead of 'origin/linux' by 3 commits.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    process.py
$ git commit -m 'Delete unneeded processes file'
[linux 22b46a4] Delete unneeded processes file
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 process.py
```
10. Rename a file
```bash
$ git mv disk_usage.py check_free_space.py
$ git status
On branch linux
Your branch is ahead of 'origin/linux' by 4 commits.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    disk_usage.py -> check_free_space.py
$ git commit -m 'New name for disk_usage.py'
[linux c5f324a] New name for disk_usage.py
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename disk_usage.py => check_free_space.py (100%)
```
11. Create .gitignore file
```bash
$ echo .DS_STORE > .gitignore
$ ls -la
$ git add .gitignore 
$ git commit -m 'Add a gitingore file, ignoring .DS_STORE files'
[linux aa0910f] Add a gitingore file, ignoring .DS_STORE files
 1 file changed, 1 insertion(+)
 create mode 100644 .gitignore
```
.gitignore files are used to tell the git tool to intentionally ignore some files in a given Git repository. For example, this can be useful for configuration files or metadata files that a user may not want to check into the master branch. Check out more at: https://git-scm.com/docs/gitignore.
Example: https://gist.github.com/octocat/9257657
12. Git Cheat Sheet
https://training.github.com/downloads/github-git-cheat-sheet.pdf
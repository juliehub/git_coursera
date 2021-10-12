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
Author: Julie Nguyen <julie@Julies-Air.lan>
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
Author: Julie Nguyen <julieng0820@gmail.com>
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

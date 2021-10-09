1. Use the below commands in Linux
- diff 
- diff -u : Output NUM (default 3) lines of unified context.
E.g. 
```bash
diff -u old_file new_file > change.diff
```
- wdiff
- meld
- KDiff3
- vimdiff

2. Applying Changes contained in a diff file to another file
```bash
$ cat cpu_usage.py
$ patch cpu_usage.py < cpu_usage.diff
```

3. Practical Application of diff and patch
```bash
$ cp disk_usage.py disk_usage_original.py
$ cp disk_usage.py disk_usage_fixed.py
$ diff -u disk_usage_original.py disk_usage_fixed.py > disk_usage.diff
$ cat disk_usage.diff 
--- disk_usage_original.py      2021-10-08 16:44:27.000000000 +1100
+++ disk_usage_fixed.py 2021-10-08 16:42:08.000000000 +1100
@@ -1,6 +1,7 @@
 #!/usr/bin/env python3
 
 import shutil
+import sys
 
 def check_disk_usage(disk, min_absolute, min_percent):
     """Returns True if there is enough free disk space, false otherwise."""
@@ -14,9 +15,9 @@
     return True
 
 # Check for at least 2 GB and 10% free
-if not check_disk_usage("/", 2*2**30, 10):
+if not check_disk_usage("/", 2, 10):
     print("ERROR: Not enough disk space")
-    return 1
+    sys.exit(1)
 
 print("Everything OK")
-return 0
\ No newline at end of file
+sys.exit(0)
\ No newline at end of file
$ patch disk_usage.py < disk_usage.diff 
patching file disk_usage.py
$ ./disk_usage.py 
Everything OK
```
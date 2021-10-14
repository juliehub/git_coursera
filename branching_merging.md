1. Create new branch
```bash
$ git branch linux
$ git branch
* master
linux
$ git checkout linux
Switched to branch 'linux'
$ git branch
* linux
  master
```
2. Create a new branch and switch to it
```bash
$ git checkout -b even-better-feature
Switched to a new branch 'even-better-feature'
$ git add free_memory.py 
$ git commit -m 'Add an empty free_memory.py'
[even-better-feature 095823c] Add an empty free_memory.py
 2 files changed, 6 insertions(+)
 create mode 100644 branching_merging.md
 create mode 100644 free_memory.py
$ git log -2
```
3. Delete a branch
```bash
$ git checkout linux
$ git branch -d even-better-feature
error: The branch 'even-better-feature' is not fully merged.
If you are sure you want to delete it, run 'git branch -D even-better-feature'.
$ git branch -D even-better-feature
```
4. Merge a branch using fast-forward merge
```bash
$ git checkout master
$ git merge linux
```
5. Resolve merge conflicts
```bash
$ git checkout master
$ git add free_memory.py
$ git commit -a -m 'Add comment to main()'
$ git checkout linux
$ git add free_memory.py
$ git commit -a -m 'Print everything ok'
```
Now there is conflict
```bash
$ git checkout master
$ git merge linux
CONFLICT (add/add): Merge conflict in free_memory.py
Auto-merging free_memory.py
Automatic merge failed; fix conflicts and then commit the result.
julie@Julies-Air git_coursera % git add free_memory.py 
julie@Julies-Air git_coursera % git status  
On branch master
Your branch is ahead of 'origin/master' by 22 commits.
  (use "git push" to publish your local commits)

All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:
        modified:   branching_merging.md
        modified:   free_memory.py
$ git commit
[master 00a4139] Merge branch 'linux'
$ git log --graph --oneline
*   00a4139 (HEAD -> master) Merge branch 'linux'
|\  
| * 0108bc5 (linux) Print everything ok
| * dd2c074 (origin/linux) Add last update
* | 5c3fd70 Add comment to main()
|/  
* 633a768 Add branching_merging.md
```
The advantage of Git throwing a merge conflict error in cases of overlap is that
it prevents loss of work if tow lines overlap.

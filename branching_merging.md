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
$ git branch -D even-better-feature
```
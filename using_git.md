1. Set basic configuration
```bash
$ git config --global user.email "me@example.com"
$ git config --global user.name "My name"
```
2. Run git init or clone, a 
```bash
$ git init
```
The git directory contains all the changes and their history. The working tree contains the current versions of the files.
3. Add file to Staging area (index)
```bash
$ git add disk_usage.py
$ git status
```
4. Get file committed
```bash
$ git commit -m "Add new disk_usage check."
```
5. Tracking Files
- Each track file can be in one of three main states: modified, staged or committed.
```bash
git status
On branch linux
Your branch is up to date with 'origin/linux'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        using_git.md

nothing added to commit but untracked files present (use "git add" to track)
```
6. 

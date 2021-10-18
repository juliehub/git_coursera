1. Showing remote branches
```bash
% git remote -v
origin  git@github.com:juliehub/git_coursera.git (fetch)
origin  git@github.com:juliehub/git_coursera.git (push)
julie@Julies-Air git_coursera % git remote show origin
* remote origin
  Fetch URL: git@github.com:juliehub/git_coursera.git
  Push  URL: git@github.com:juliehub/git_coursera.git
  HEAD branch: master
  Remote branches:
    linux  tracked
    master tracked
  Local branches configured for 'git pull':
    linux  merges with remote linux
    master merges with remote master
  Local refs configured for 'git push':
    linux  pushes to linux  (up to date)
    master pushes to master (up to date)
julie@Julies-Air git_coursera % git branch -r
  origin/linux
  origin/master
```
2. If we want to make a change to a remote branch,
we pull the remote branch, merge it with the local branch,
then push it back to its origin.
3. Fetch new changes and merge
```bash
$ git remote show origin
$ git fetch
```
4. Run git checkout to view the working tree and
and run git log to view the commit history
```bash
$ git checkout
$ git log origin/master
```
5. Use git pull to update your local branch
or use 'git merge' to merge remote master branch into
our local master branch (using fast-forward)
```bash
$ git merge origin/master
$ git log
```
6. The main difference between git fetch and git pull
is that git fetch fetches remote updates but doesn't merge;
git pull fetches remote updates and merges.
7. A squash merge will take the commits from a target branch and combine or squash them into one commit. This commit is then appended to the HEAD of the merge base branch to keep a 'clean history' during a merge.
8. Push changes to remote branch
```bash
$ git push -u origin linux
```
9. Rebasing changes
```bash
$ git checkout linux
$ git rebase master
$ git checkout master
$ git merge linux
$ git log --graph --oneline
```
10. Remote remote branch
```bash
$ git push --delete origin linux
```
11. Remove local branch
```bash
$ git branch -d linux
```

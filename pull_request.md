1. From Github website, create a fork from the repo on Github
2. Clone the fork
```bash
$ git clone https://..
```
3. Create new branch
```bash
$ git checkout -b add-readme
$ git add README.md
$ git commit -m 'Add a simple README.md file'
$ git push -u origin add-readme
```
4. At the top of project page, click on "Pull request" link.
- If there is conflict, we need to rebase our change against
the current branch of the original repo so that it can be merged.
- Then, enter comments about the change for the Pull Request (fix the bug,
create new feature, how the change was tested manually or auto, etc).
- Tick "Allow edits from mainteners".
- Look at the diff at the bottom of the page to make sure we send the
right change, then click "Create pull request" button.
- Record the indentifier number of the pull request. Maintainer 
can come back with more questions.
5. Update an existing pull request
- Add documentation and test, make sure changes work for all cases,
follow project styles, etc.
```bash
$ vi README.md
$ git commit -a -m 'Add more information to the README'
$ git push
```
- We just push the change to the existing branch
- If we want to create a new pull request, we need to create a new branch.
- We can view changes at "Files changed" tab. Green for new lines and Red 
for lines that we delete.
- We are seeing only 1 file even with 2 commits. We are seeing the differences
between the original repo and the created pull request.
- We can also click on the Review icon to show the rdnered markdown contents.
6. Squash changes into single commit
- You shouldn't rewrite history when the commits have been published. That's because someone else may have already synchronized that repo with those contents. This rule is waived with pull requests, since it's usually only you who have cloned your fork of the repository. 
- So say the project maintainers ask us to create a single commit that includes both changes and a more detailed description than the one we submitted. We can do that by using the interactive version of the rebase command called rebase-i, as the parameter to the command will pass the master branch.
- When we call an interactive rebase, a text editor opens with a list of all the selected commits from the oldest to the most recent. By changing the first word of each line, we can select what we want to do with the commits. The default action here is pick which takes the commits and rebases them against the branch we selected.
- We have two options for combining commits, squash and fix up. In both cases, the contents of the selected commit are merged into the previous commit in the list. The difference is what happens with the commit messages. When we choose squash, the commit messages are added together and an editor opens up to let us make any necessary changes. When we choose fix up, the commit message for that commit is discarded.
E.g.
pick
squash
7. Show the latest changes
```bash
$ git show
$ git status
```
- Show latest 4 commits for all branches
```bash
$ git log --graph --oneline --all -4
```
- Push the new changes (replace a new commit with a new commit, we don't want to merge)
```bash
$ git push -f
$ git log --graph --oneline --all -4
```
Git Fork and Pull Request Cheat Sheet
Check out the following link for more information:

https://help.github.com/en/articles/about-pull-request-merges







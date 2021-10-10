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
Each track file can be in one of three main states: modified, staged or committed.
```bash
    $ git status
    On branch linux
    Your branch is up to date with 'origin/linux'.
    Untracked files:
    (use "git add <file>..." to include in what will be committed)
            using_git.md
    nothing added to commit but untracked files present (use "git add" to track)
```
6. Add file to the stage area
```bash
$ git add using_git.md 
$ git status
On branch linux
Your branch is up to date with 'origin/linux'.
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   using_git.md
```
7. Commit changes
```bash
$ git commit -m 'Add using_git.md file'
 ```
8. Show git comments
```bash
$ git log
```
9. 5 Useful tips for a better commit message
https://thoughtbot.com/blog/5-useful-tips-for-a-better-commit-message
Add this line to your ~/.vimrc to add spell checking and automatic wrapping at the recommended 72 columns to you commit messages.
```bash
autocmd Filetype gitcommit setlocal spell textwidth=72
```
```bash
Commit message style guide for Git

The first line of a commit message serves as a summary.  When displayed
on the web, it's often styled as a heading, and in emails, it's
typically used as the subject.  As such, you should capitalize it and
omit any trailing punctuation.  Aim for about 50 characters, give or
take, otherwise it may be painfully truncated in some contexts.  Write
it, along with the rest of your message, in the imperative tense: "Fix
bug" and not "Fixed bug" or "Fixes bug".  Consistent wording makes it
easier to mentally process a list of commits.

Oftentimes a subject by itself is sufficient.  When it's not, add a
blank line (this is important) followed by one or more paragraphs hard
wrapped to 72 characters.  Git is strongly opinionated that the author
is responsible for line breaks; if you omit them, command line tooling
will show it as one extremely long unwrapped line.  Fortunately, most
text editors are capable of automating this.

:q
```
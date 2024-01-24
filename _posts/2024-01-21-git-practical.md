---
layout: post
title: Git Practical
---

Git is **the** version control tool that's powerful and fast. It's a friend that software engineers meet almost everyday. Besides some simple commands that are so familiar that one can type without even thinking, there are some others that are less frequently used and therefore harder to bear in mind. When their use cases show up, people may have to search and loop through pages for usage examples again and again.

This post aims to serve as a quick and easy reference in practice. It will first give an outline of Git basics, and then list some of those less frequently used Git commands that are very helpful in certain circumstances.

## Basics

`.gitignore` files tell Git what files to not track. They should be set up for any new repository, and be iteratively updated when needed. Useful `.gitignore` templates: <https://github.com/github/gitignore>

Following the sequence in a typical code development process, the basic git commands are:

1. Get a **Git repository** in the first place
   * initialize a new repository: `git init`
   * clone an existing repository from remote: `git clone <url>` (supported transfer protocols such as https, ssh)

2. Pull latest update from remote: `git pull`

3. Create a new **branch** for code development and switch to it: `git checkout -b <branch>`

4. Make code changes - code development process

5. **Check changes**
   * file-level: `git status`
     * "Untracked files": files that are not there in the previous commit, and have not yet been staged
   * line-level: `git diff <optional: file>`

6. **Stage changes** to staging area: `git add <file>`

7. **Commit changes**: `git commit`
   * edit commit message in the pop-up editor, follow best practice to compose commit messages, i.e. short summary followed by a blank line then detailed context and explanation.
   * `git commit -m <commit_message>` for simple commit message

8. Confirm commit history: `git log`

9. **Push** to remote: `git push`

## Beyond Basics

The key design idea of Git is that it stores **snapshots**, rather than a series of changesets or differences. At the core of Git is a simple key-value store, that you can insert any kind of content into a Git repository, for which Git will hand you back a unique key you can use later to retrieve that content. A commit object contains a pointer to the snapshot of the content that is staged, the commit message, the author's name and email address, and pointers to the parent(s) of the commit.

`git log --graph --oneline`: show the commit logs with compact format, and draw a text-based graphical representation of the commit history.

`git log --graph --date-order --pretty=format:'%C(auto)%h%d %C(green)%s%C(reset) <%C(dim)%an %C(blue)%ai%C(reset)>'`: more customized git log visualization

- %h: abbreviated commit hash
- %s: commit message subject
- %d: ref names
- %an: author name
- %cn: committer name
- %ai: author date, ISO 8601-like format
- %ar: author date, relative
- %cd: committer date (format respects `--date=`option, e.g. `--date=short`)
- %cr: committer date, relative
- %Cred, %Cgreen, %Cblue, %C(auto), %Creset: switch color
- %n: newline

`git config --global alias.lg "log --graph --pretty=format:<format_string>"`: set alias

`git config --list`: show git configurations

`git diff --staged <file>` or cached: compare staged changes to the last commit (differently, `git diff` compare working directory with staging area).

`git show <commit_hash>`: show log message and textual diff for a commit.

`git rm <file>`: remove files from working directory (as what `rm` does) and from staging area (stage the removal change)

`git restore --staged <file>`: un-stage staged changes

`git restore <file>`: discard changes in *working directory*

`git commit --amend`: replace the last commit with a new, improved commit that includes new staged changes. Use case: make minor improvements to the last commit that is *local and have not been pushed anywhere*, without cluttering git history with commit messages such as "oops, forgot to ...".

`git commit --amend --date=now --no-edit`: set the author date of the last commit to now, without opening commit message editor.

**rebase**: take the changes that were committed on the current branch, and replay them on target branch. Use case: rebase local changes before pushing to clean up the work, but never rebase anything that have been pushed somewhere.

`git rebase -i <mainline>`: interactively choose whether to squash the commits

**three-way merge**: use two snapshots pointed to by the branch tips and the common ancestor of the two, and automatically create a new merge commit.

**fast-forward**: when you try to merge an older commit with a newer commit that can be reached by following the older commit's history, Git simplifies things by moving the pointer forward because there is no divergent work to merge together.

**merge conflicts**: If two branches changed the same part of the same file differently, Git won't be able to merge them cleanly. It prompts the user to open the files and resolve the conflicts manually.

conflict-resolution markers:
```
<<<<<<< HEAD
top part
=======
bottom part
>>>>>>> the other branch
```

`git cherry-pick A^..B`: cherry-pick all commits from commit A to B

`git branch -d <branch>`: Delete a branch after the work is merged in and the branch is no further needed, otherwise need `-D` to force the delete.

`git push origin --delete <remote_branch_name>`: Delete a remote branch.

`git remote -v`: show all remote servers with shortnames and URLs (`origin` is the default name of the server you cloned from)

`git remote add <shortname> <url>`: add a new remote Git repository

## Reference

- Git Internals - Plumbing and Porcelain, <https://git-scm.com/book/en/v2/Git-Internals-Plumbing-and-Porcelain>
- git documentation - [git-log](https://git-scm.com/docs/git-log)
- [Pretty Git branch graphs](https://stackoverflow.com/questions/1057564/pretty-git-branch-graphs), stackoverflow
- Most commonly used git tips and tricks, <https://github.com/git-tips/tips#everyday-git-in-twenty-commands-or-so>
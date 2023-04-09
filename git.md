# Git

## General

### Staging area
* A middle step between the working directory and the repository.
* Changes made to files in the working directory are not immediately recorded in the repository.
* To prepare changes for the next commit, use the `git add` command to add changes to the staging area
* You can review staged changes using `git status` and `git diff --staged.`
* Use the `git commit` command to record changes in the repository, which creates a new commit with the staged changes and a commit message.
* The staging area allows for reviewing and organizing changes before committing.
* You can selectively stage changes from different files and commit them separately, which makes it easier to collaborate with others and keep track of changes.
* The staging area helps avoid accidentally committing changes that you didn't mean to include.

### Local branch vs Tracking branch
#### Local Branch

* A branch that exists only on your local machine and is not shared with others.
* Used to make changes to your code without affecting the main branch or other branches in the repository.
* Created using the `git co -b <branch>` command.
* Switched to using the `git co <branch>` command.


#### Tracking Branch

* A local copy of a remote branch that allows you to keep track of changes made to the remote branch.
* When you clone a Git repository, your local repository is set up with a default tracking branch (usually named origin/master).
* Updated using the `git fetch` command to update your local copy of the remote branch.
* Used to determine what branch you're working on when you run Git commands that interact with the remote repository (e.g. `git push` or `git pull`).
* Separate from a local branch, which is used for making changes to your code.

### Git pull vs Git fetch
Git pull retrieves the changes from the remote repository and merges them into the local branch, while Git fetch retrieves the changes from the remote repository into the tracking branch but does not merge them into the local branch.

`git fetch` followed by `git merge` is effectively the same thing as `git pull`

### Cherry-picking
Allows you to selectively apply specific commits from one branch to another. It's useful when you want to apply changes from one branch to another without merging the entire branch.

Here's how cherrypicking works:

1. Identify the commit you want to cherry pick. You can do this by checking the commit history of the branch you want to cherry pick from using the git log command. `git log --oneline`
* Switch to the branch you want to apply the cherry-picked commit to using the git checkout command. `git co <branch>`
* Use the git cherry-pick command followed by the commit hash of the commit you want to apply. For example, if you want to cherry pick a commit with hash abc123, you would run `git cherry-pick abc123`.
* Git will apply the changes from the cherry-picked commit to your current branch as a new commit.

Note that cherry picking can be useful in situations where you want to apply a specific fix or feature from one branch to another without merging the entire branch.


## Commands

### Staging
```
# add changes to the staging area
$ git add

# review staged changes
$ git status

# diff between working dir and staged
$ git diff <file>

# diff of staged and repo
$ git diff --staged

# diff between a specific commit and staged
$ git diff <commit> --staged
$ git diff <commit> --staged <file>

# unstage
$ git restore --staged <file>

```

### Cherry-pick a single file from a commit
```
# Get the commit
$ git cherry-pick -n <commit>

# Unstage everything
$ git reset HEAD

# Stage the modifications you want to keep
$ git add <path>

# Make the work tree match the index
# (do this from the top level of the repo)
$ git checkout .
```


### Revert changes to a single file

```
# revert all changes
$ git co example.txt

# if there are multiple changes and want to revert it to a specific previous commit
$ git log —oneline
$ git co abc123 -- file.txt
```

### Undo changes that have not been committed

```
# Move current branch pointer to the commit you want to return to, effectively removing
# the changes made in the subsequent commits. The changes made in those subsequent commits
# will still be present in your working directory and can be modified or committed again.
$ git log --oneline
$ git reset abc123

# or to undo changes made to a file that have not been committed 
$ git co example.txt
```

### Add to the previous commit
```
$ git commit --amend 
```

### Rebase a branch (A B C A')
```
$ git co new-branch

# make changes and commit on new-branch

$ git rebase master
$ git checkout master
$ git merge new-branch
```

### Rebase a branch so that changes are inserted (A A' B C)
```
$ git co new-branch

# make changes and commit on new-branch

# rebase from hash A. This effectively makes it so it looks like B and C
# are created on top of A`
$ git rebase --onto master A new-branch
$ git checkout master
$ git merge new-branch
```

### Delete a remote branch
```
$ git push origin --delete new-branch
```

### Change a commit message
```
$ git commit —amend
```

### Squash the last two commits
```
$ git rebase -i HEAD~2
```




xxxxxx

git commit --amend: This command allows you to modify the most recent commit message or add changes to the most recent commit.

git rebase: This command can be used to change the commit history of a branch by reapplying commits onto a new base. It is often used to remove or squash commits, reorder commits, or combine multiple commits into a single commit.

git reset: This command allows you to move the HEAD pointer to a previous commit, effectively undoing changes made after that commit. This can be done with the --soft, --mixed, or --hard flags, which control how much of the changes are undone.

git filter-branch: This command allows you to rewrite the history of a repository by applying a filter to each commit. This can be used to remove sensitive data, change author information, or split a repository into multiple repositories.



xxxx

Git's rerere (reuse recorded resolution) feature allows Git to remember how you resolved conflicts in the past and use that resolution automatically in the future when it encounters a similar conflict. This can save you time and effort by avoiding the need to manually resolve the same conflicts multiple times.

Here's how Git rerere works:

When Git encounters a conflict during a merge or rebase operation, it saves the conflict resolution in a special directory called ".git/rr-cache". The saved resolution includes the contents of the conflicted files as well as the resolutions you made to resolve the conflict.

If Git encounters a similar conflict in the future, it checks the ".git/rr-cache" directory to see if there is a saved resolution for that conflict. If there is, Git applies the saved resolution automatically without prompting you to resolve the conflict again.

You can manually edit or delete saved resolutions in the ".git/rr-cache" directory if needed.

Git rerere is a powerful feature that can save you time and effort when dealing with conflicts. However, it's important to be aware of the potential pitfalls of rerere, such as accidentally applying a previous resolution to a new conflict that requires a different resolution. Therefore, it's important to use rerere judiciously and with care.


xxxx
git clean: This command removes untracked files from your working directory. It can be useful if you have a lot of generated files that you don't want to commit.





git stash: This command allows you to temporarily save changes that you have made to your working directory without committing them.

git blame: This command shows you who last modified each line of a file, making it useful for tracking down the source of bugs or issues.

git bisect: This command allows you to perform a binary search through the history of your Git repository to find a specific commit that introduced a bug or regression.

xxxx
git instaweb
install lighttpd
ps -ax | grep lighttpd
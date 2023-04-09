# Git

## Cherry-pick a single file from a commit
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
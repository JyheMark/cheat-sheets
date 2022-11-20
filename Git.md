# Git cheatsheet

## Add

Add file to staging area
```Bash
git add <file>
```

## Branch

Rename current branch
```Bash
git branch -m <newName>
```

Remove local branch
```Bash
git branch -d <branch>
```

Show remote branched
```Bash
git branch -r
```

## Checkout

Checkout a branch or commit (works for local and remote branches)
```Bash
git checkout <branch/commit>
```

## Cherry-pick

Merge commit into current branch
```Bash
git cherry-pick <commit>
```

## Clean

Clean files untracked by git, recurse into directories, force
```Bash
git clean -xdf
```

## Clone
Clone remote repository to active working directory
```Bash
git clone <repoAddress>
```

## Commit

Commit changes to branch
```Bash
git commit
```

Commit changes to branch with inline message
```Bash
git commit -m "Commit message"
```

## Diff

Show current un-committed changes on tracked files
```Bash
git diff
```

Show changes on commit
```Bash
git diff <commit>
```

## Fetch

Fetch remote branches/heads
```Bash
git fetch
```

Remove pointers to deleted remote branches
```Bash
git fetch -p
```

## For-each-ref

List remote branches with latest commit author and date, sort by date
```Bash
git for-each-ref --format='%(committerdate) %09 %(authorname) %09 %(refname)' --sort=committerdate
```

## Log

Show log for current branch
```Bash
git log
```

## Merge

Merge branch into current branch
```Bash
git merge <branch>
```

## Pull

Pull changes from a remote branch
```Bash
git pull
```

Remove local changes to tracked files
```Bash
git checkout -f
```

## Push

Push changes to remote
```Bash
git push
```

Force push (Danger)
```Bash
git push -f
```

Delete a remote branch
```Bash
git push origin --delete <branch>
```

## Rebase

Rebase current branch off of another branch
```Bash
git rebase <branch>
```

Interactive rebase on current branch for n commits
```Bash
git rebase -i HEAD~n
```

Interactive rebase on current branch for **all** commits
```Bash
git rebase -i --root
```

## Reflog

Show the ref log
```Bash
git reflog
```

## Remote

Change address for remote repository
```Bash
git remote set-url origin <repoAddress>
```

## Reset

Reset current branch to commit/branch. Keep changes to files.
```Bash
git reset --soft <commit/branch>
```

Reset current branch to commit/branch. Discard changes.
```Bash
git reset --hard <commit/branch>
```

## Show

Show changes on current HEAD
```Bash
git show
```

## Status

Show current status of tracked and untracked files
```Bash
git status
```
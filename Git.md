# Git cheatsheet

git push
git push origin --delete <branch>
git pull
git checkout <branch/commit>
git checkout -f
git add <file> 
git commit -m ""
git rebase -i HEAD~2
git rebase <branch>
git merge <branch>
git diff
git show
git clean
git status
git reset <file>
git branch -m <newname>
git branch -d <branch>
git fetch
git fetch -p
git reset
git reset --hard
git cherry-pick
git reflog
git remote set-url origin <repoAddress>

git for-each-ref --format='%(committerdate) %09 %(authorname) %09 %(refname)' --sort=committerdate
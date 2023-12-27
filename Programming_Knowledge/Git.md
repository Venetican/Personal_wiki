# Usefull commands
**to delete repo locally**
through git bash cd to git repo and then
rm -rf .git (remove recursively (r) & force (f))

**to create develop branch from master**

**to create sample git repo structure**
cookiecruter library
- cookiecutter -c v1 https://github.com/drivendata/cookiecutter-data-science
- multiple layouts for various git repo structures
https://www.cookiecutter.io/

**git chache**
to clear git chache
git rm -r -cached .

**git environments**
working
staging
commit

**File states**
Tracked
- unmodified
- modified
- staging
Untracked

**git commands**
git add FILENAME
git add --all
git add -A
git add .
- puts file to staging, so ready for commit

git commit -m "message"
commit every file which is in staging

git log
shows every information about commits
git log --oneline

git status
shows all files which are in diff with main

git restore
restores all changes in file in diff with main

git rm
remove a file and directly push to staging

git mv
move or rename file and push directly to staging

git diff
shows all diff to last commit

git commit --amend
allows you to make changes to the most recent commit in your repository without creating additional commits

git reset
returns to specific commit hash

git rebase
allows you to completely rewrite the history

git fetch
to update your local repository with changes from a remote repository, 
but without merging those changes into your local branches.
git fetch --prune

git stash
temporarily shelves (or stashes) changes you've made to your working directory, allowing you to work on something else, and then come back and re-apply them later on
git stash list - to get all stashes
git stash apply - last stashed saved - git stash apply stash@{n}
git stash pop - apply most recent stash and then remove it from list

git clean
git clean -n - dry run
git clean -d - directories
git clean -f - force


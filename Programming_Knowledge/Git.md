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
git rm-r-cached .

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

git status
shows all files which are in diff with main

git restore
restores all changes in file in diff with main
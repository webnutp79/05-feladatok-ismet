# Git jegyzet

## Git parancsok

```
git  --version
git config --global --ist
git config --global user.name "Username"
git config --global user.email username@domain.hu

git init Personal

git status

git add .
git add index.html

git commit -m "message"

git commit -am "message"

git add --patch

git log --oneline
git log --oneline --graph
git log
gitk

git checkout 86ef77 index.html

git reset HEAD index.html

git checkout -- .

git checkout -b másik-ág

git merge másik-ág
git rebase másik-ág
git rebase --continue

git rm README.md
git mv css/styles.css assets/css/styles.css

git checkout -B master

git reflog

git diff HEAD HEAD~1

git reset --soft HEAD~1

git branch -d törlendő-ág
```

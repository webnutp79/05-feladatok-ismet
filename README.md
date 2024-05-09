# Git jegyzet

## Git parancsok

```
git  --version
git config --global --list
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
git rebase --abort

git rm README.md
git mv css/styles.css assets/css/styles.css

git checkout -B master

git reflog

git diff HEAD HEAD~1

git reset --soft HEAD~1

git branch -d törlendő-ág
git branch --list
```

### Ha már létezik a fájl a Git repoban, és be akarjuk tenni a .gitignore-ba:

```
#.gitignore
nagyontitkos.txt

#gitbash-ben
git rm nagyontitkos.txt #Töröljük a fájl-t a reporól
git add .gitignore      #Hozzáadjuk .gitignore-t a stage-hez
git commit -m "Nagyon tikos fájl törlése és .gitignore módosítása"  #Commitoljuk a fájltörlést és .gitignore módosítást
git checkout HEAD~1 -- nagyontitkos.txt     #Visszaszerezzük a törölt fájlt
git reset nagyontitkos.txt                  # Törölt fájlt levesszük a stage-ről
```

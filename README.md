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

### GitHub-bal kapcsolatos parancsok

```
#Publikus kulcs létrehozása a saját gépen
ssh-keygen -t rsa -b 4096 -C "email@címed.hu"
cat c/Users/..../id_rsa.pub              #Ide kerül az id_rsa.pub pontos elérési útvonala, a kimenetet másold fel a GitHub-ra kulcsként

#A Git repoban tároltak (főág) feltöltése a GitHub repoba
git remote add origin https://github.com/webnutp79/masodik.git
git branch -M main
git push -u origin main

#GitHub-on tároltak lehúzása a Git-re
git pull
git pull --rebase  #Javasolt a rebase, nem a merge

#Git-en tárotak feltöltése a GitHub-ra
git push origin main

#ÚJ fejlesztési ág feltöltése a GitHub-ra
git checkout -b feature-valami
git push -u origin feature-valami

#Ha GitHub megrendelésre (issue) dolgozunk
git commit -m "Commit Fixes #2"       # A #2 az issue száma
```
## Submodule

### A GitHub Pages-en egedélyezni kell a submodule használatát a ./.github/workflows/static.yml fájlban:
~~~
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        with:
                  submodules: 'true'
~~~

### Submodule repojának beillesztése az eredeti repo-ba és feltöltése GitHub-ra az eredeti repo-ba
~~~
#Submodule repojának hozzáadása a GitHub-ról
git submodule add https://github.com/webnutp79/Submodule-Repo.git

#Kommitolás
git add .
git commit -m "Submodule-Repo hozzáadása"

#Feltöltés GitHub-ra
git push origin main
~~~

### Változtatás végrehajtása után a submodule-on
~~~
#Kommitolás
git add .
git commit -m "változtatás"
git push origin main
~~~

### Változtatás átvezetése az eredeti repo-n
~~~
git submodule update --remote --merge
git add .
git commit -m "submodule update"
git push origin main
~~~


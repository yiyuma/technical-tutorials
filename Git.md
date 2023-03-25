Git ist ein Tool zur Versionierung. 
clone ein Projekt aus remote repository in local repository
```sf
git clone https://github.com/yiyu-qiao/ekl-backend.git
```
Alle Branch werden angezeigt, inklusive Branch aus remote repository
```
git branch -a
```
zeigt alle Branch aus local repository
```sf
git branch
```
zeigt Details vom branch aus local repository mit Namen von upstream branch 
```
git branch -vv
``
zeigt den Status des Projekts
```sf
git status
```
fügt alle Änderungen ins Index hinzu.
```sf
git add .
```
Alle Änderungen werden committed
```sf
git commit -m "user login erweitert"
```
Die beide Operationen aus den letzten Commands 
```sf
git commit -am "user login erweitert"
```
Die Änderungen in local respository werden mit remote repository synchronisiert.
```sf
git push
```
Die Information über remote repository wird synchronisiert.
```sf
git fetch --all
```
working tree von Branch HEAD wird mit remote repository synchronisiert. Sprich, auf dem aktuellen Stand aus remote repository gebracht.
```sf
git pull 
```
Wechsle zu Branch names branch-name
```sf
git switch brach-name
```
erstellt neues Branch mit dem Name branch-name und wechsle zu diesem Branch
```sf
git checkout -b branch-name
```
setzt das Upstream-Branch für das local branch und lädt die Änderungen auf dem remote repository hoch.
```
git push -u origin branch-name
```
löscht den Branch mit dem Name branch-name. -D zwingt das Löschen.
```sf
git branch -d branch-name
```
löscht den Branch mit dem Name branch-name aus dem remote repository. origin ist default name von remote repository.
```sf
git push -d origin branch-name
```

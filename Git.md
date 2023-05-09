Git ist ein Tool zur Versionierung.<br>
Git hat 4 Workspaces: Working directory, index/Stage, local repository, remote repository.<br>
Die Dateien, die git verwaltet, haben 4 Status: untracked, modified, staged, unmodified.<br> 
```
untracked + git add => staged (in stage/indexs)
modified + git add => staged (in stage/indexs)
staged + git commit => unmodified (in local repository)
unmodified + git push => (in remote repository)
staged + git reset => modified (in working directory)
```

Clone ein Projekt aus remote repository in local repository. ".git" Datei ist die remote repository.
```
git clone https://github.com/yiyu-qiao/ekl-backend.git
```
Alle Branch werden angezeigt, inklusive Branch aus remote repository
```
git branch -a
```
Zeigt alle Branch aus local repository
```
git branch
```
Zeigt Details vom branch aus local repository mit Namen von upstream branch 
```
git branch -vv
```
Zeigt den Status aller Dateien des Projekts
```
git status
```
Zeigt den Status der Datei
```
git status filename
```
Fügt alle Änderungen ins Index hinzu.
```
git add .
```
Fügt filename1 und filename2 ins Index hinzu.
```
git add filename1 filename2
```
filename1 wird vom Index zurück zu working directory.
```
git reset filename1
```
delete filename1 aus working directory.
```
git rm filename1
```
Alle Änderungen werden committed
```
git commit -m "user login erweitert"
```
fügt alle Änderungen ins Index hinzu und alle Änderungen werden committed. 
```
git commit -am "user login erweitert"
```
Die Änderungen in local repository werden mit remote repository synchronisiert.
```
git push
```
Die Information über remote repository wird synchronisiert.
```
git fetch --all
```
working tree von Branch HEAD wird mit remote repository synchronisiert. Sprich, auf dem aktuellen Stand aus remote repository gebracht.
```
git pull 
```
Wechsle zu Branch names branch-name
```
git switch brach-name
```
erstellt neues Branch mit dem Name branch-name und wechsle zu diesem Branch
```
git checkout -b branch-name
```
setzt das Upstream-Branch für das local branch und lädt die Änderungen auf dem remote repository hoch.
```
git push -u origin branch-name
```
löscht den Branch mit dem Name branch-name. -D zwingt das Löschen.
```
git branch -d branch-name
```
löscht den Branch mit dem Name branch-name aus dem remote repository. origin ist default name von remote repository.
```
git push -d origin branch-name
```
stash die Änderungen 
```
git stash push -m "stash the changes"
```
Die Änderungen aus Stash mit Index 0 werden angezeigt
```
git stash show 0
```
Alle vorhandene Stash werden angezeigt
```
git stash list
```
Änderungen von Stash mit index 1 werden auf dem HEAD Branch eingesetzt. Das Stash mit index 1 wird gelöscht.
```
git stash pop 1
```
Änderungen von Stash mit index 1 werden auf dem HEAD Branch eingesetzt
```
git stash apply 1
```
Das Stash mit index 1 wird gelöscht
```
git stash drop 1
```
zeigt die Unterschiede zwischen dev und master. stash@{1} kann auch verglichen werden
```
git diff dev master
```
zeigt die letzte 3 Commits
```
git log -n 3
```
zeigt die globale Einstellung von git
```
git config --global --list
```
zeigt die lokale Einstellung von git
```
git config --local --list
```
erstellt ein tag mit dem Name 0.01
```
git tag 0.0.1
```
zeigt alle tags
```
git tag --list
```
erstellt ein tag im remote repository mit dem Name release-1.0.1
```
git push --tag origin release-1.0.1
```
Zeigt dem Name und url von remote repository
```
git remote -v
```
fügt ein remote repository mit name und url hinzu.
```
git remote set-url --add origin https://github.com/yiyuma/familySchedule.git
```
löscht remote repository mit name und url aus der Konfiguration local
```
git remote set-url --delete origin https://github.com/yiyuma/oldProject.git
```


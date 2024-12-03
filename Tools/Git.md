## Git
**Git** is a **distributed version control system (VCS)**.<br>
Git has 4 workspaces: Working directory, Index/Stage, Local repository, Remote repository.<br>
The file in git has 4 states: untracked (in Working directory), modified (in Working directory), staged (in Stage), unmodified (in Local repository).<br> 
```
untracked + git add [path] => staged (in stage/indexs)
staged + git reset [path] => untracked (in working directory)
modified + git add [path] => staged (in stage/indexs)
staged + git reset [path] => modified (in working directory)
staged + git commit -m "message" => unmodified (in local repository)
unmodified + git push => (in remote repository)
```

**Clone** a project from remote repository to local repository. File with the extension ".git" is the remote repository.
```
cd localRepositoryDirectory
git clone https://github.com/yiyuma/technical-tutorials.git
```

**Branch**
- Show all branches in the local repository and in the remote repository.
  ```
  git branch -a
  ```
- Show all branches in the local repository.
  ```
  git branch
  ```
- Show the details of all branches in the local repository mit Namen von upstream branch werden angezeigt.
  ```
  git branch -vv
  ```
- Es wird zu Branch names branch-name gewechselt.
  ```
  git switch brach-name
  ```
- Neues Branch mit dem Name branch-name wird von aktuellem Branch kopiert und zu diesem neuen Branch gewechselt.
  ```
  git checkout -b branch-name
  ```
- setzt das Upstream-Branch für das local branch und lädt die Änderungen auf dem remote repository hoch.
  ```
  git push -u origin branch-name
  or
  git push --set-upstream origin branch-name
  ```
- löscht den Branch in local repository mit dem Name branch-name. -D zwingt das Löschen.
  ```
  git branch -d branch-name
  ```
- löscht den Branch mit dem Name branch-name aus dem remote repository. origin ist default name von remote repository.
  ```
  git push -d origin branch-name
  or
  git push origin :branch-nameq
  ```

**Projekt**
- Der Status aller Dateien des Projekts werden angezeigt.
  ```
  git status
  ```
- Der Status einer Datei wird angzeigt.
  ```
  git status filename
  ```
- Alle Änderungen werden in Index hinzufügt.
  ```
  git add .
  ```
- filename1 und filename2 werden in Index hinzufügt.
  ```
  git add filename1 filename2
  ```
- filename1 wird vom Index zu working directory zurückgesezt.
  ```
  git reset filename1
  ```
- filename1 wird aus working directory gelöscht.
  ```
  git rm filename1
  ```
- Alle Änderungen werden committed
  ```
  git commit -m "comment for the commit"
  ```
- Alle Änderungen werden ins Index hinzufügt und committed. 
  ```
  git commit -am "comment for the add and commit"
  ```
- Die Änderungen in local repository werden mit remote repository synchronisiert.
  ```
  git push
  ```
- Die Information über remote repository wird synchronisiert.
  ```
  git fetch --all
  ```
- Working tree von Branch HEAD wird mit remote repository synchronisiert. Sprich, auf dem aktuellen Stand aus remote repository gebracht.
  ```
  git pull 
  ```
**Stash**<br>


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
pop = apply + drop
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
zeigt die Unterschiede Datei zwischen dev und master. Man kann durch den Command wissen, welche Dateien schon committed, aber noch nicht push sind.
```
git diff --stat dev master
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
git lfs (git large file storage): <br>
1. download git lfs from internet
2. install git lfs
3. in command line (git bash) type command "git lfs install"

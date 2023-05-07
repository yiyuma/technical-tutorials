Wenn man neues Feature arbeitet, wie kann man neuer Branch für das Feature machen?
1. Aktualisierung eines lokalen Branches mit remote repository. 
   ```
   git pull
   ```
2. maven build das Projekt. 
    ```
    mvn clean package
    ```
3. Erstellt einen neuen Branch aus aktuellen lokalen Branch für das neue Feature und wechselt auf diesem Branch.
   ```
    git checkout -b newBranchName
   ```
4. Bearbeiten auf diesem Feature Branch. maven build und testen das Feature Branch.
    ```
    mvn clean package
    ```
5. Push die Änderungen zu remote repository
   ```
   git commit -am -m "Comments"
   git push
    ```


1. clone from remote repository to local workspace
```
git clone https://github.com/yiyu-qiao/ekl-backend.git
```
2. maven build project 
```
   mvn clean package
```
3. create new feature branch
```
    git checkout -b newBranchName
   ```
4. maven build and test the feature branch
```
   mvn clean package
```
5. push changes to remote repository
```
  git push
```
6. pull request from feature branch to dev branch
7. maven build and test pull request with Jenkins
8. merge pull request in dev branch
9. pull request from dev branch to master branch in gitHub
10. merge pull request in master branch
11. maven build and test release candidate with master bran

Create a new repository on the command line
echo "# TestProject" >> README.md
```
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/yiyuma/TestProject.git
git push -u origin main
```

Push an existing repository from the command line
```
git remote add origin https://github.com/yiyuma/TestProject.git
git branch -M main
git push -u origin main
```
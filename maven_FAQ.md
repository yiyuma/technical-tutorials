Was ist Maven?<br>
Maven ist ein Build Tool für Java Projekt. Jedes Maven Projekt hat eine pom.xml Datei. Mit pom.xml kann man das Projekt konfigurieren.<br>
z.B. Mit Elementen groupId, artifactId und Version kann man das Artefakt eines Java Projekts eindeutig festlegen. Mit Element Packaging kann man das Format des Artefakts definieren. Mit Element Dependencies kann man die Abhängigkeiten eines Projekts konfigurieren.

Was kennst du über Repository in Maven?
Maven hat 2 Arten von Repository. local repository und remote repository.<br>
local repository is ein Verzeichnis auf dem lokalen Rechner. Man kann local repository in settings.xml konfigurieren. Man kann remote Repository in pom.xml im Element Repositories konfigurieren. Maven sucht die Abhängigkeit eines Projekts zuerst in local repository. Falls Maven keine Abhängigkeit findet, sucht Maven die Abhängigkeit weiter in remote repository. 

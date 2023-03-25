Maven ist ein Build Tool für Java Projekt.<br> 

## pom.xml
Jedes Maven Projekt hat eine Datei *pom.xml* (POM=Project Object Model). pom.xml enthält die Konfiguration von einem Projekt.
Zur Konfiguration gehören z.B.:
- **groupId, artifactId & version**: Mit diesen Informationen wird das Artifakt eindeutig festgelegt.<br>
- **packaging**: Mit dem Element packaging wird das Format des Artifakts definiert.<br>
- **dependencies**: Das Element dependencies enthält die Abhängigkeiten des Projekts.<br>
- **repositories**: gibt an, welche remote Repository verwendet werden. 
- **properties**: Mit dem Element properties wird Variable definiert. pom.xml verwendet diese Variable.
- **Build**: Hier werden *defaultGoal, directory, finalName, filters, plugins* für Build-Prozess definiert.
- **Profiles**: Hier wird die Build Umgebungen definiert.

## Artifakt
Artifakt ist Endergebnis eines Projekts. Artifakt wird durch Build-Prozess erzeugt, ist sozusagen das Binary des Projekts.


## Maven built-in build lifecycle
maven definiert 3 Lifecycle:<br>
- **clean**: wird die im letzten Mal beim Build erstellten Dateien aufgeräumt.
- **default**: enthält mehrere Phases. Jede Phase hat einen Task. z.B. Die Phase compile kompiliert die source code des Projekts. Die Phase install installiert das Projekt auf dem lokalen Repository.
- **site**: wird die Erstellung der Webseite des Projekts behandelt.

Ein Lifecycle hat mehrere Phases. 
```sh
mvn <PHASE>
```
Maven wird diese Phase und die vorangegangene Phases ausgeführt. 
Eine Phase wird mit goals aus Plugin angebunden. Ein goal ist für ein Task verantwortlich. 
```sh
mvn <PLUGIN>:<GOAL>
```
Maven wird bestimmte goal aus Plugin ausgeführt.

## Repository
Es gibt 2 Arten von Repository, local Repository und remote Repository. <br>
- Local Repository ist ein Verzeichnis auf dem Computer, wo Maven zuerst nach Abhängigkeit sucht.
Das standard Verzeichnis von local Repository ist 
```sh
C:\Users\<User_Name>\.m2
```
Man kann das local Repository auch in der settings.xml Datei unter dem Verzeichnis *C:\Users\<User_Name>\.m2* definiert.
```sh
<settings>
    <localRepository>C:/maven_repository</localRepository>
    ...
```
- Remote Repository kann man im pom.xml definieren. Standard Remote Repository ist maven central (https://repo.maven.apache.org/maven2/.).<br>


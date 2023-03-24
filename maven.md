# Maven tutorial

Maven ist ein Build Tool für Java Projekt.<br> 

## pom.xml
Jedes Maven Projekt hat eine *pom.xml* Datei (POM=Project Object Model), die das Java Projekt konfiguriert. 
Im pom.xml werden folgende Informationen festgelegt:
- **project identifiers (groupId, artifactId, version)**: Mit diesen Informationen wird das Artifakt eindeutig festgelegt.<br>
- **packaging**: Hier wird definiert, mit welchem Dateityp das Artifakt erzeugt wird.<br>
- **dependencies**: Hier werden die Abhängigkeiten der Applikation deklariert.<br>
- **repositories**: Hier werden die Id und Url einer Abhängigkeit eingegeben, die nicht im default remote Repository (Maven central) zur Verfügung steht.
- **properties**: Hier wird die Version der Abhängigkeit definiert.
- **Build**: Hier werden *defaultGoal, directory, finalName, filters, plugins* definiert.
- **Profiles**: Hier wird die Build Umgebungen definiert.

## Maven built-in build lifecycle
maven definiert 3 Lifecycle:<br>
- **clean**: wird alle im letzten Mal gebuildet Dateien aufgeräumt.
- **default**: wird erstelltes Projekt deployment ausgeführt.
- **site**: wird der Erstellung der Webseite behandelt.

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
- Local Repository ist ein Verzeichnis auf dem Computer, auf dem Maven ausgeführt wird. Die vom remote Repository runtergeladene Abhängigkeiten werden im local Repository gespeichert. Das standard Verzeichnis von local Repository ist 
```sh
C:\Users\<User_Name>\.m2
```
Man kann das local Repository auch in der settings.xml Datei unter dem Verzeichnis *C:\Users\<User_Name>\.m2* definiert.
```sh
<settings>
    <localRepository>C:/maven_repository</localRepository>
    ...
```
- Standard Remote RepositoryDie ist maven central (https://repo.maven.apache.org/maven2/.). Aber manche Abhängigkeiten stehen nicht in maven central zur Verfügung. In diesem Fall muss man die Id und Url der Abhängigkeit im Repositories im pom.xml definiert.<br>

Maven sucht zuerst die im pom.xml deklaierte Abhängigkeit in der lokalen Repository. Wenn die Abhängigkeit nicht vorhanden ist, wird maven die Abhängigkeit in der zentralen Repository gesucht und in der lokalen Repository runtergeladen. Wenn die Abhängigkeit nicht in der zentrale Repository vorhanden ist, dann wird in repositories *id* und *url* der Repository deklariert.

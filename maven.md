Maven ist ein Build Tool für Java Projekt.<br> 

### pom.xml
Jedes Maven Projekt hat eine Datei *pom.xml* (POM=Project Object Model). pom.xml enthält die Konfiguration von dem Projekt.
Zur Konfiguration gehören z.B.:
- **groupId, artifactId & version**: Mit diesen Informationen wird das Artefakt eindeutig festgelegt.<br>
- **packaging**: Mit dem Element packaging wird das Format  (jar, war, ear, pom...) des Artefakts definiert.<br>
- **dependencies**: Das Element dependencies enthält die Abhängigkeiten des Projekts. Bei Abhängigkeitsauflösung gewinnt der kürzeste Weg.<br>
- **repositories**: gibt an, welche remote Repository verwendet werden. 
- **properties**: Im Element properties werden Variablen definiert, die im pom.xml verwendet werden können.
- **build**: Das Element Build enthält alle Informationen, die zum Erstellen eines Projekts erforderlich sind. Es enthält das Element plugin.
- **plugins**: analog zu dependencies. Zusätzlich kann man mit dem Element Plugins die verwendete Plugin konfigurieren. z.B. Mit welche Phase soll ein goal angebunden werden. Plugins ist im Element Build.
-  **profiles**: Hier werden Profiles definiert. z.B. remote repository. Profile ist eine Sammlung von Konfigurationen, um eine bestimmte Umgebung zu definieren.
- **distributionManagement**: definiert die remote repositories, wo das gebaute Artefakt gespeichert wird.
- **parent**: definiert das parent Projekt
- **dependencyManagement**: Kommt in der Regel im pom.xml von Parent Projekt und legt die Version der verwendeten Abhängigkeit fest.
- **pluginsManagement**: Analog zu dependencyManagement.


### Maven lifecycle
maven definiert 3 Lifecycle. Maven definiert auch default lifecycle binding.<br> 
- **clean**: Das binay wird damit aufgeräumt. Definiert Phases pre-clean, clean und post-clean
- **default**:definiert die Phases z.B. compile, test, package, install & deploy.
- **site**: Mit lifecycle site wird die Seite von Java doc erstellt.

```sh
mvn <PHASE>
```
Maven wird diese Phase und alle anderen Phases, die vor PHASE im lifecycle stehen, ausführen. 
Ein goal erledigt bestimmte Aufgabe.
```sh
mvn <PLUGIN>:<GOAL>
```
Maven wird bestimmte goal aus Plugin ausführen.

### Repository
Es gibt 2 Arten von Repository, local Repository und remote Repository. <br>
- Local Repository ist ein Verzeichnis auf dem Computer, wo Maven zuerst nach Abhängigkeit sucht.
- Remote Repository: Maven sucht dann in remote repository nach der Abhängigkeit und speichert die gefundene Abhängigkeit in local repository. 

### settings.xml
settings.xml enthält die globale Konfiguration für Maven. z.B. localrepository, repository und profiles.

### Super pom
Maven liefert das super pom, wo die standard Konfiguration von Maven sind. z.B. In der super POM definiert, dass Maven central repository die default plugin repository ist.

### standard directory layout
--src/main/java
--src/main/resource
--src/test/java
--src/test/resource
--target/

### Artefakt (artifact)
Artefakt ist Endergebnis eines Projekts. Artefakt wird durch Build-Prozess erzeugt, ist sozusagen das Binary des Projekts.


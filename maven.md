Maven ist ein Build Tool für Java Projekt.<br> 

### pom.xml
Jedes Maven Projekt hat eine Datei *pom.xml* (POM=Project Object Model). pom.xml enthält die Konfiguration von dem Projekt.
Zur Konfiguration gehören z.B.:
- **groupId, artifactId & version**: Mit diesen Informationen wird das Artefakt eindeutig festgelegt.<br>
- **packaging**: Mit dem Element packaging wird das Format (jar, war, ear, pom...) des Artefakts definiert.<br>
- **dependencies**: Das Element dependencies enthält die Abhängigkeiten des Projekts. Bei Abhängigkeitsauflösung gewinnt der kürzeste Weg.<br>
- **repositories**: gibt an, welche remote Repository verwendet werden. 
- **properties**: Im Element properties werden Variablen definiert, die im pom.xml verwendet werden können.
- **build**: Das Element build enthält alle Informationen, die zum Erstellen eines Projekts erforderlich sind. Es enthält das Element plugin.
- **plugins**: analog zu dependencies. Zusätzlich kann man mit dem Element plugins die verwendeten Plugins konfigurieren. z.B. Mit welche Phase soll ein goal angebunden werden. Plugins ist im Element Build.
-  **profiles**: Hier werden Profiles definiert. z.B. remote repository. Profile ist eine Sammlung von Konfigurationen, um eine bestimmte Umgebung zu definieren.
- **distributionManagement**: definiert die remote repositories, wo das gebaute Artefakt gespeichert wird.
- **parent**: definiert das parent Projekt. Project inheritance.
- **dependencyManagement**: Kommt in der Regel im pom.xml von Parent Projekt und legt die Version der verwendeten Abhängigkeit fest.
- **pluginsManagement**: Analog zu dependencyManagement.


### Maven lifecycle
Maven definiert 3 lifecycle. Die sind clean, default und site. Jede Lifecycle hat mehrere Phases. Jede Phase ist mit ein goal aus plugin angebunden. Ein goal erledigt bestimmte Aufgabe.<br>
Maven definiert auch default lifecycle binding.<br> 
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
- Local Repository ist ein Verzeichnis auf dem Computer, wo Maven zuerst nach Abhängigkeit sucht. Das Verzeichnis für local repository liegt in der settings.xml.
- Remote Repository: Falls Maven die Dependencies nicht in local repository gefunden hat, sucht Maven in remote repository nach sie weiter und speichert die gefundene Dependencies in local repository.<br>
Die URL von remote repository wird im pom.xml im Block "repositories" deklariert. <br>
Mit der Phase install in default lifecycle kann man das gebaute Artefakt in local repository installieren.<br>
Man kann auch im pom.xml die remote repository definieren, wo das gebaute Artefakt gespeichert wird.<br>
Mit der Phase deploy in default Lifecycle kann man das gebaute Artefakt in remote repository hochladen.

### Projekt Inheritance und Projekt Aggregation
Projekt Inheritance: Im pom.xml kann man im Block "parent" die Parent Projekt deklarieren. Das Projekt kann die default Value von Parent Projekt übernehmen, wenn es selber nicht für den Wert definiert. Jedes Projekt kann nur ein Parent Projekt haben.<br>
Projekt Aggregation: Im pom.xml kann man im Block "modules" mehrere Subprojekte deklarieren. Jedes Subprojekt wird im Block "module" deklariert.

### settings.xml
settings.xml enthält die globale Konfiguration für Maven. z.B. localrepository, repository und profiles. Es gibt 2 settings.xml Dateien. Eine ist User level Datei. Dieser Datei ist im Verzeichnis, wo User Information gespeichert ist. Eine ist global level Datei. Diese Datei ist im Verzeichnis, wo Maven installiert. Diese 2 settings.xml zusammenfassen zu einer effektiven settings Datei, wenn Maven aufgerufen ist. User level setting Datei hat höhere Priorität als global lever setting Datei.
```
mvn help:effective-settings
```
effective settings wird angezeigt.

### Super pom
Maven liefert das super pom, wo die Standardkonfiguration von Maven sind. z.B. In der super POM definiert, dass Maven central repository die default plugin repository ist. Super POM ist parent von alle pom Dateien.<br>
Simplest POM ist die pom.xml, die von User für ein Maven projekt definiert. Die muss mindestens ModelVersion, groupId, artifactId und Version enthalten. Effektive POM mergt super pom und simplest pom. Simplest POM hat höhere Priorität.
```
mvn help:effective-pom
```
Effective pom wird angezeigt. Oder in IntelliJ kann man im Kontextmenü->Maven->Show Effective POM

### standard directory layout
--src/main/java
--src/main/resource
--src/test/java
--src/test/resource
--target/
--pom.xml

### Artefakt (artifact)
Artefakt ist Endergebnis eines Projekts. Artefakt wird durch Build-Prozess erzeugt, ist sozusagen das Binary des Projekts.





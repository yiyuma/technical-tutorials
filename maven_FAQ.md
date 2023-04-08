Was ist Maven?<br>
Maven ist ein Build Tool für Java Projekt. Jedes Maven Projekt hat eine pom.xml (Project object model) Datei. In der pom.xml kann man das Projekt konfigurieren. z.B. Mit groupId, artifactId und Version kann man das Artefakt eines Projekts eindeutig festlegen. Mit Packaging kann man das Format des Artefakts definieren. Mit Dependencies kann man die Abhängigkeiten eines Projekts deklarieren. Es gibt noch viele andere Elementen, z.B. Repositories, Properties, Profiles, Build, und so weit und so fort.<br>
Maven hat 2 Arten von Repository, local repository und remote repository.<br>
Maven definiert 3 lifecycle. Die sind clean, default und site.

Was ist pom.xml? Was hat im pom.xml definiert?<br>
Mit pom.xml kann man ein Maven Projekt konfigurieren. z.B. Mit groupId, artifactId und Version kann man das Artefakt eines Projekts eindeutig festlegen. Mit Packaging kann man das Format des Artefakts definieren. Mit Dependencies kann man die Abhängigkeiten eines Projekts deklarieren. Es gibt noch viele andere Elementen, z.B. Repositories, Properties, Profiles, Build, und so weit und so fort.

Was ist Maven Dependency?<br>
Im pom.xml kann man die Abhängigkeiten des Projekts deklarieren. Maven löst die Abhängigkeiten auf. Maven sucht die Abhängigkeit zuerst in local repository. Falls Maven die Abhängigkeit nicht findet, sucht Maven die Abhängigkeit weiter in remote repository und speichert die gefundene Abhängigkeit in local repository.

Was kennst du über Repository in Maven?<br>
Maven hat 2 Arten von Repository, local repository und remote repository.<br>
local repository is ein Verzeichnis auf dem lokalen Rechner. Man kann local repository in settings.xml konfigurieren. Man kann remote Repository in pom.xml konfigurieren. Maven sucht die Abhängigkeit eines Projekts zuerst in local repository. Falls Maven keine Abhängigkeit findet, sucht Maven die Abhängigkeit weiter in remote repository und speichert die gefundene Abhängigkeit in local repository. Mit der Phase install in default lifecycle kann man das gebaute Artefakt in local repository installieren. Man kann auch im pom.xml die remote repository definieren, wo das gebaute Artefakt gepeichert wird. Mit der Phase deploy in default Lifecycle kann man das gebaute Artefakt in remote repository hochladen.

Was kennst du über Maven lifecycle?<br>
Maven definiert 3 lifecycle. Die sind clean, default und site. Jede Lifecycle hat mehrere Phases. Jede Phase ist mit ein goal aus plugin angebunden. Ein goal erledigt bestimmte Aufgabe.<br>
Mit clean wird das Binary aufgeräumt.<br>
Mit site wird die Seite von Java doc erstellt.<br>
default lifecycle hat mehrere Phases. Sie sind Teile von Build Prozess. z.B. Phase compile kompiliert die Source Code. Phase package erstellt das Artefakt des Projekts. Phase install installiert das Artefakt in local repository. Phase deploy lädet das Artefakt in remote repository hoch.
Außerdem definiert Maven default lifecycle bindings. Die definiert, welche Phase mit welchem goal aus Plugin angebunden ist.
Wenn man mvn phase in Command line eingibt, wird Maven die eingebene Phase und die Phases, die vor dieser Phase stehen, ausführen. Vorausgesetzt, die Phase mit ein goal aus Plugin angebunden ist. 

Was ist den Unterschied zwischen Dependencies und DependencyManagement?<br>

Kennst du settings.xml?<br>
Settings.xml Datei enthält die globale Konfiguration für Maven. z.B. local repository, global repository. Es gibt 2 settings.xml Dateien. Eine ist User level Datei. Dieser Datei ist im Verzeichnis, wo User Information gespeichert ist. Eine ist global level Datei. Diese Datei ist im Verzeichnis, wo Maven installiert. Diese 2 settings.xml zusammenfassen zu einer effektiven settings Datei, wenn Maven aufgerufen ist. User level setting Datei hat höhere Priorität als global lever setting Datei.

Was ist Super POM? Was ist simplest POM? Was ist effektive POM?<br>
Maven liefert das super pom, wo die Standardkonfiguration von Maven sind. z.B. In der super POM definiert, dass Maven central repository die default plugin repository ist. Super POM ist parent von alle pom Dateien. 
Simplest POM ist von User für ein Maven projekt definiert. Die muss mindestens Model version, groupId, artifactId und Version enthalten. Effektive POM mergt super pom und simplest pom. Simplest POM hat höhere Priorität.


## Maven tutorial

Maven ist ein Build Tool für Java Projekt.<br> 
In einem Maven Projekt wird eine *pom.xml* Datei (POM=Project Object Model) festgelegt, um das Projekt zu konfigurieren. 
Im pom.xml werden folgende Informationen beschrieben:
- **project identifiers (groupId, artifactId, version)**: Mit diesen Informationen wird das Artifact eindeutig festgelegt.<br>
- **packaging**: Hier wird definiert, mit welchem Dateityp das Artifact exporitert wird.<br>
- **dependencies**: Hier wird die Abhängigkeiten der Applikation deklariert.<br>
- **repositories**: Hier wird Repositories 
Maven bietet 2 Repositories, eine lokale Repository und eine zentrale Repository. Die lokale Repository ist in lokalem Rechner. Die standard zentrale Repository ist maven central (https://repo.maven.apache.org/maven2/.). Maven sucht zuerst die im pom.xml deklaierte Abhängigkeit in der lokalen Repository. Wenn die Abhängigkeit nicht vorhanden ist, wird maven die Abhängigkeit in der zentralen Repository gesucht und in der lokalen Repository runtergeladen. Wenn die Abhängigkeit nicht in der zentrale Repository vorhanden ist, dann wird in repositories id und url der Repository deklariert.
- **properties**: Hier wird die Version der Abhängigkeit definiert.
- **Build**: Hier werden die Information der default Maven goal, das Verzeichnis des kompilierten Projekts und der Name der Applikation definiert.
- **Profiles**: Hier wird die Build Umgebungen definiert.

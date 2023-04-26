Was ist Artefakt?<br>
Artefakt ist Endergebnis eines Projekts. Artefakt wird durch Build-Prozess erzeugt, ist sozusagen das Binary des Projekts.

Was ist POJO?<br>
Plain Old Java Object (POJO) ist eine Java Klasse.
- Sie hat keine Superklasse. 
- Sie implementiert kein Interface.
- Sie annotiert nicht mit Annotation.

Was ist Java Bean?<br>
Java Bean ist eine Java Klasse.
- Sie hat ein public Constructor ohne Argument,
- seine Properties müssen private sein.
- Sie hat public getter und setter.
- Sie muss Interface Serializable implementieren.

Was ist Servlet?<br>
Servlet ist eine Java API, die die HTTP Methoden mit Java spezifiziert. Tomcat ist eine Implementierung von Servlet.<br>

Was ist Rest API?<br>

System properties and Environment variable<BR>
System properties ist Properties von JVM. Java Plattform verwendet ein Properties-Objekt, um ihre eigene Konfiguration zu verwalten. Zu den System Properties gehören Informationen der aktuellen Benutzer, die aktuelle Version der Java Runtime, usw.<br>
```
string propertyValue = System.getProperty(propertyName, defaultVaule);
```
Mit -DpropertyName=newValue kann man den Wert von propertyName ändern.
```
java -Dekl.backend.ws.env=dev -jar C:\YM\Workspaces\Playground\TestProject2\target\TestProject2-1.0-SNAPSHOT.jar  
```
Environment variable ist Umgebungsvariablen von Betriebssystem.<br>
```
string environmentValue = System.getenv(environmentName);
```

Was ist Clean Code?<br>
Man verwendet Clean Code, weil er die Codes einfach verstehen und warten möchte.
- Projektstruktur: z.B. Maven standard directory layout
- Namen Convention: Klassenname ist mit Substantiv, Variablenname ist mit Absicht, Methodenname ist mit Verb.
- Source Datei Struktur: package->import (All static imports, all non-static imports)->(Class variables,instance variables,constructors, methods)
- Indentation: Einrückung ist mit 4 leer Zeichen oder mit ein Tab. 
- Method parameters: soll nicht mehr als 3 Parameter sein. Wenn es mehr als 3 Parametern hat, können die Parameter in einem Objekt definiert werden. Neu definiertes Objekt kann als Parameter für die Methode verwendet werden.
- Hardcoding Teil kann durch Constant oder Enum ersetzt werden, die in Class level oder in eine andere Class definiert werden.
- Comments: 
- Logging: Wo soll man log aufgerufen? Mit welches Loglevel? Mit welche Log-Message?
- Einige Prinzipien können Entwickler helfen, um Clean Code zu schreiben.<br>
  SOLID Prinzipien.<br>
  - Single responsibility: 
    - Eine Klasse, ein Interface oder eine Methode sollte nur eine Verantwortung haben. 
    - Es sollte nur einen Grund geben, warum man eine Klasse ändern möchte.
  - Open/Close: 
    - Eine Klasse sollte offen für Erweiterungen sein, aber geschlossen für Modifikationen. 
    - Man sollte nicht eine Klasse wegen neue Feature ändern.
  - Liskov Substitution:
    - Eine Unterklasse sollte alle Eigenschaften der Oberklasse erfüllen und immer als ein Objekt der Oberklasse verwendbar sein.
    - Eine Unterklasse sollte die Funktionalität der Oberklasse nur erweitern und nicht verändern oder einschränken.
  - Interface segregation: Zu große Interfaces sollten in kleinere Interfaces aufgeteilt werden.<br>
  - Dependency Inversion:
    - Klassen höherer Ebene sollten nicht von Klassen niederer Ebene abhängen. Beide sollten mittels interface abstrahiert werden.
  - Kiss-Prinzip: Keep it simple, stupid: Wir sollten versuchen, den Code so einfach wie möglich zu halten.<br>
  - DRY-Prinzip: Don't repeat yourself: Ein Stück Code sollte nicht im Software immer wiederholt werden.<br>
- TDD (Test Driven Development): Wir beginnen mit dem Design für automatisierter Test. Wenn es fehlschlägt, dann implementieren wir die Funktionen. Vorteil ist, dass wir die erwartete Funktion haben.
- Tools: IntelliJ bietet automatisierte Code Formatters. 

Design Pattern:

Was ist Artefakt?<br>
Artefakt ist Endergebnis eines Projekts. Artefakt wird durch Build-Prozess erzeugt, ist sozusagen das Binary des Projekts.

Was ist POJO?<br>
Plain Old Java Object (POJO) ist eine Java Klasse, die keine Superklasse hat, keine Interface implementiert und keine Annotation verwendet.

Was ist Java Bean?<br>
Java Bean ist eine Java Klasse, die ein public Constructor ohne Argument hat, seine Properties private sind, die public getter und setter hat, die interface Serializable implementieren muss.

Was ist Servlet?<br>
Servlet ist eine Java API, die die HTTP Methoden mit Java spezifiziert. Tomcat ist eine Implementierung von Servlet.

Was ist Clean Code?<br>
Clean Code bedeutet, dass die Codes einfach verständlich sind und anständig wartbar sein sollten.
- Projektstruktur: z.B. Maven standard directory layout
- Namen Convention: Klassenname ist mit Substantiv, Variablenname ist mit Absicht, Methodenname ist mit Verb.
- Source Datei Struktur: package->import (All static imports, all non-static imports)->(Class variables,instance variables,constructors, methods)
- Indentation: Einrückung ist mit 4 leer Zeichen oder mit ein Tab. 
- Method parameters: soll nicht mehr als 3 Parameter sein. Wenn es mehr als 3 Parametern hat, können die Parameters in einem Objekt definiert werden. Neu definiertes Objekt kann als Parameter für die Methode verwendet werden.
- Hardcoding Teil kann durch Constant oder Enum ersetzt werden, die in Class level oder in eine andere Class definiert werden.
- Comments: 
- Logging: Wo soll man log aufgerufen? Mit welches Loglevel? Mit welche Log-Message?
- Einige Prinzipen können Entwickler helfen, um Clean Code zu schreiben.<br>
  SOLID Prinzipen.<br>
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
  - DRY-Prinzi: Don't repeat yourself: Ein Stück Code sollte nicht im Software immer wiederholt werden.<br>
- TDD (Test Driven Development): Wir beginnen mit dem Design für automatisierter Test. Wenn es fehlschlägt, dann implementieren wir die Funktionen. Vorteil ist, dass wir die erwartete Funktion haben.
- Tools: IntelliJ bietet automatisierte Code Formatters. 

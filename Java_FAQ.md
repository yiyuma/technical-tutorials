Was ist JDK, JRE und JVM?<br>
JVM (Java Virtual Machine) ist verantwortlich für Ausführung von Java ByteCode.<br>
JRE (Java Runtime Environment) ist die Laufzeitumgebung und ist unabhängig von Betriebssystem. Sprich, es gibt für jedes Betriebssystem eine entsprechende Version. JRE enthält ein JVM und Libraries Set.<br>
JDK (Java Development Kit) ist das Entwicklungstool für Java. JDK enthält JRE und Development Tool(Debugger + Compiler + JavaDoc).<br>

Was ist Collection? Was ist Java Collection Framework? Welche Interface kennst du in Java Collection Framework?<br>
Collection ist ein Objekt, das mehrere Elemente zu einer einzigen Einheit zusammenfasst.<br>
Java Collection Framework stellt Interfaces und Implementierungen zur Verwaltung von Daten. Root Interface ist Interface Collection<E>. Interface Collection hat Subinterfaces, z.B. List, Set, Map, Queue, Deque, SortedSet, SortedMap.
- Set ist eine Collection, die keine Duplikate erlaubt. HashSet, TreeSet und LinkedSet sind die Implementierungen von Interface Set.
- List ist eine Collection, die Duplikate erlaubt. ArrayList und LinkedList sind die Implementierungen von Interface List. 
- Queue folgt first in first out Regel. 
- Deque (gesprochen Deck) handelt sich um eine Datenstruktur ähnlich Queue oder Stack.
- Map enthält ein key value Paar. HashMap, TreeMap und LinkedMap sind die Implementierungen von Interface Map.
- SortedSet ist ein Set, das die Elemente aufsteigend sortiert und speichert. Die Sortierung erfolgt anhand der natürlichen Sortierung der Elemente oder der vorgegebenen Comparator (Functional Interface, Methode compare(T,T)).
- SortedMap ist analog zu SortedSet.
  
Was ist Functional Programming?<br>
Functional Programming ist ein Programmierparadigma.<br>
Was ist Functional Interface?<br>
Functional Interface 
stellen Zieltype für Lambda expression und Method reference bereit. Functional Interface hat genau eine abstract Methode. Diese abstract Method heißt functional method. Man kann functional Interface mit @FunctionalInterface annotieren.<br>
### java.util.function definiert einige functional interface.
- Fuction<T,R> repräsentiert eine Funktion, die ein Input akzeptiert und ein Ergebnis erzeugt. T ist Datentyp für Argument. R ist Datentyp für Ergebnis. Functional Method ist R apply(T t).
- Consumer<T> repräsentiert eine Operation, die ein Input akzeptiert und kein Ergebnis zurückgibt. T ist Datentyp für Argument. Functional Mehtod ist void accept(T t).
- Predicate<T> repräsentiert ein Predicate(boolean values Function), das ein Argument akzeptiert und ein boolean-Wert zurückgibt. T ist Datentyp für Argument. Functional Method ist boolean test(T).
- Supplier<T> repräsentiert ein Supplier, die kein Argument braucht und ein Ergebnis erzeugt. T ist Datentyp für Ergebnis. Functional Method ist T get().<br>
### java.util package definiert auch einige Functional Interface.
- Comparator<T> vergleichen 2 Objekte. Functional method ist int compare(T o1, T o2)<br>

Was ist Stream?<br>
Steam bietet die Funktionen, die Verarbeitung von Collection vereinfachen. Stream ist eine neue Feature in Java 8 und sein Paketname ist java.util.stream. Die Streams gibt es in 2 Varianten, als sequenzielle (.stream()) und parallele (.parallelStream()) Streams.
Was ist Optional?<br>
Optional erleichert die Prüfung auf Null.<br>
Was ist Lambda Expression?<br>
Lambda expression hat das Format (parameter)->{code block} und kann als Implementierung von Functional Interface verwendet werden.<br>
Was ist Generic?<br>
Generic ermöglicht die Deklaration von Interface und die Definition von Methode ohne auf einen konkreten Datentyp festlegen zu müssen.<br>





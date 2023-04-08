Was ist JDK, JRE und JVM?<br>
JVM (Java Virtual Machine) ist verantwortlich für Ausführung von Java ByteCode.<br>
JRE (Java Runtime Environment) ist die Laufzeitumgebung und ist unabhängig von Betriebsystem. Sprich, es gibt für jedes Betriebsystem eine entsprechende Versionn. JRE enthält ein JVM und Libraries Set.<br>
JDK (Java Development Kit) ist das Entwicklungstool für Java. JDK enthält JRE und Development Tool(Debugger + Compiler + JavaDoc).<br>

Was ist Collection? Was ist Java Collection Framework? Welche Interface kennst du in Java Collection Framework?<br>
Collection ist ein Objekt, das mehrere Elemente zu einer einzigen Einheit zusammenfasst.<br>
Java Collection Framework stellt Interfaces und Implementierungen zur Verwaltung von Daten. Root Interface ist Interface Collection<E>. Interface Collection hat Subinterfaces, z.B. List, Set, Map, Queue, Deque, SortedSet, SortedMap.
- Set ist eine Collection, die keine Duplikate erlaubt.
- List ist eine Collection, die Duplikate erlaubt.
- Queue
- Deque (gesprochen Deck) handelt sich um eine Datenstruktur ähnlich Queue oder Stack.
- Map enthält ein key value Paar.
- SortedSet ist ein Set, das die Elemente aufsteigend sortiert und speichert. Die Sortierung erfolgt anhand der natürlichen Sortierung der Elemente oder der vorgegebenen Comparator (Functional Interface, Methode compare(T,T)).
- SortedMap ist analog zu SortedSet.
  
Was ist Functional Programming?<br>
Functional Programming ist ein Programmierungsparadigma.<br>
Was ist Functional Interface?<br>
Functional Interface stellen Zieltype für Lambda expression und Method reference bereit. Functional Interface hat genau eine abstract Methode. Diese abstract Method heißt functional method. Man kann functional Interface mit @FunctionalInterface annotieren.<br>
java.util.function definiert einige functional interface.
- Fuction<T,R> hat input data type T und output data type R. Functional Method ist R apply(T t)
- Consumer<T> hat input data type T und keine output. Functional Mehtod ist void accept(T t)
- Supplier<T> return mit output data type T. Functional Method ist T get()
- Predicate
Was ist Stream?<br>
Steam bietet die Funktionen, die Verarbeitung von Collection vereinfachen. Stream ist eine neue Feature in Java 8 zum java.util-Package. Die Streams gibt es in 2 Varianten, als sequenzielle (.stream()) und parallele (.parallelStream()) Streams.

  





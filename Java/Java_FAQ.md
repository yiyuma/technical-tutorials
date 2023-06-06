Was ist JDK, JRE und JVM?<br>
JVM (Java Virtual Machine) ist verantwortlich für Ausführung von Java Byte Code.<br>
JRE (Java Runtime Environment) ist die Laufzeitumgebung und ist unabhängig von Betriebssystem. Es gibt für jedes Betriebssystem eine entsprechende Version. JRE enthält ein JVM und Libraries Set.<br>
JDK (Java Development Kit) ist das Entwicklungstool für Java. JDK enthält JRE und Development Tool(Debugger + Compiler + JavaDoc).<br>

Was ist Collection? Was ist Java Collection Framework? Welches Interface kennst du in Java Collection Framework?<br>
Collection ist ein Objekt, dass mehrere Elemente zu einer einzigen Einheit zusammenfasst.<br>
Java Collection Framework stellt Interfaces und Implementierungen zur Verwaltung von Daten. Root Interface ist Interface Collection<E>. Interface Collection hat Subinterfaces, z.B. List, Set, Map, Queue, Deque, SortedSet, SortedMap.
- Set ist eine Collection, die keine Duplikate erlaubt. HashSet, TreeSet und LinkedSet sind die Implementierungen von Interface Set.
- List ist eine Collection, die Duplikate erlaubt. ArrayList und LinkedList sind die Implementierungen von Interface List. 
- Queue folgt first in first out Regel. 
- Deque (gesprochen Deck) handelt sich um eine Datenstruktur ähnlich Queue oder Stack.
- SortedSet ist ein Set, das die Elemente aufsteigend sortiert und speichert. Die Sortierung erfolgt anhand der natürlichen Sortierung der Elemente oder der vorgegebenen Comparator (Functional Interface, Methode compare(T,T)).
- SortedMap ist analog zu SortedSet.
<br>
Neben Interface Collection gibt es ein Interface Map. Map enthält ein key value Paar. HashMap, TreeMap und LinkedMap sind die Implementierungen von Interface Map.
  
Was ist Functional Programming?<br>
Functional Programming ist ein Programmierparadigma.<br>
Was ist Functional Interface?<br>
Functional Interface hat genau eine abstract Methode. Diese abstract Method heißt functional method. Man kann functional Interface mit @FunctionalInterface annotieren.<br>
Man kann für Lambda expression und Method reference Functional Interface verwenden.
### java.util.function definiert einige functional interface.
- Function<T,R> repräsentiert eine Funktion, die ein Input akzeptiert und ein Ergebnis erzeugt. T ist Datentyp für Argument. R ist Datentyp für Ergebnis. Functional Method ist R apply(T t).
- Predicate<T> repräsentiert ein Predicate(boolean values Function), das ein Argument akzeptiert und ein boolean-Wert zurückgibt. T ist Datentyp für Argument. Functional Method ist boolean test(T).
- Consumer<T> repräsentiert eine Operation, die ein Input akzeptiert und kein Ergebnis zurückgibt. T ist Datentyp für Argument. Functional Method ist void accept(T t).
- Supplier<T> repräsentiert ein Supplier, die kein Argument braucht und ein Ergebnis erzeugt. T ist Datentyp für Ergebnis. Functional Method ist T get().<br>
### java.util package definiert auch einige Functional Interface.
- Comparator<T> vergleichen 2 Objekte. Functional method ist int compare(T o1, T o2). Rückgabewert negative => o1<o2, Rückgabewert == 0 => o1 == 02, <br>

Was ist Stream?<br>
Steam bietet die Funktionen, die Verarbeitung von Collection vereinfachen. Stream ist ein neues Feature in Java 8 und sein Paketname ist java.util.stream. Die Streams gibt es in 2 Varianten, als sequenzielle (.stream()) und parallele (.parallelStream()) Streams.<br>

Was ist Optional?<br>
Optional erleichert die Prüfung auf Null.<br>

Was ist Lambda Expression?<br>
Lambda expression hat das Format (parameter)->{code block} und kann als Implementierung von Functional Interface verwendet werden.<br>

Was ist Generic?<br>
Generic ermöglicht die Deklaration von Interface und die Definition von Methode ohne auf einen konkreten Datentyp festlegen zu müssen.<br>

Was ist Reflection?<br>
Reflection bietet die Möglichkeit auf innere Struktur von Java-Klassen zuzugreifen. z.B. Class, Constructor, Method, Field and Annotation.<br>

Was ist Thread? <br>
Thread hat die Methoden run() und start(). Mit run() wird das Runnable im selben Thread durchgeführt, während die Methode start() das Runnable in einem neuen Thread ausführt.<br>
- Interface Runnable ist ein Functional Interface. Functional Method ist run(). run() hat keine Parameter und Rückgabewert. Es ist im package java.lang definiert.
- Interface Callable<V> ist ein Functional Interface. Functional Method ist V call() throws Exception. Es ist im package java.util.concurrent.<br>

Was ist LocalDateTime?<br> 
LocalDateTime stellt API zur Verwaltung von Date und Time zur Verfügung.
- Die Method LocalDateTime.now() liefert die aktuelle Zeit aus dem System Zeit Zone. 
- Mit dem Method LocalDateTime.now(ZoneId.of("Asia/Shanghai")) wird die Zeit von Shanghai erzeugt. 
- Mit DateTimeFormatter.ofPattern("yyyy MM dd HH:mm:ss") wird die Zeit formatiert.

Java Runtime Environment (JRE) ist die Laufzeitumgebung von Java, ist unabhängig von Betriebsystem. Sprich, es gibt für jedes Betriebsystem eine entsprechende Version. 
JRE enthält ein Java Virtual Machine (JVM), welches für Ausführung von Java Bytecode verantwortlich ist. 
Jave Development Kit (JDK) ist das Entwicklungstool für Java und beinhaltet auch JRE.<br>

Java Collecion Framework stellt Interfaces und Implementierungen zur Verwaltung von Daten. Die Interfaces List, Set, Map, Queue, Deque, SortedSet, SortedMap.
-- Deque (gesprochen Deck) handelt sich um eine Datenstruktur ähnlich Queue oder Stack.
-- Set ist ähnlich wie List, aber erlaubt keine Duplikate.
-- Map enthält ein key value Paar.
-- SortedSet ist ein Set, das die Elemente aufsteigend sortiert und speichert. Die Sortierung erfolgt anhand der natürlichen Sortierung der Elemente oder der vorgegebenen Comparator (Functional Interface, Methode compare(T,T)).
-- SortedMap ist analog zu SortedSet.

Functional Interface ist ein Interface, das genau eine abstrakte Methode hat. Der Vorteil ist, dass ein lamda expression als Implementierung von Functional Interface eingesetzt werden kann. Falls eine abstrakte Methode eines Interface eine public Mehtode von Klasse Object überschreibt, zählt diese Methode nicht als abstrakte Methode.
```
Comparator
int compare(T,T);
```
<? super T> bedeutet, ? ist super class vom T. Sprich, ? ist assignable from T.
<? extends V> bedeutet, ? erweitert V, sprich V ist super class von ?.
```
Function<T,R>
R apply(T);
default <V> Function<T,V> andThen(Function<? super R,? extends V> after)
```
```
BiFunction<T, U, R> 
R apply(T,U);
```
```
Supplier<T>
T get();
```
```
Consumer<T>
void accept(T);
```
```
Predicate<T>
bool test(T);
```

Lambda expression hat das Format (parameter)->{code block} und kann als Implementierung von Functional Interface verwendet werden.

Stream bietet die Funktionen, die Verarbeitung von Collection vereinfacht.
```
<R> Stream<R> map(Function<? super T, ? extends R> mapper);
List<int> result = list.stream().map(i->i+1).collect(Collectors.toList());
```
```
Stream<T> filter(Predicate<? super T> predicate);
List<String> hasValue = stringList.stream().filter(i->i.contains("value")).collect(Collectors.toList());
```
```
void forEach(Consumer<? super T> action);
```
```
stringList.parallelStream().map(s->s.subString(0,3)).collect(Collectors.toList());
```

Optional erleichert die Prüfung auf Null.
```
optional.of(user);
optional.ofNullable(user).isPresent();
optional.ofNullable(user).orElseThrow(new IllegalArgumentException());
```

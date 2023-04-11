Java Runtime Environment (JRE) ist die Laufzeitumgebung von Java, ist unabhängig von Betriebsystem. Sprich, es gibt für jedes Betriebsystem eine entsprechende Version. 
JRE enthält ein Java Virtual Machine (JVM), welches für Ausführung von Java Bytecode verantwortlich ist. 
Java Development Kit (JDK) ist das Entwicklungstool für Java und beinhaltet auch JRE.<br>

Java Collecion Framework stellt Interfaces und Implementierungen zur Verwaltung von Daten. Die Interfaces List, Set, Map, Queue, Deque, SortedSet, SortedMap.
- Deque (gesprochen Deck) handelt sich um eine Datenstruktur ähnlich Queue oder Stack.
- Set ist ähnlich wie List, aber erlaubt keine Duplikate.
- Map enthält ein key value Paar.
- SortedSet ist ein Set, das die Elemente aufsteigend sortiert und speichert. Die Sortierung erfolgt anhand der natürlichen Sortierung der Elemente oder der vorgegebenen Comparator (Functional Interface, Methode compare(T,T)).
- SortedMap ist analog zu SortedSet.

Functional Interface ist ein Interface, das genau eine abstrakte Methode hat. Der Vorteil ist, dass ein lambda expression als Implementierung von Functional Interface eingesetzt werden kann. Falls eine abstrakte Methode eines Interface eine public Mehtode von Klasse Object überschreibt, zählt diese Methode nicht als abstrakte Methode.
```
Comparator<T>
int compare(T o1,T o2); 
Wenn Rückgabewert einen negative Integer ist, bedeutet o1 kleiner als o2 ist.
Wenn Rückgabewert gleich 0 ist, bedeutet o1 gleicht wie o2 ist.
Wenn Rückgabewert einen positive Integer ist, bedeutet o1 größer als o2 ist.
```

```
Function<T,R>
R apply(T);
default <V> Function<T,V> andThen(Function<? super R,? extends V> after)
<? super T> bedeutet, ? ist super class vom T. Sprich, ? ist assignable from T.
<? extends V> bedeutet, ? erweitert V, sprich V ist super class von ?.
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
Stream<T> sorted(Comparator<? super T> comparator);
Comparator<Double> doubleComparator = (d1, d2) -> {return d1.compareTo(d2);};
List<Double> sortedList = doubleList.stream().filter(doubleComparater).collect(Collectors.toList());
```
```
void forEach(Consumer<? super T> action);
```
```
stringList.parallelStream().map(s->s.subString(0,3)).collect(Collectors.toList());
```

Optional erleichert die Prüfung auf Null.
```
Optional.of(user);
Optional.ofNullable(user).isPresent();
Optional.ofNullable(null).isEmpty(); isEmpty() in Java 11
Optional.ofNullable(null).orElseThrow(new IllegalArgumentException()); Ab Java 10 can orElseThrow() method ohne Parameter haben. Wenn optional leer is, ist NoSuchElementException geworfen. 
```
Generic ermöglicht die Deklaration von Interface und die Definition von Methode ohne auf einen konkreten Datentyp festlegen zu müssen.

Reflection bietet die Möglichkeit auf innere Struktur von Java-Klassen zuzugreifen. z.B. Class, Constructor, Method, Field and Annotation.

**Plain Old Java Object (POJO)** ist eine Java Klasse, die keine Superklasse hat, keine Interface implementiert und keine Annotation verwendet.

**Java Beans** ist eine Java Klasse, die public setter und getter hat, default Constructor hat und Interface Serializable implmentiert.

**Thread** hat die Methoden run() und start(). Mit run() wird das Runnable im selben Thread durchgeführt, während die Methode start() das Runnable in einem neuen Thread ausführt. 
**Exeucator**,**ExecutorService** und **ScheduledExecutorService** sind die Interfaces aus dem Concurrency Framework. **ScheduledThreadPoolExecutor** ist die Implementierung und stellt die Methoden scheduleWithFixedDaly(Runnable/Callable, long, long, TimeUnit) and scheduleWithFixRate(Runnable/Callable, long, long, TimeUnit).

**LocalDateTime** stellt API zur Verwaltung von Date und Time zur Verfügung. Die Method LocalDateTime.now() liefert die aktuelle Zeit aus dem System Zeit Zone. Mit dem Method LocalDateTime.now(ZoneId.of("Asia/Shanghai")) wird die Zeit von Shanghai erzeugt. Mit DateTimeFomatter.ofPattern("yyyy MM dd HH:mm:ss") wird die Zeit formattiert.

Java 11 hat neue Methode bei String, z.B. isBlank(),lines, strip, stripLeading, stripTrailing. Neue Methode Predicate.not(Predicate)
```
listString.filter(Predicate.not(s -> s.isBlank()))
== 
listString.filter(s -> !s.isBlank())
```
Collection hat eine neue Methode toArray() 
```
List sampleList = Arrays.asList("Java", "Kotlin");
String[] sampleArray = sampleList.toArray(String[]::new);
assertThat(sampleArray).containsExactly("Java", "Kotlin");
```
Java 17 hat bei switch-statement Lambda expression.

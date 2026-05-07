# Java - Core Concepts

## Collections Cheat Sheet

| Interface | Implementation | Ordered? | Duplicates? | Thread-safe? | Use When |
|---|---|---|---|---|---|
| List | ArrayList | Yes (index) | Yes | No | Random access, most common |
| List | LinkedList | Yes (index) | Yes | No | Frequent insert/delete at ends |
| Set | HashSet | No | No | No | Fast lookup, uniqueness |
| Set | LinkedHashSet | Insertion order | No | No | Unique + order preserved |
| Set | TreeSet | Sorted | No | No | Sorted unique elements |
| Map | HashMap | No | Keys: No | No | Most common key-value |
| Map | LinkedHashMap | Insertion order | Keys: No | No | LRU cache implementation |
| Map | TreeMap | Sorted by key | Keys: No | No | Range queries on keys |
| Queue | PriorityQueue | By priority | Yes | No | Min/Max heap |
| Queue | ArrayDeque | FIFO/LIFO | Yes | No | Stack or Queue (faster than Stack) |

## String / StringBuilder / StringBuffer

| Type | Mutable? | Thread-safe? | Use When |
|---|---|---|---|
| String | No (immutable) | Yes | Small, few modifications |
| StringBuilder | Yes | No | Loop concatenation (single thread) |
| StringBuffer | Yes | Yes | Loop concatenation (multi thread) |

## Equals & HashCode Contract
```java
// RULE: If a.equals(b) → a.hashCode() == b.hashCode()
// Always override BOTH together
@Override
public boolean equals(Object o) {
    if (this == o) return true;
    if (o == null || getClass() != o.getClass()) return false;
    MyClass that = (MyClass) o;
    return Objects.equals(this.id, that.id);
}

@Override
public int hashCode() {
    return Objects.hash(id);
}
```

## Comparable vs Comparator

```java
// Comparable — natural ordering (inside the class)
class Student implements Comparable<Student> {
    public int compareTo(Student o) {
        return this.name.compareTo(o.name);
    }
}

// Comparator — custom ordering (outside the class)
students.sort(Comparator.comparing(Student::getAge).reversed());
```

## Functional Interfaces (Lambda)

| Interface | Method | Use |
|---|---|---|
| `Predicate<T>` | `boolean test(T)` | Filter |
| `Function<T,R>` | `R apply(T)` | Transform |
| `Consumer<T>` | `void accept(T)` | forEach |
| `Supplier<T>` | `T get()` | Factory/lazy init |
| `BiFunction<T,U,R>` | `R apply(T,U)` | Two-arg transform |

## Stream API

```java
list.stream()
    .filter(x -> x > 10)           // Predicate
    .map(x -> x * 2)               // Function
    .sorted()                       // natural order
    .distinct()                     // remove dups
    .limit(5)                       // first 5
    .collect(Collectors.toList());  // terminal

// Common collectors
Collectors.groupingBy(Student::getCity)
Collectors.partitioningBy(s -> s.getAge() > 18)
Collectors.joining(", ")
Collectors.toMap(Student::getId, Student::getName)
```

## My Notes
<!-- Add your own observations, mistakes, and learnings below -->

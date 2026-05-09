# Java - OOP & Misc

## OOP Quick Recap

| Concept | One-liner | Interview Example |
|---|---|---|
| **Encapsulation** | Hide data, expose via methods | Private fields + public getters/setters |
| **Abstraction** | Hide complexity, show essentials | Interface / Abstract class |
| **Inheritance** | Reuse parent behavior | `extends` (class), `implements` (interface) |
| **Polymorphism** | Same method, different behavior | Method overriding (runtime), overloading (compile) |

## Abstract Class vs Interface

| Feature | Abstract Class | Interface |
|---|---|---|
| Methods | Abstract + concrete | Abstract + default (Java 8+) |
| Variables | Any type | `public static final` only |
| Constructor | Yes | No |
| Inheritance | Single (`extends`) | Multiple (`implements`) |
| Use when | Shared state + behavior | Contract / capability |

## Exception Hierarchy
```
Throwable
├── Error (don't catch: OutOfMemoryError, StackOverflowError)
└── Exception
    ├── Checked (must handle: IOException, SQLException)
    └── RuntimeException / Unchecked (NullPointer, ArrayIndex, ClassCast)
```

## Generics
```java
// Bounded type
<T extends Comparable<T>>  // T must implement Comparable

// Wildcards
List<?>                    // unknown type (read-only)
List<? extends Number>     // Number or subclass (producer)
List<? super Integer>      // Integer or superclass (consumer)

// PECS: Producer Extends, Consumer Super
```

## Java Memory Model
```
Heap (shared)              Stack (per thread)
├── Young Gen              ├── Local variables
│   ├── Eden               ├── Method params
│   ├── S0, S1             └── Return addresses
└── Old Gen
```

- **String Pool** — in Heap, reuses string literals
- **GC:** Mark & Sweep → Young GC (minor) → Old GC (major/full)

## Java 8+ Key Features

| Feature | Example |
|---|---|
| Lambda | `(a, b) -> a + b` |
| Stream API | `list.stream().filter().map().collect()` |
| Optional | `Optional.ofNullable(val).orElse(default)` |
| Method Reference | `list.forEach(System.out::println)` |
| Default methods | `default void log() { }` in interface |

## My Notes
<!-- Add your own observations, mistakes, and learnings below -->

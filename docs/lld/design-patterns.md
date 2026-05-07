# LLD - Design Patterns

## When to Use Which Pattern

| Pattern | Use When | Example |
|---|---|---|
| **Strategy** | Multiple algorithms, swap at runtime | Payment modes, sorting strategies |
| **Observer** | One-to-many notifications | Event listeners, pub-sub |
| **Factory** | Create objects without exposing creation logic | VehicleFactory, ShapeFactory |
| **Singleton** | One instance globally | DB connection, Logger |
| **Decorator** | Add behavior dynamically without subclassing | Pizza toppings, I/O streams |
| **Command** | Encapsulate request as object, undo/redo | Remote control, task queue |
| **State** | Object behavior changes with internal state | Vending machine, traffic light |
| **Proxy** | Control access to an object | Caching proxy, access control |
| **Builder** | Complex object construction step-by-step | Query builder, meal builder |
| **Adapter** | Make incompatible interfaces work together | Legacy system integration |

## SOLID Principles (One-liner each)

| Principle | Meaning | Violation Smell |
|---|---|---|
| **S** - Single Responsibility | One class = one reason to change | God class doing everything |
| **O** - Open/Closed | Open for extension, closed for modification | if-else chains for new types |
| **L** - Liskov Substitution | Subtypes must be substitutable for base | Square extending Rectangle breaks |
| **I** - Interface Segregation | Small focused interfaces | Forcing empty method implementations |
| **D** - Dependency Inversion | Depend on abstractions, not concretions | `new ConcreteClass()` everywhere |

## LLD Interview Template

```
1. Clarify Requirements (2 min)
   → Who are the actors? What actions?

2. Identify Core Objects/Entities (3 min)
   → Nouns = classes, Verbs = methods

3. Define Relationships (3 min)
   → Has-a, Is-a, Uses

4. Write Class Diagram (5 min)
   → Classes, fields, methods, interfaces

5. Identify Design Patterns (2 min)
   → Which patterns fit naturally?

6. Code Key Classes (15 min)
   → Focus on core logic, not boilerplate
```

## My Notes
<!-- Add your own observations, mistakes, and learnings below -->

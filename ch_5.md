# Unit V: Design Patterns and Reuse

---

## 5.1 Reuse Concepts

> **Past Questions:**
> - **[Old1]** How does delegation reduce tight coupling between classes? Give an example of a design pattern that applies delegation. _(Q5ai)_
> - **[Old1]** What problem can occur if implementation inheritance is overused, and how does the Liskov Substitution Principle (LSP) help? _(Q5aii)_
> - **[Internal1]** Write short notes on: Reusability. _(Q7a)_
> - **[Internal3]** What is the Liskov Substitution Principle? Explain with an example where violating LSP causes issues. _(Q5a OR)_

### Software Reusability

**Reusability** is the degree to which existing software components (classes, modules, libraries, frameworks, patterns) can be used in new applications with little or no modification. It is a core goal of software engineering because it reduces development time, cost, and defects.

**Levels of reuse:**
- **Code reuse** — using existing classes, functions, or libraries directly.
- **Design reuse** — applying proven design patterns to solve recurring problems.
- **Architecture reuse** — adopting established architectural styles (e.g., MVC, microservices).
- **Framework reuse** — building on top of existing frameworks (e.g., Spring, Django, React).

### Application Objects vs. Solution Objects

**Application (Domain) Objects:** Represent real-world entities from the problem domain. Identified by domain experts and stakeholders.
- Examples: `Customer`, `Order`, `Book`, `Patient`, `Invoice`.

**Solution Objects:** Represent technical components that don't exist in the problem domain but are needed to implement the system. Identified by developers.
- Examples: `DatabaseConnector`, `Logger`, `ThreadPool`, `EventDispatcher`, `AuthenticationManager`.

Solution objects are prime candidates for reuse across projects because they solve common technical problems independent of any specific business domain.

### Specification Inheritance vs. Implementation Inheritance

**Specification (Interface) Inheritance:**
- A subclass inherits only the **interface** (method signatures) from a parent class or interface.
- It defines a **contract** — the subclass promises to provide behavior conforming to the interface.
- Focus is on **substitutability** — any subclass can be used wherever the parent type is expected.
- Achieved through interfaces or abstract classes with purely abstract methods.
- Example: `PaymentMethod` interface declares `processPayment()`. Both `CreditCard` and `PayPal` implement this interface, each with their own logic.

**Implementation Inheritance:**
- A subclass inherits both the **interface and the code** (method implementations) from a parent class.
- Provides **code reuse** — child classes get functionality "for free."
- Creates **tight coupling** — changes to the parent class can break all subclasses.
- Example: `ArrayList` extends `AbstractList`, inheriting shared list operations.

**Problems with overusing implementation inheritance:**
- **Fragile base class problem** — modifying the parent class may unexpectedly break subclass behavior.
- **Deep hierarchies** — complex inheritance chains become hard to understand, maintain, and debug.
- **Inappropriate "is-a" relationships** — forcing inheritance when the classes don't have a true "is-a" relationship leads to design flaws and LSP violations.
- **Reduced flexibility** — inheritance is a compile-time, permanent relationship. You cannot change the parent of a class at runtime.

**Guideline:** Prefer specification inheritance (interfaces) over implementation inheritance. Use implementation inheritance only when there is a genuine "is-a" relationship and shared behavior.

### Delegation

**Delegation** is a design technique where an object handles a request by forwarding it to a helper object (the **delegate**) rather than implementing the behavior itself. It achieves reuse through **composition** ("has-a") rather than inheritance ("is-a").

**How delegation reduces tight coupling:**
- The delegating class depends on an **interface**, not a concrete implementation.
- The delegate can be **swapped at runtime** — different behavior without modifying the delegating class.
- The delegating class only exposes functionality it explicitly forwards, not the entire API of another class.
- No fragile base class problem — changing the delegate's internals doesn't break the delegating class.

**Delegation vs. Inheritance:**

| Aspect | Inheritance | Delegation |
|---|---|---|
| Relationship | "is-a" (compile-time) | "has-a" (runtime composable) |
| Coupling | Tight (subclass depends on parent internals) | Loose (depends on interface only) |
| Flexibility | Fixed at compile time | Delegate swappable at runtime |
| API exposure | Inherits entire parent API | Exposes only explicitly forwarded methods |

**Example — Delegation with Strategy Pattern:**
Instead of `Duck extends FlyingBird` (inheritance), use `Duck` has-a `FlyBehavior` (delegation). A `Duck` object holds a reference to a `FlyBehavior` interface. At runtime, you can set it to `FlyWithWings` or `NoFly` — the duck's flying behavior changes without any class hierarchy modification. The Strategy pattern is a classic example of delegation in action.

### Liskov Substitution Principle (LSP)

**Definition:** Objects of a superclass should be **replaceable** with objects of its subclasses without altering the correctness of the program. If `S` is a subclass of `T`, then objects of type `T` can be replaced with objects of type `S` without breaking the application.

**Formally:** Subtypes must be substitutable for their base types.

**Why LSP matters:**
- It ensures that inheritance hierarchies are semantically correct, not just syntactically correct.
- Violating LSP leads to unexpected behavior, runtime errors, and code that requires type-checking (`instanceof` checks), defeating the purpose of polymorphism.

**Classic LSP Violation — Rectangle-Square Problem:**

```
class Rectangle:
    width, height
    setWidth(w): width = w
    setHeight(h): height = h
    area(): return width * height

class Square extends Rectangle:
    setWidth(w): width = w; height = w   // Square enforces width == height
    setHeight(h): width = h; height = h
```

Client code:
```
r = getShape()    // could return Rectangle or Square
r.setWidth(5)
r.setHeight(10)
assert r.area() == 50   // FAILS if r is a Square (area = 100, not 50)
```

A `Square` violates LSP because it **changes the expected behavior** of `setWidth()` and `setHeight()`. Code written for `Rectangle` breaks when a `Square` is substituted.

**How to fix:** Don't make `Square` extend `Rectangle`. Instead, use separate classes implementing a common `Shape` interface, or use composition. The violation occurred because a Square "is-not-a" Rectangle in terms of behavior, even though it is geometrically.

**LSP compliance checklist:**
- The subclass must honor the parent's contract (preconditions, postconditions, invariants).
- The subclass should not throw unexpected exceptions.
- The subclass should not weaken postconditions or strengthen preconditions.

---

## 5.2 Common Design Patterns

> **Past Questions:**
> - **[Old2]** Discuss Factory and Abstract Factory patterns. How do they help create objects flexibly? _(Q4b)_
> - **[Old2]** Discuss Strategy and Command patterns. How do they decouple behavior from objects? _(Q4b OR)_
> - **[Internal1]** Define design patterns. Describe types and usage. _(Q5a)_
> - **[Internal2]** Explain the Adapter design pattern with example. _(Q5a)_
> - **[Internal3]** What is the Factory Method pattern? How does it promote flexibility? Drawbacks? _(Q5a)_
> - **[Internal3]** Define "Design Pattern." Three main categories. How do patterns promote reuse and maintainability? _(Q5b)_

### What is a Design Pattern?

A design pattern is a **reusable, proven solution** to a commonly occurring problem in software design. It is not finished code — it is a template or blueprint describing how to solve a problem that can be adapted to many situations.

**Origin:** The concept was popularized by the "Gang of Four" (GoF) — Gamma, Helm, Johnson, Vlissides — in their 1994 book *"Design Patterns: Elements of Reusable Object-Oriented Software."*

**Why design patterns matter:**
- **Proven solutions** — patterns have been tested and refined by the software engineering community over decades.
- **Common vocabulary** — saying "use a Factory here" immediately communicates a design idea to any developer familiar with patterns.
- **Reuse at the design level** — patterns promote code reuse, maintainability, and flexibility by applying established structural relationships.
- **Reduced coupling** — most patterns aim to decouple components, making systems easier to modify and extend.

### Three Categories of Design Patterns

**Creational Patterns** — deal with **object creation** mechanisms, providing flexibility in what gets created, who creates it, and how.
- Examples: Factory Method, Abstract Factory, Singleton, Builder, Prototype.

**Structural Patterns** — deal with **object composition**, defining how classes and objects are assembled into larger structures.
- Examples: Adapter, Composite, Bridge, Decorator, Facade, Proxy.

**Behavioral Patterns** — deal with **communication and responsibility** between objects, defining how objects interact and distribute behavior.
- Examples: Strategy, Command, Observer, State, Template Method, Iterator.

---

### Creational Patterns

### Factory Method Pattern

**Intent:** Define an interface for creating an object, but let **subclasses decide** which class to instantiate. The Factory Method defers instantiation to subclasses.

**Problem it solves:** Client code needs to create objects but shouldn't be tightly coupled to specific concrete classes. Directly using `new ConcreteClass()` throughout the code makes it rigid and hard to extend.

**Structure:**
- **Product** (interface) — defines the interface of objects the factory creates.
- **ConcreteProduct** — implements the Product interface.
- **Creator** (abstract class) — declares the factory method `createProduct()` which returns a `Product`.
- **ConcreteCreator** — overrides `createProduct()` to return a specific `ConcreteProduct`.

**Example — Notification System:**
```
interface Notification { send(message) }
class EmailNotification implements Notification { send(msg) { /* send email */ } }
class SMSNotification implements Notification { send(msg) { /* send SMS */ } }

abstract class NotificationFactory { abstract createNotification(): Notification }
class EmailFactory extends NotificationFactory { createNotification() { return new EmailNotification() } }
class SMSFactory extends NotificationFactory { createNotification() { return new SMSNotification() } }
```
Client code calls `factory.createNotification().send("Hello")` — it doesn't know or care whether it gets an email or SMS notification.

**Benefits:** Promotes flexibility (add new products without changing existing code), follows Open/Closed Principle.
**Drawbacks:** Increases number of classes; can be overkill for simple scenarios.

### Abstract Factory Pattern

**Intent:** Provide an interface for creating **families of related objects** without specifying their concrete classes. Often called a "factory of factories."

**Problem it solves:** When a system needs to produce multiple related products that must be used together (e.g., a UI toolkit where buttons, menus, and scrollbars must all match the same theme).

**Structure:**
- **AbstractFactory** — declares methods for creating each type of abstract product (`createButton()`, `createMenu()`).
- **ConcreteFactory** — implements the creation methods for a specific family (e.g., `DarkThemeFactory`, `LightThemeFactory`).
- **AbstractProduct** — interface for each type of product (e.g., `Button`, `Menu`).
- **ConcreteProduct** — specific implementation (e.g., `DarkButton`, `LightButton`).
- **Client** — uses only the abstract interfaces; doesn't know concrete classes.

**Example — Cross-platform GUI:**
```
interface GUIFactory { createButton(): Button; createCheckbox(): Checkbox }
class WindowsFactory implements GUIFactory { createButton() → WindowsButton; createCheckbox() → WindowsCheckbox }
class MacFactory implements GUIFactory { createButton() → MacButton; createCheckbox() → MacCheckbox }
```
The client receives a factory and calls `factory.createButton()` — guaranteed to get a button consistent with the platform.

**Benefits:** Ensures compatibility among products in a family, isolates concrete classes from client.
**Drawbacks:** Adding a new product type requires changing all factory interfaces and implementations.

---

### Structural Patterns

### Adapter Pattern

**Intent:** Convert the interface of a class into another interface that clients expect. Adapter lets classes work together that otherwise couldn't due to **incompatible interfaces**.

**Analogy:** A travel power adapter that lets a European plug fit into a US socket.

**Problem it solves:** You want to use an existing class (or third-party library), but its interface doesn't match what your code expects. You cannot modify the existing class.

**Structure:**
- **Target** — the interface the client expects.
- **Adaptee** — the existing class with an incompatible interface.
- **Adapter** — implements the Target interface and internally delegates calls to the Adaptee.

**Example:**
```
interface MediaPlayer { play(filename) }      // Target — what client expects
class VLCPlayer { playVLC(filename) { ... } }  // Adaptee — incompatible interface

class MediaAdapter implements MediaPlayer {    // Adapter
    vlc = new VLCPlayer()
    play(filename) { vlc.playVLC(filename) }   // translates the call
}
```
Client code calls `player.play("song.vlc")` — the adapter translates this into `vlc.playVLC("song.vlc")`.

**Benefits:** Reuses existing classes without modification; follows Single Responsibility and Open/Closed principles.

### Composite Pattern

**Intent:** Compose objects into **tree structures** to represent part-whole hierarchies. Composite lets clients treat individual objects and compositions of objects **uniformly**.

**Problem it solves:** You have a hierarchical structure (like a file system, organization chart, or menu) and want to treat leaves (single items) and branches (groups) through the same interface.

**Structure:**
- **Component** — common interface for all objects in the tree (`display()`, `getSize()`).
- **Leaf** — a single object with no children (e.g., `File`).
- **Composite** — a container that holds children (both leaves and other composites) and implements component operations by delegating to children (e.g., `Directory`).

**Example — File System:**
```
interface FileSystemComponent { display(); getSize() }
class File implements FileSystemComponent { display() { print name }; getSize() { return size } }
class Directory implements FileSystemComponent {
    children: List<FileSystemComponent>
    add(component); remove(component)
    display() { for child in children: child.display() }
    getSize() { return sum of child.getSize() }
}
```
A `Directory` can contain `File`s and other `Directory`s. Calling `display()` on a directory recursively displays all contents.

**Benefits:** Simplifies client code (no type-checking); makes it easy to add new component types.

### Bridge Pattern

**Intent:** Decouple an **abstraction** from its **implementation** so that the two can vary independently.

**Problem it solves:** When a class varies in two independent dimensions, using inheritance for both creates a combinatorial explosion of subclasses. For example, `Shape` × `Color` gives: `RedCircle`, `BlueCircle`, `RedSquare`, `BlueSquare`, etc.

**Structure:**
- **Abstraction** — defines the high-level interface and holds a reference to an Implementor.
- **RefinedAbstraction** — extends the Abstraction (e.g., `Circle`, `Square`).
- **Implementor** — defines the interface for implementation classes.
- **ConcreteImplementor** — provides specific implementations (e.g., `RedColor`, `BlueColor`).

**Example:**
```
interface Color { applyColor() }
class Red implements Color { applyColor() { "apply red" } }
class Blue implements Color { applyColor() { "apply blue" } }

abstract class Shape { color: Color; abstract draw() }
class Circle extends Shape { draw() { "draw circle with " + color.applyColor() } }
class Square extends Shape { draw() { "draw square with " + color.applyColor() } }
```
Adding a new color or a new shape requires only one new class, not an entire matrix of combinations.

**Benefits:** Eliminates subclass explosion; abstraction and implementation evolve independently.

---

### Behavioral Patterns

### Strategy Pattern

**Intent:** Define a family of algorithms, encapsulate each one, and make them **interchangeable**. Strategy lets the algorithm vary independently from clients that use it.

**Problem it solves:** A class needs to perform a task in multiple ways, and you want to switch between them at runtime without modifying the class.

**Structure:**
- **Context** — maintains a reference to a Strategy object and delegates the algorithm execution to it.
- **Strategy** (interface) — declares the method(s) common to all supported algorithms.
- **ConcreteStrategy** — implements a specific algorithm.

**Example — Payment Processing:**
```
interface PaymentStrategy { pay(amount) }
class CreditCardPayment implements PaymentStrategy { pay(amount) { /* charge card */ } }
class PayPalPayment implements PaymentStrategy { pay(amount) { /* debit PayPal */ } }
class CryptoPayment implements PaymentStrategy { pay(amount) { /* transfer crypto */ } }

class ShoppingCart {
    strategy: PaymentStrategy
    setPaymentStrategy(s) { strategy = s }
    checkout(amount) { strategy.pay(amount) }
}
```
At runtime: `cart.setPaymentStrategy(new PayPalPayment())` — the cart uses PayPal without any code changes.

**Benefits:** Open/Closed Principle (add new strategies without modifying existing code); eliminates conditional logic (no `if/else` chains for selecting algorithms); algorithm is swappable at runtime.

**Delegation in action:** The Strategy pattern is a direct application of delegation — the Context delegates algorithm execution to the Strategy object.

### Command Pattern

**Intent:** Encapsulate a request as an **object**, thereby letting you parameterize clients with different requests, queue or log requests, and support **undo/redo** operations.

**Problem it solves:** You want to decouple the object that invokes an operation (sender) from the object that performs it (receiver). You also need to support undo, queuing, or logging of operations.

**Structure:**
- **Command** (interface) — declares `execute()` and optionally `undo()`.
- **ConcreteCommand** — implements `execute()` by invoking operations on the Receiver. Stores the state needed for `undo()`.
- **Receiver** — the object that performs the actual work.
- **Invoker** — holds a Command and calls `execute()` on it. Does not know the Receiver.
- **Client** — creates ConcreteCommand objects and sets their Receivers.

**Example — Smart Home Remote:**
```
interface Command { execute(); undo() }

class LightOnCommand implements Command {
    light: Light     // Receiver
    execute() { light.turnOn() }
    undo() { light.turnOff() }
}

class Remote {       // Invoker
    command: Command
    pressButton() { command.execute() }
    pressUndo() { command.undo() }
}
```
The `Remote` doesn't know about the `Light`. It just calls `execute()` on whatever command it holds. You can easily swap in a `FanOnCommand`, `GarageDoorOpenCommand`, etc.

**Benefits:** Decouples invoker from receiver; supports undo/redo, command queuing, macro commands (composite commands), and logging/auditing.

---

## 5.3 Selecting and Applying Design Patterns

### Heuristics for Pattern Selection

When faced with a design problem, use these guidelines to select the appropriate pattern:

- **"I need to create objects without specifying exact classes"** → Factory Method or Abstract Factory.
- **"I need to create families of related objects"** → Abstract Factory.
- **"I need to use a class with an incompatible interface"** → Adapter.
- **"I need to treat individual objects and groups uniformly"** → Composite.
- **"I have two independent dimensions of variation"** → Bridge.
- **"I need to switch algorithms at runtime"** → Strategy.
- **"I need to encapsulate requests, support undo, or queue operations"** → Command.

### Integrating Patterns into Designs

- **Start with the problem, not the pattern** — don't force patterns where they aren't needed. Over-engineering is as harmful as under-engineering.
- **Apply one pattern at a time** — integrate and test before adding another.
- **Patterns can be combined** — for example, an Abstract Factory can use Factory Methods internally; a Command can use a Strategy to decide how to execute.
- **Document pattern usage** — annotate class diagrams and code comments with the pattern name so future developers understand the design rationale.
- **Refactor toward patterns** — it is often better to start with simple code and refactor toward a pattern when the need becomes clear, rather than applying patterns preemptively.

---

## 5.4 Managing Reuse

### Documenting Reuse Strategies

- Maintain a **reuse repository** — a catalog of reusable components (classes, libraries, patterns, frameworks) with documentation on their purpose, interface, usage examples, and constraints.
- Write **clear API documentation** — any reusable component must have well-documented public interfaces.
- Record **design decisions** — document why a particular pattern or reusable component was chosen over alternatives.
- Maintain **version history** — reusable components evolve; track changes and maintain backward compatibility.

### Assigning Responsibilities for Reusable Components

- Designate a **reuse champion or team** — responsible for identifying, developing, maintaining, and promoting reusable components.
- Establish **quality standards** — reusable components must be well-tested, well-documented, and follow coding standards.
- Define **ownership and maintenance** — every reusable component should have a clear owner responsible for bug fixes and updates.
- Create **guidelines for contribution** — define how new reusable components are proposed, reviewed, approved, and added to the repository.
- Conduct **reuse reviews** — periodically review projects to identify opportunities for creating new reusable components from project-specific code.

---

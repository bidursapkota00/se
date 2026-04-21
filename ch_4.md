# Unit IV: Object-Oriented Analysis and Design with UML

---

## 4.1 OOAD Principles

> **Past Questions:**
> - **[Old1]** Explain the role of abstraction, inheritance, and polymorphism in OO paradigm with examples. _(Q4b)_
> - **[Internal1]** Explain Object Oriented Development and its key features. What are the different types of modeling? _(Q4a)_
> - **[Internal3]** Define encapsulation, abstraction, inheritance, and polymorphism with a scenario. _(Q4a)_

### What is OOAD?

Object-Oriented Analysis and Design (OOAD) is a software engineering approach that models a system as a collection of **interacting objects**, each representing a real-world entity with data (attributes) and behavior (methods).

- **Analysis** — focuses on understanding the problem domain. Answers: *What does the system need to do?* Produces analysis models (use cases, domain models).
- **Design** — focuses on defining a solution architecture. Answers: *How will the system do it?* Produces design models (class diagrams, sequence diagrams, component diagrams).

### The Four Core Principles

**Encapsulation:**

Bundling data (attributes) and the methods that operate on that data into a single unit (class), while **restricting direct access** to internal details.

- The internal state of an object is hidden; only a controlled interface (public methods) is exposed.
- Protects data integrity — external code cannot corrupt an object's state by directly modifying its fields.
- Example: A `BankAccount` class encapsulates the `balance` attribute as private. External code cannot set `balance = -1000` directly — it must use the `withdraw()` method, which enforces business rules (e.g., cannot withdraw more than available balance).

**Abstraction:**

Showing only the **essential features** of an object while hiding irrelevant implementation details. It reduces complexity by letting users interact with a simplified interface.

- Focus on *what* an object does, not *how* it does it internally.
- Example: A `Vehicle` abstract class exposes `start()`, `stop()`, and `accelerate()` methods. A driver uses these without knowing whether the engine is electric, diesel, or hybrid — the internal mechanics are abstracted away.

**Inheritance:**

A mechanism where a new class (subclass/child) **acquires the properties and behaviors** of an existing class (superclass/parent). It establishes an "is-a" relationship.

- Promotes code reuse — common functionality is written once in the parent and inherited by all children.
- Supports hierarchical classification.
- Example: `Animal` (parent) has attributes `name`, `age` and method `eat()`. `Dog` (child) inherits all of these and adds its own method `bark()`. `Cat` (child) inherits from `Animal` and adds `purr()`. Both Dog and Cat *are* Animals.

**Polymorphism:**

The ability of objects of **different classes** to respond to the **same method call** in different ways. One interface, multiple implementations.

- Enables flexibility — new subclasses can be added without modifying existing code that uses the parent interface.
- **Compile-time polymorphism (Overloading):** Same method name, different parameters in the same class.
- **Runtime polymorphism (Overriding):** Subclass provides its own implementation of a method defined in the parent class.
- Example: A `Shape` class defines `draw()`. `Circle` overrides `draw()` to render a circle. `Rectangle` overrides `draw()` to render a rectangle. Code that calls `shape.draw()` works correctly regardless of the actual shape type — the correct version is called at runtime.

### Types of Modeling in OO Development

- **Functional Model** — describes *what* the system does (use case diagrams, data flow).
- **Object/Static Model** — describes the *structure* of the system (class diagrams, object diagrams — classes, attributes, relationships).
- **Dynamic Model** — describes the *behavior* of the system over time (sequence diagrams, state machine diagrams, activity diagrams — interactions, state changes, workflows).

---

## 4.2 Analysis Object Models and Dynamic Models

### Entity, Boundary, and Control Objects

The **Entity-Boundary-Control (EBC)** pattern classifies analysis objects by their role in the system. This separation of concerns makes the design modular and maintainable.

**Entity Objects:**
- Represent the core **business data** of the system — the "things" the system manages.
- They are persistent (stored in databases) and contain business rules related to the data.
- Typically derived from nouns in the problem description.
- Examples: `Book`, `Customer`, `Order`, `Patient`, `Doctor`.

**Boundary Objects:**
- Represent the **interface** between the system and external actors (users or external systems).
- They handle input/output — displaying information to users and capturing user actions.
- Every actor-system interaction passes through a boundary object.
- Examples: `LoginScreen`, `SearchForm`, `PaymentGateway`, `ReportPrinter`, `APIEndpoint`.

**Control Objects:**
- Represent the **use case logic** — they coordinate the flow of events between boundary and entity objects.
- They contain the application logic that doesn't naturally belong to an entity or boundary.
- Typically, there is one control object per use case.
- Examples: `PurchaseController`, `LoginHandler`, `BookingManager`, `PaymentProcessor`.

**How EBC works together (example — "Purchase Book"):**
1. `BookstoreUI` (Boundary) captures the customer's book selection and checkout action.
2. `PurchaseController` (Control) receives the request, validates the order, checks inventory, and coordinates payment.
3. `Book`, `Order`, `Customer` (Entity) objects are created/updated with the transaction data.
4. `PaymentGateway` (Boundary) communicates with an external payment system.
5. `PurchaseController` sends confirmation back through `BookstoreUI`.

### Generalization and Specialization

**Generalization** is the process of extracting common attributes and behaviors from multiple classes into a single, more general **superclass**.
- Example: `Dog`, `Cat`, and `Bird` share `name`, `age`, `eat()` → extract into a general `Animal` class.

**Specialization** is the reverse — creating more specific **subclasses** from a general class by adding unique attributes or behaviors.
- Example: From `Animal`, specialize into `Dog` (adds `breed`, `bark()`), `Cat` (adds `indoor`, `purr()`).

Together, generalization and specialization form **inheritance hierarchies** ("is-a" relationships) that promote code reuse, polymorphism, and cleaner design.

---

## 4.3 UML Diagrams

> **Past Questions:**
> - **[Old1]** Draw a use case diagram for Online Bookstore (customer, bookstore owner, delivery personnel). _(Q3c)_
> - **[Old1]** How can class diagrams and sequence diagrams model a Library Management System? _(Q4a)_
> - **[Old1]** How can use case diagrams and activity diagrams capture requirements and workflows? _(Q4a OR)_
> - **[Old2]** Draw a UML sequence diagram for online appointment booking with exception handling. _(Q2a)_
> - **[Old2]** Draw a Use Case diagram for a library management system. _(Q6a)_
> - **[Internal1]** Illustrate an example of a use case model. _(Q3c)_
> - **[Internal1]** For Hospital Management, develop a class diagram and a sequence diagram. _(Q4b)_
> - **[Internal2]** Make use case diagram for a patient management system. _(Q2a)_
> - **[Internal2]** Make sequence diagram using UML. _(Q2b)_
> - **[Internal3]** Draw a use case diagram for Online Bookstore and explain how it captures stakeholder needs. _(Q3c)_

### Use Case Diagrams

**Purpose:** Model the functional requirements of a system by showing the interactions between actors and the system's use cases. They answer: *What can users do with the system?*

**Components:**
- **Actor** — stick figure representing a user role or external system that interacts with the system.
- **Use Case** — oval representing a specific functionality or goal the system provides.
- **System Boundary** — rectangle enclosing all use cases, representing the scope of the system.
- **Relationships:**
  - **Association** — solid line connecting an actor to a use case (actor participates in the use case).
  - **Include (<<include>>)** — dashed arrow from base use case to included use case. Mandatory shared behavior (always executed). Example: "Place Order" <<include>> "Authenticate User."
  - **Extend (<<extend>>)** — dashed arrow from extending use case to base use case. Optional behavior (executed only under certain conditions). Example: "Apply Coupon" <<extend>> "Place Order."
  - **Generalization** — solid arrow with hollow triangle. Inheritance between actors or use cases.

**Example — Library Management System:**
- **Actors:** Student, Librarian, System Administrator.
- **Use Cases:** Search Book, Borrow Book, Return Book, Pay Fine, Manage Inventory, Issue Book, Track Overdue Books, Manage User Accounts.
- **Relationships:** Student → Search Book, Borrow Book, Return Book, Pay Fine. Librarian → Issue Book, Manage Inventory, Track Overdue Books. "Borrow Book" <<include>> "Check Availability." "Pay Fine" <<extend>> "Return Book" (fine only if overdue).

### Class Diagrams

**Purpose:** Model the static structure of a system — the classes, their attributes, operations, and the relationships between them. Class diagrams are the backbone of OO design.

**Class Notation:**
A rectangle divided into three compartments:
- **Top:** Class name (e.g., `Book`)
- **Middle:** Attributes with visibility and type (e.g., `- title: String`, `- price: float`)
- **Bottom:** Operations with visibility, parameters, and return type (e.g., `+ getTitle(): String`)

**Visibility:**
- `+` Public — accessible from anywhere.
- `-` Private — accessible only within the class.
- `#` Protected — accessible within the class and its subclasses.

**Relationships:**
- **Association** — solid line. A general structural connection between two classes (e.g., `Student` is associated with `Course`).
- **Aggregation** — solid line with **hollow diamond** at the "whole" end. Weak ownership — the part can exist independently. Example: `Department` ◇— `Professor` (a professor can exist without a department).
- **Composition** — solid line with **filled diamond** at the "whole" end. Strong ownership — the part cannot exist without the whole. Example: `House` ◆— `Room` (rooms don't exist without the house).
- **Inheritance (Generalization)** — solid line with **hollow triangle** pointing to parent. Example: `SavingsAccount` —▷ `BankAccount`.
- **Dependency** — dashed arrow. A weak relationship where one class uses another temporarily. Example: `OrderProcessor` - - -> `PaymentGateway`.

**Multiplicity:** Placed at each end of a relationship line.
- `1` — exactly one
- `0..1` — zero or one
- `*` or `0..*` — zero to many
- `1..*` — one to many

**Example — Library Management System (partial):**

```
+------------------+         1..*  +------------------+
|     Book         |◆-------------|     Copy         |
+------------------+               +------------------+
| - isbn: String   |               | - copyId: int    |
| - title: String  |               | - status: String |
| - author: String |               +------------------+
+------------------+               | + checkOut()     |
| + getDetails()   |               | + checkIn()      |
+------------------+               +------------------+

+------------------+        borrows  +------------------+
|    Member        |  0..* -------> |      Loan         |
+------------------+                +------------------+
| - memberId: int  |                | - loanDate: Date  |
| - name: String   |                | - dueDate: Date   |
+------------------+                | - returnDate: Date |
| + register()     |                +------------------+
| + borrowBook()   |                | + calculateFine() |
+------------------+                +------------------+
```

### Sequence Diagrams

**Purpose:** Model the dynamic behavior of a system by showing how objects interact in a specific scenario over time. They show the **order of messages** exchanged.

**Components:**
- **Lifeline** — a vertical dashed line extending downward from an object/actor box. Represents the object's existence over time.
- **Activation Bar** — a thin vertical rectangle on a lifeline indicating when the object is actively processing.
- **Messages:**
  - **Synchronous** — solid arrow with filled arrowhead. Sender waits for a response.
  - **Asynchronous** — solid arrow with open arrowhead. Sender does not wait.
  - **Return** — dashed arrow with open arrowhead. Returns a value to the caller.
  - **Self-message** — an arrow that loops back to the same lifeline.
- **Combined Fragments:**
  - **alt** — alternative paths (if/else).
  - **loop** — repeated behavior.
  - **opt** — optional behavior (executes only if condition is true).

**Example — Borrow Book (Library System):**

```
Student        LibraryUI        LoanController        Book        Loan
  |                |                  |                 |            |
  |--searchBook()->|                  |                 |            |
  |                |--findBook()----->|                 |            |
  |                |                  |--checkAvail()-->|            |
  |                |                  |<--available-----|            |
  |                |                  |--createLoan()---|----------->|
  |                |                  |<--loanCreated---|------------|
  |                |<--confirmation---|                 |            |
  |<--displayMsg---|                  |                 |            |
```

**How sequence diagrams help:** They clarify the order and responsibility of message handling, reveal which objects interact, and identify missing methods or classes during design.

### Activity Diagrams

**Purpose:** Model the workflow or business process — the step-by-step flow of activities, including decisions, parallel flows, and synchronization. Similar to an enhanced flowchart.

**Components:**
- **Initial Node** — filled circle. Starting point of the flow.
- **Activity/Action Node** — rounded rectangle. A single step or task.
- **Decision Node** — diamond. A branching point with guard conditions (e.g., `[payment successful]`, `[payment failed]`).
- **Merge Node** — diamond. Merges multiple incoming flows back into one.
- **Fork** — thick horizontal bar. Splits one flow into multiple **parallel** flows.
- **Join** — thick horizontal bar. Synchronizes parallel flows; all must complete before proceeding.
- **Final Node** — filled circle inside a circle (bull's-eye). End of the flow.
- **Swimlanes** — vertical or horizontal partitions that show which actor or component is responsible for each activity.

**Example — Return Book (Library System):**

```
[Start] → Student presents book → Librarian scans book
        → [Decision: Is it overdue?]
            → [Yes] → Calculate fine → Student pays fine → Update record
            → [No]  → Update record
        → Mark book as available → [End]
```

**When to use:** Use activity diagrams to model complex workflows, business processes, use case flows with decisions and parallel actions, or any process where the step-by-step logic needs to be visualized.

### State Machine Diagrams

**Purpose:** Model the **lifecycle of a single object** — the states it can be in, the events that trigger transitions, and the actions performed during transitions.

**Components:**
- **State** — rounded rectangle. A condition or situation in an object's life (e.g., `Available`, `Borrowed`, `Reserved`, `Lost`).
- **Initial State** — filled circle. The state the object starts in.
- **Final State** — filled circle inside a circle. The terminal state.
- **Transition** — arrow from one state to another. Labeled with: `event [guard] / action`.
  - **Event** — trigger causing the transition (e.g., `borrowBook`).
  - **Guard** — boolean condition that must be true (e.g., `[memberValid]`).
  - **Action** — operation performed during the transition (e.g., `/ updateStatus()`).
- **Composite State** — a state containing sub-states (nested state machine).

**Example — Book Copy Lifecycle (Library System):**

```
[Initial] → Available
Available --borrowBook [memberValid]--> Borrowed
Borrowed  --returnBook--> Available
Borrowed  --reportLost--> Lost
Available --reserve--> Reserved
Reserved  --pickUp--> Borrowed
Reserved  --cancelReservation--> Available
Lost      --bookFound--> Available
Lost      --> [Final] (if permanently lost)
```

**When to use:** Use state machine diagrams when an object has distinct states with clearly different behavior (e.g., an Order: Placed → Confirmed → Shipped → Delivered → Returned; a Bug: New → Assigned → In Progress → Resolved → Closed).

---

## 4.4 Modeling Interactions and Object Lifecycles

### Mapping Use Cases to Objects

Each use case is realized by a collaboration of objects. The mapping process:

1. **Identify participating objects** — for each use case, determine which entity, boundary, and control objects are needed.
2. **Assign responsibilities** — decide which object handles which part of the use case logic.
3. **Create sequence diagrams** — draw the message flow between objects to realize the use case.
4. **Refine the class diagram** — add newly discovered attributes, methods, and relationships.

**Example — "Borrow Book" use case maps to:**
- Boundary: `LibraryUI` (captures request)
- Control: `LoanController` (coordinates logic)
- Entity: `Book`, `Copy`, `Member`, `Loan` (stores data)

### Modeling Associations and Aggregations

**Association:** A structural relationship between two classes indicating they are connected.
- Example: `Doctor` treats `Patient` — a bidirectional association with multiplicity `1..*` to `0..*`.

**Aggregation (has-a, weak):** The whole contains parts, but parts can exist independently.
- Example: `Library` has `Books` — if the library closes, the books still exist as objects.

**Composition (has-a, strong):** The whole owns parts; parts are destroyed when the whole is destroyed.
- Example: `Order` is composed of `OrderItems` — deleting an order deletes its items.

### Modeling Inheritance Relationships

Inheritance captures "is-a" relationships between classes.
- Look for classes that share common attributes/methods → extract a superclass (generalize).
- Look for specialized variants of a class → create subclasses (specialize).
- Example: `User` (parent) with `name`, `email`, `login()` → `Student` (child: adds `studentId`, `enroll()`) and `Librarian` (child: adds `employeeId`, `issueBook()`).

---

## 4.5 Reviewing Analysis and Design Models

### Iterative Refinement

Analysis and design models are never perfect on the first pass. They are refined through repeated cycles:

- **Review consistency** — ensure class diagrams, sequence diagrams, and use case diagrams all agree. A method called in a sequence diagram must exist in the class diagram.
- **Review completeness** — every use case must be realized by at least one sequence diagram. Every class must trace back to at least one requirement.
- **Check for redundancy** — eliminate duplicate classes, unnecessary relationships, and overcomplication.
- **Validate against requirements** — walk through each requirement and verify the models satisfy it.
- **Incorporate feedback** — present models to stakeholders, developers, and testers for review.

### Client Sign-Off Procedures

Before proceeding to implementation, the analysis and design models must be formally approved:

- Present the models to key stakeholders in a review meeting.
- Walk through use cases and demonstrate how the design addresses each requirement.
- Document any open issues, assumptions, or risks.
- Obtain written sign-off indicating the client agrees the design meets their needs.
- Sign-off establishes a **baseline** — any changes after this point go through formal change management.

---

## 4.6 Case Study: Applying OOAD and UML to a Real-World Application

**Scenario — Hospital Management System:**

**Step 1: Identify Actors and Use Cases**
- Actors: Patient, Doctor, Admin Staff, Billing System (external).
- Use Cases: Register Patient, Book Appointment, View Schedule, Update Patient Record, Generate Bill, Cancel Appointment.

**Step 2: Draw Use Case Diagram**
- Patient → Register, Book Appointment, View Medical Reports.
- Doctor → View Schedule, Update Patient Record.
- Admin → Manage Doctor Schedules, Approve/Cancel Appointments.
- "Book Appointment" <<include>> "Check Doctor Availability."
- "Generate Bill" <<extend>> "Book Appointment" (only for paid consultations).

**Step 3: Identify Classes (EBC analysis)**
- Entity: `Patient`, `Doctor`, `Appointment`, `MedicalRecord`, `Bill`.
- Boundary: `PatientPortal`, `DoctorDashboard`, `AdminPanel`.
- Control: `AppointmentController`, `BillingController`.

**Step 4: Draw Class Diagram (partial)**
- `Patient` (patientId, name, dob, contact) → associated with `Appointment` (0..*).
- `Doctor` (doctorId, name, specialty) → associated with `Appointment` (0..*).
- `Appointment` (appointmentId, date, time, status) → composed with `Bill` (0..1).
- `Patient` associated with `MedicalRecord` (1..*).

**Step 5: Draw Sequence Diagram — "Book Appointment"**
1. Patient → PatientPortal: selectDoctor()
2. PatientPortal → AppointmentController: checkAvailability(doctorId, date)
3. AppointmentController → Doctor: getSchedule()
4. Doctor → AppointmentController: return availableSlots
5. AppointmentController → PatientPortal: displaySlots()
6. Patient → PatientPortal: confirmSlot()
7. PatientPortal → AppointmentController: bookAppointment()
8. AppointmentController → Appointment: create(patientId, doctorId, date, time)
9. AppointmentController → PatientPortal: confirmationMessage()

**Step 6: Iterative Refinement**
- Review: Does the class diagram match the sequence diagram? Are all methods in sequence diagram present in the classes?
- Add missing attributes/methods discovered during sequence diagram creation.
- Present to client and obtain sign-off before implementation.

---

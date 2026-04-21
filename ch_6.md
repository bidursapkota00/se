# Unit VI: Software Quality Assurance and Testing

---

## 6.1 Software Quality Concepts and Attributes

> **Past Questions:**
> - **[Internal1]** Explain the significance of quality management in development. How is internal quality and external quality confirmed? _(Q6a)_

### What is Software Quality?

Software quality is the degree to which a software product satisfies stated and implied requirements, meets user expectations, and is free from defects. Quality is not just about "does it work?" — it encompasses reliability, performance, security, usability, and maintainability.

### Quality Attributes (ISO 9126 / ISO 25010)

**Reliability:** The capability of the software to maintain its level of performance under specified conditions over a specified period.
- **Maturity** — frequency of failure due to faults.
- **Fault tolerance** — ability to maintain performance despite software faults.
- **Recoverability** — ability to restore performance and recover data after a failure.
- Example: An online banking system must process transactions correctly 99.99% of the time and recover gracefully from server crashes.

**Usability:** The effort required for users to learn, operate, and interact with the software.
- **Learnability** — how easily new users can accomplish basic tasks.
- **Operability** — how efficiently experienced users can perform tasks.
- **Accessibility** — can users with disabilities use the system?
- Example: A new user should be able to complete a purchase on an e-commerce site within 3 minutes without training.

**Efficiency (Performance):** The relationship between the software's performance level and the resources used.
- **Time behavior** — response time, processing time, throughput.
- **Resource utilization** — CPU, memory, disk, network usage.
- Example: Search results must be returned within 2 seconds under normal load; the system should not consume more than 512 MB of RAM.

**Maintainability:** The effort needed to make modifications — bug fixes, enhancements, or adaptations.
- **Analyzability** — ease of diagnosing defects or identifying parts to modify.
- **Changeability** — ease of implementing modifications.
- **Stability** — risk of unexpected effects from modifications.
- **Testability** — ease of validating modified software.
- Example: Modular code with SOLID principles, clear documentation, and comprehensive test suites makes a system highly maintainable.

**Software Safety:** The software's ability to operate without causing unacceptable risk of harm to people, property, or the environment.
- Critical in medical devices, automotive systems, aviation software, and industrial control systems.
- Achieved through hazard analysis, fail-safe mechanisms, and rigorous testing.

**Software Security:** The software's ability to protect data and functionality from unauthorized access, use, disclosure, modification, or destruction.
- **Confidentiality** — only authorized users can access data.
- **Integrity** — data cannot be tampered with without detection.
- **Availability** — the system remains accessible to authorized users.
- Achieved through authentication, authorization, encryption, input validation, and secure coding practices.

### Internal Quality vs. External Quality

**Internal Quality:** Measured **during development** by examining the software product itself (source code, design documents) **without executing** it.
- Measured through: code reviews, static analysis, code complexity metrics (cyclomatic complexity), coupling/cohesion analysis, adherence to coding standards.
- Examples: low code duplication, high test coverage, clean architecture, consistent naming conventions.

**External Quality:** Measured **during execution** by observing the software's behavior in a test or operational environment.
- Measured through: functional testing, performance testing, usability testing, security testing.
- Examples: response time under load, crash rate, user satisfaction scores, defect density.

**Relationship:** Internal quality influences external quality. Well-structured, clean code (internal) leads to fewer bugs and better performance (external). Poor internal quality eventually manifests as external quality problems.

---

## 6.2 Software Cost Estimation

> **Past Questions:**
> - **[Old2]** What are the different software cost estimation techniques? Explain one in detail. _(Q3a)_
> - **[Internal1]** For the given scenario, estimate the cost using Function Points. _(Q6b)_
> - **[Internal2]** Explain the Function Point (FP) method. _(Q5b)_

### Estimation Techniques Overview

- **Expert Judgment** — experienced professionals estimate based on past experience. Quick but subjective.
- **Analogy-Based Estimation** — compare current project to similar completed projects.
- **Algorithmic Models** — use mathematical formulas based on project parameters (COCOMO, Function Points).
- **Top-Down Estimation** — estimate the overall project cost first, then distribute to sub-tasks.
- **Bottom-Up Estimation** — estimate individual tasks, then aggregate to get total cost.

### COCOMO Model (Constructive Cost Model)

Developed by **Barry Boehm (1981)**. An algorithmic model that estimates effort, duration, and cost based on project size (KLOC — Thousands of Lines of Code).

**Project Modes:**
- **Organic** — small, simple projects with experienced teams and well-understood requirements (e.g., payroll system).
- **Semi-detached** — medium complexity, mix of experienced and less-experienced staff (e.g., database management system).
- **Embedded** — highly complex, tightly constrained projects with stringent requirements (e.g., air traffic control, medical devices).

**Basic COCOMO Formulas:**

**Effort:** E = a × (KLOC)^b (Person-Months)
**Development Time:** D = c × (E)^d (Months)
**Staff Required:** P = E / D (Persons)

| Mode | a | b | c | d |
|---|---|---|---|---|
| Organic | 2.4 | 1.05 | 2.5 | 0.38 |
| Semi-detached | 3.0 | 1.12 | 2.5 | 0.35 |
| Embedded | 3.6 | 1.20 | 2.5 | 0.32 |

**Levels of COCOMO:**
- **Basic** — quick estimate using only KLOC and project mode.
- **Intermediate** — refines Basic by applying 15 cost driver attributes (team capability, reliability, tool usage, etc.) as an Effort Adjustment Factor (EAF). Formula: E = a × (KLOC)^b × EAF.
- **Detailed** — applies cost drivers at individual SDLC phases for maximum precision.

### Function Point Analysis (FPA)

FPA estimates software size based on **user-visible functionality** rather than lines of code. It is language-independent and can be used early in the project.

**Five Function Types:**

- **External Inputs (EI)** — data or control information entering the system (e.g., forms, data entry screens).
- **External Outputs (EO)** — data leaving the system, typically involving processing/calculation (e.g., reports, invoices).
- **External Inquiries (EQ)** — requests that retrieve data without modifying internal files (e.g., search queries, lookups).
- **Internal Logical Files (ILF)** — user-identifiable data groups maintained within the system (e.g., database tables, master files).
- **External Interface Files (EIF)** — data groups referenced by the system but maintained by another system (e.g., shared databases, external APIs).

**Weighing Factors:**

| Component | Low | Average | High |
|---|---|---|---|
| EI | 3 | 4 | 6 |
| EO | 4 | 5 | 7 |
| EQ | 3 | 4 | 6 |
| ILF | 7 | 10 | 15 |
| EIF | 5 | 7 | 10 |

**Calculation Steps:**

**Step 1:** Calculate Unadjusted Function Points (UFP):
UFP = Σ (Count of each type × Weighing factor)

**Step 2:** Calculate Value Adjustment Factor (VAF):
VAF = 0.65 + (0.01 × TDI)
Where TDI = Total Degree of Influence (sum of 14 General System Characteristics, each rated 0–5).

**Step 3:** Calculate Final Function Points:
FP = UFP × VAF

**Step 4:** Calculate Effort and Cost:
Effort = FP / Productivity (FP per person-month)
Cost = Effort × Average Salary

### Worked Example (from Internal1)

**Given:**
- External Inputs: 150, External Outputs: 130, External Inquiries: 120
- Internal Logical Files: 90, External Interface Files: 100
- Average weighing factor used
- Value Adjustment Factor (VAF): 0.65 + (0.01 × 65) = **1.30**
- Productivity: 75 FP/person-month
- Average Salary: NRs. 75,000/person-month

**Step 1 — UFP:**

| Component | Count | Avg Weight | Total |
|---|---|---|---|
| EI | 150 | 4 | 600 |
| EO | 130 | 5 | 650 |
| EQ | 120 | 4 | 480 |
| ILF | 90 | 10 | 900 |
| EIF | 100 | 7 | 700 |
| **UFP** | | | **3330** |

**Step 2 — FP:**
FP = 3330 × 1.30 = **4329**

**Step 3 — Effort:**
Effort = 4329 / 75 = **57.72 person-months**

**Step 4 — Cost:**
Cost = 57.72 × 75,000 = **NRs. 43,29,000**

---

## 6.3 Software Quality Assurance Planning and Process

> **Past Questions:**
> - **[Old1]** Explain the objectives of SQA and discuss key activities (reviews, audits, testing, process monitoring). How do they reduce defects? _(Q6b OR)_
> - **[Internal3]** Write short notes on: Software Quality Assurance (SQA) Activities. _(Q7c)_

### What is Software Quality Assurance (SQA)?

SQA is a **systematic, planned set of activities** that ensures the software development process and products conform to defined requirements, standards, and procedures. SQA is **process-oriented** — it focuses on preventing defects rather than just detecting them.

### Objectives of SQA

- Ensure the software product meets functional and non-functional requirements.
- Ensure the development process follows established standards and procedures.
- Identify and eliminate defects as early as possible in the lifecycle.
- Provide management with visibility into the quality of the software process and product.
- Ensure continuous improvement of the development process.

### Key SQA Activities

**Reviews:**
- **Requirements Reviews** — verify requirements are complete, consistent, and testable before design begins.
- **Design Reviews** — verify design accurately maps to requirements and follows architectural standards.
- **Code Reviews (Peer Reviews)** — developers examine each other's code for defects, standards compliance, and best practices. Catches defects early at the lowest cost.
- **Walkthrough** — author presents work to peers for informal feedback.
- **Inspection** — formal, structured examination of a work product by trained inspectors using checklists. Most rigorous form of review.

**Audits:**
- Formal, independent examination of whether development processes and work products comply with defined plans, standards, and procedures.
- Conducted by an audit team independent of the project.
- Examples: process audits (is the team following the defined process?), product audits (does the documentation match the actual code?).

**Testing:**
- Systematic execution of software to identify defects.
- Includes unit testing, integration testing, system testing, acceptance testing, regression testing.
- SQA ensures testing is planned, systematic, and adequately covers requirements.

**Process Monitoring:**
- Tracking and measuring the development process using metrics (defect density, test coverage, review efficiency, schedule variance).
- Using metrics to identify process weaknesses and drive improvements.

**Standards and Procedures:**
- Defining and enforcing coding standards, documentation standards, and process guidelines.
- Ensuring compliance with industry standards (ISO 9001, CMMI, IEEE standards).

### Role of QA in the Software Lifecycle

- **Requirements phase** — review requirements for quality properties (completeness, testability, consistency).
- **Design phase** — review design for correctness and adherence to architecture standards.
- **Implementation phase** — enforce coding standards, conduct code reviews, run static analysis.
- **Testing phase** — plan and oversee testing activities, track defects, report quality metrics.
- **Deployment phase** — verify deployment procedures, conduct acceptance testing.
- **Maintenance phase** — ensure changes go through proper review and regression testing.

### How SQA Reduces Defects and Improves Quality

- **Prevention over detection** — process standards and reviews prevent defects from entering the code.
- **Early detection** — reviews and inspections catch defects during requirements/design (10–100x cheaper to fix than post-release).
- **Process improvement** — metrics and audits identify systemic issues and drive continuous improvement.
- **Customer satisfaction** — consistent quality assurance leads to more reliable software that meets user expectations.

---

## 6.4 Testing Concepts

> **Past Questions:**
> - **[Old2]** Define test cases, test stubs, and test drivers. How do they contribute to testing? Provide examples. _(Q5b)_
> - **[Internal2]** What are stubs and drivers in testing? How are they utilized during integration testing? Illustrate with example and diagram. _(Q3)_

### Faults, Erroneous States, and Failures

These three concepts form a causal chain that explains how defects manifest:

**Error (Mistake):** A human action that produces an incorrect result — a misunderstanding, typo, or wrong assumption by the developer.
- Example: Developer misreads requirement and uses `>` instead of `>=` in a comparison.

**Fault (Defect/Bug):** The result of an error — a flaw in the code, design, or documentation.
- Example: The code contains `if (age > 18)` instead of `if (age >= 18)`.

**Erroneous State:** An incorrect internal state of the system caused by executing a fault.
- Example: When a user aged exactly 18 submits the form, the system incorrectly sets `eligible = false`.

**Failure:** An externally observable deviation from expected behavior.
- Example: The user sees "You are not eligible" even though they are 18 and should be eligible.

**Chain:** Error → Fault → Erroneous State → Failure

**Important:** Not every fault leads to a failure (the faulty code may never be executed), and not every erroneous state causes a failure (subsequent code may mask the error).

### Test Cases

A **test case** is a set of conditions, inputs, and expected results used to verify whether a specific requirement or functionality works correctly.

**Components of a test case:**
- **Test Case ID** — unique identifier (e.g., TC-001).
- **Description** — what is being tested.
- **Preconditions** — state of the system before the test.
- **Test Input** — the data or actions provided.
- **Expected Result** — what the system should do.
- **Actual Result** — what the system actually did (filled after execution).
- **Status** — Pass/Fail.

**Example:**

| TC ID | Description | Input | Expected Result |
|---|---|---|---|
| TC-001 | Login with valid credentials | user: "admin", pass: "pass123" | Dashboard displayed |
| TC-002 | Login with invalid password | user: "admin", pass: "wrong" | Error: "Invalid credentials" |
| TC-003 | Login with empty fields | user: "", pass: "" | Error: "Fields required" |

### Test Stubs and Test Drivers

Stubs and drivers are **temporary, dummy modules** used during integration testing when the complete system is not yet available.

**Test Stub (used in Top-Down Integration):**
- Replaces a **lower-level module** that has not been developed yet.
- The module under test **calls** the stub.
- The stub returns hardcoded or simplified responses.
- Example: Testing `OrderController` (developed) which calls `PaymentService` (not developed yet). A stub simulates `PaymentService` and always returns "Payment Successful."

**Test Driver (used in Bottom-Up Integration):**
- Replaces a **higher-level module** that has not been developed yet.
- The driver **calls** the module under test.
- The driver provides test inputs and captures outputs.
- Example: Testing `EmailSender` (developed) before `UserManagement` (not developed). A driver acts as `UserManagement`, calling `EmailSender.send("test@email.com", "Hello")` and verifying the output.

**Visual Representation:**

```
Top-Down Testing:              Bottom-Up Testing:
┌──────────────┐               ┌──────────────┐
│  Module A    │               │  DRIVER      │ ← replaces Module A
│  (developed) │               │  (temporary) │
└──────┬───────┘               └──────┬───────┘
       │ calls                        │ calls
┌──────▼───────┐               ┌──────▼───────┐
│   STUB       │ ← replaces   │  Module B    │
│  (temporary) │   Module B    │  (developed) │
└──────────────┘               └──────────────┘
```

---

## 6.5 Testing Activities

> **Past Questions:**
> - **[Old1]** What is unit testing, integration testing, and system testing? Describe purpose and stage. How do they ensure quality? _(Q6a)_
> - **[Internal3]** Define unit, integration, and system testing. At which SDLC stage should each be performed? How do they work together? _(Q6a)_

### Unit Testing

**What:** Testing **individual components** (functions, methods, classes) in isolation.
**When:** During the **development/coding phase** — performed by developers as they write code.
**Purpose:** Verify that each unit of code works correctly on its own before integrating with other units.

**Characteristics:**
- Tests the smallest testable parts of the software.
- Uses test frameworks (JUnit, pytest, NUnit).
- Fast to execute; should be automated and run frequently.
- Isolates the unit from dependencies using mocks or stubs.

**Example:** Testing a `calculateDiscount(price, percentage)` function with various inputs to verify it returns the correct discounted price.

### Integration Testing

**What:** Testing the **interaction between integrated modules** to verify they work together correctly.
**When:** After unit testing — during the **integration phase** when modules are combined.
**Purpose:** Detect interface defects, data flow errors, and incorrect interactions between modules that individually pass unit tests.

**Integration Strategies:**
- **Big Bang** — all modules integrated simultaneously and tested together. Simple but difficult to isolate faults.
- **Top-Down** — integration starts from the top-level module downward. Lower modules replaced by **stubs**. Tests high-level logic early.
- **Bottom-Up** — integration starts from the lowest-level modules upward. Higher modules replaced by **drivers**. Tests foundational components first.
- **Sandwich (Hybrid)** — combines top-down and bottom-up approaches simultaneously.

**Example:** After unit testing `LoginModule` and `DatabaseModule` separately, integration testing verifies that `LoginModule` correctly queries `DatabaseModule` for user credentials and handles the response properly.

### System Testing

**What:** Testing the **complete, integrated system** as a whole against the specified requirements.
**When:** After integration testing — during the **QA/testing phase** before release.
**Purpose:** Validate that the entire system meets all functional and non-functional requirements.

**Types of system testing:**
- **Functional Testing** — does the system do what requirements specify?
- **Performance Testing** — does it meet response time and throughput requirements?
- **Security Testing** — can it resist unauthorized access and attacks?
- **Usability Testing** — is it easy for users to learn and use?
- **Load/Stress Testing** — how does it behave under heavy load or extreme conditions?
- **Compatibility Testing** — does it work across different browsers, devices, and OS versions?

**Example:** Testing the entire e-commerce application end-to-end — from browsing products, adding to cart, checkout, payment processing, to receiving a confirmation email.

### Regression Testing

**What:** Re-testing **previously tested functionality** after code changes to ensure nothing is broken.
**When:** **Ongoing** — performed every time code is modified (bug fixes, new features, refactoring).
**Purpose:** Ensure that new changes don't introduce unintended side effects in existing functionality.

**Characteristics:**
- Highly suited for automation — the same test suite is run repeatedly.
- Critical in CI/CD pipelines — regression tests run automatically on every commit.
- The regression test suite grows over time as new test cases are added.

**Example:** After fixing a bug in the payment module, regression tests run the entire checkout flow plus login, search, and cart functionality to ensure those features still work correctly.

### How Testing Levels Work Together

Testing follows a **progressive, layered approach** — each level builds confidence:
1. **Unit testing** ensures individual components are correct.
2. **Integration testing** ensures components interact correctly.
3. **System testing** ensures the complete product meets requirements.
4. **Regression testing** ensures modifications don't break existing functionality.

Together, they form a comprehensive safety net: unit tests catch coding errors, integration tests catch interface errors, system tests catch requirement gaps, and regression tests prevent regressions. No single level is sufficient alone — all four are necessary for quality and reliability.

---

## 6.6 Automated Testing Frameworks

### Introduction to Selenium and JUnit

**JUnit** — a widely-used unit testing framework for **Java** applications.
- Provides annotations (`@Test`, `@Before`, `@After`) to define test methods and setup/teardown.
- Supports assertions (`assertEquals()`, `assertTrue()`, `assertThrows()`) to verify expected behavior.
- Integrates with build tools (Maven, Gradle) and CI/CD pipelines (Jenkins).
- Generates test reports showing passed, failed, and skipped tests.

**Selenium** — an open-source framework for automating **web browser** interactions.
- Supports multiple browsers (Chrome, Firefox, Safari, Edge) and multiple programming languages (Java, Python, JavaScript).
- Used for functional testing and regression testing of web applications.
- **Selenium WebDriver** — interacts directly with the browser to simulate user actions (clicking, typing, navigating).
- **Selenium Grid** — runs tests in parallel across multiple browsers and machines.

### Integrating Testing Tools with CI/CD Pipelines

Automated testing is essential for CI/CD — tests must run automatically on every code change.

**Typical integration:**
1. Developer pushes code to Git.
2. CI server (Jenkins) detects the change and triggers the pipeline.
3. **Build step** — compile the application.
4. **Unit test step** — run JUnit tests. If any fail, the pipeline stops and the team is notified.
5. **Integration test step** — run integration tests against a test database/environment.
6. **UI test step** — run Selenium tests against a deployed staging environment to verify end-to-end user workflows.
7. **Report step** — generate and publish test reports and code coverage metrics.
8. If all tests pass, proceed to deployment.

**Benefits of automation in CI/CD:**
- Tests run consistently and repeatedly — no human errors in test execution.
- Immediate feedback — developers know within minutes if their change broke something.
- Faster releases — confidence in automated test suites enables frequent, safe deployments.
- Scalability — Selenium Grid and parallel execution allow large test suites to run quickly.

---

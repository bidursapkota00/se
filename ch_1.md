# Unit I: Introduction

---

## 1.1 Software Engineering Concepts

> **Past Questions:**
> - **[Old1]** What is Software Engineering? Can it be considered a true engineering discipline? Justify. _(Q1b)_

### Definition of Software Engineering

**IEEE Definition:** *"The application of a systematic, disciplined, quantifiable approach to the development, operation, and maintenance of software; that is, the application of engineering to software."*

Software Engineering is not just programming — it encompasses the entire lifecycle of software from conception through retirement, applying engineering principles to produce reliable, efficient, and maintainable software within time and budget constraints.

### Is Software Engineering a True Engineering Discipline?

**Yes, it can be considered a true engineering discipline because:**

- It applies **systematic methods** — structured processes like SDLC, formal design techniques, and standardized testing.
- It uses **quantifiable metrics** — LOC, function points, defect density, code coverage, and cyclomatic complexity for measurement-driven decisions.
- It follows **established standards** — IEEE, ISO/IEC standards, SWEBOK (Software Engineering Body of Knowledge).
- It demands **professional accountability** — critical systems (medical, aviation, finance) require the same rigor as civil or mechanical engineering.

**However, it differs from traditional engineering because:**

- Its subject matter is **virtual, not physical** — not bound by laws of physics.
- Software is inherently **malleable** — changes are easier but also more frequent and harder to control.
- The field is **younger** and lacks the same level of universal licensing/certification as civil or electrical engineering.

**Conclusion:** While differences exist, the discipline's reliance on formal processes, scientific measurement, and professional standards firmly places it within the engineering domain.

### Participants and Roles in Software Projects

**Participants** are the people involved in a software project. **Roles** define their responsibilities.

- **Client/Customer** — commissions the project, defines high-level needs, funds development.
- **End User** — the actual person who uses the delivered software.
- **Project Manager** — plans, schedules, tracks progress, manages risks and resources.
- **Systems Analyst** — bridges client requirements and technical design; elicits and documents requirements.
- **Software Architect** — defines the overall system structure, technology stack, and design decisions.
- **Developer/Programmer** — writes, tests, and debugs code according to design specifications.
- **QA Engineer/Tester** — designs test cases, executes tests, validates quality standards.
- **DevOps Engineer** — manages CI/CD pipelines, deployment, infrastructure, and monitoring.
- **Scrum Master** (Agile) — facilitates the Scrum process, removes impediments for the team.
- **Product Owner** (Agile) — represents stakeholders, prioritizes the product backlog.

### Systems and Models

**System:** A collection of interrelated components (software, hardware, data, people, processes) working together to achieve a common goal. A software system includes the programs, documentation, and operational procedures that function as a cohesive whole.

**Model:** An abstract representation of a system used to understand, visualize, and manage complexity. Models simplify reality to focus on relevant aspects.

- **Process Models** — define *how* software is developed (e.g., Waterfall, Agile, Spiral).
- **System/Analysis Models** — represent *what* the software does or *how* it is structured (e.g., use case diagrams, class diagrams, data flow diagrams).

### Work Products

Work products (also called **artifacts**) are the tangible outputs produced during each phase of software development:

- **Requirements Phase** — SRS (Software Requirements Specification), BRD (Business Requirements Document), use case documents.
- **Design Phase** — architecture documents, UML diagrams, database schemas, interface designs.
- **Implementation Phase** — source code, build scripts, configuration files.
- **Testing Phase** — test plans, test cases, test reports, defect logs.
- **Deployment Phase** — deployment guides, release notes, user manuals.
- **Maintenance Phase** — change requests, patch documentation, updated SRS.

### Activities, Tasks, and Resources

**Activity:** A high-level phase or major step in the development process (e.g., Requirements Engineering, Design, Implementation, Testing, Deployment, Maintenance).

**Task:** A smaller, well-defined unit of work within an activity. For example, within "Testing," tasks include *write test cases*, *execute regression tests*, *log defects*.

**Resources:** Assets required to complete tasks:
- **Human** — developers, testers, managers (measured in person-months).
- **Time** — schedules, deadlines, milestones.
- **Infrastructure** — servers, cloud environments, development machines.
- **Tools** — IDEs, version control (Git), CI/CD tools (Jenkins), project management (Jira).

### Notations, Methods, and Methodologies

**Notation:** A standardized visual or textual language for representing systems.
- **UML (Unified Modeling Language)** — the most widely used notation for modeling software structure and behavior (use case, class, sequence, activity, state diagrams).
- **BPMN** — Business Process Model and Notation for modeling business workflows.
- **ERD** — Entity-Relationship Diagrams for database modeling.

**Method:** A specific technical procedure for performing a particular task.
- Object-Oriented Analysis and Design (OOAD)
- Test-Driven Development (TDD)
- Structured Analysis (SA/SD)
- Formal methods (Z notation, VDM)

**Methodology:** A comprehensive collection of methods, practices, tools, and guidelines that provide a complete framework for software development.
- **Scrum** — iterative Agile methodology with sprints, roles, and ceremonies.
- **Kanban** — flow-based methodology using visual boards and WIP limits.
- **Extreme Programming (XP)** — Agile methodology emphasizing pair programming, TDD, and continuous integration.
- **RUP (Rational Unified Process)** — iterative methodology with use-case-driven development.

**Relationship:** A methodology uses multiple methods, and methods rely on notations to express their outputs.

> Methodology → Methods → Notations
> Example: Scrum (methodology) → user story mapping (method) → UML use case diagrams (notation)

---

## 1.2 Overview of Software Process Models

> **Past Questions:**
> - **[Old1]** How do Waterfall, Iterative, Agile, and DevOps/CI-CD models differ in handling changing requirements, risk, resource use, and scalability? _(Q1a)_
> - **[Old2]** Analyze key factors for selecting Waterfall vs. Agile. Justify your recommendation. _(Q1b)_
> - **[Internal1]** Define SDLC. Describe the Spiral model. How is it different from Waterfall? _(Q1b)_
> - **[Internal2]** How would frequent requirement changes affect development if a traditional model was used? _(Q1d)_
> - **[Internal3]** Reflect on the Vasa Tragedy. Which model would you recommend for changing requirements and poor communication? _(Q1a)_

### Software Development Life Cycle (SDLC)

SDLC is a structured framework that defines the phases involved in developing software from initial concept to final deployment and maintenance. The common phases are:

1. **Requirements Gathering** — understand what to build.
2. **System Design** — plan how to build it.
3. **Implementation** — write the code.
4. **Testing** — verify it works correctly.
5. **Deployment** — release to users.
6. **Maintenance** — fix bugs, add features, adapt to changes.

Different process models organize these phases differently.

### Waterfall Model

A **linear, sequential** model where each phase must be fully completed before the next begins. There is no going back.

**Phases:** Requirements → Design → Implementation → Testing → Deployment → Maintenance

**Advantages:**
- Simple, easy to understand and manage.
- Well-structured with clear milestones and deliverables.
- Extensive documentation at each phase.
- Easy to estimate cost and timeline upfront.

**Disadvantages:**
- **Rigid** — no accommodation for changing requirements once a phase is done.
- **Late testing** — defects discovered only at the end, making them expensive to fix.
- **No working software** until late in the lifecycle.
- High risk for projects with unclear or evolving requirements.

**Best suited for:** Projects with stable, well-defined requirements (e.g., government systems, compliance-driven applications).

### Iterative Model

Develops the software in **repeated cycles (iterations)**. Each iteration goes through requirements, design, coding, and testing to produce an improved version.

**Advantages:**
- Early detection of problems through repeated cycles.
- Feedback incorporated after each iteration.
- More flexible than Waterfall; partial changes manageable between iterations.
- Working software available early.

**Disadvantages:**
- Requires strong project management to keep iterations focused.
- Can become costly if iterations are not well-controlled.
- Overall architecture must be robust enough to accommodate iterative changes.

**Best suited for:** Projects where full requirements are not clear initially but the general scope is understood.

### Spiral Model

Proposed by **Barry Boehm (1986)**. A **risk-driven** model that combines iterative development with systematic risk analysis. Represented as a spiral with four quadrants, expanding outward with each loop.

**Four Phases (per loop):**

1. **Planning** — define objectives, requirements, constraints, and alternative approaches for the current iteration.
2. **Risk Analysis** — identify potential risks (technical, business, schedule) and develop mitigation strategies. Often involves building prototypes.
3. **Engineering** — develop, design, code, and test the software based on validated plans.
4. **Evaluation** — stakeholders review the output, assess progress and quality, and decide whether to proceed to the next loop.

**The radial dimension represents cumulative cost; the angular dimension represents progress through phases.**

**Advantages:**
- Excellent risk management — risks identified and mitigated early.
- Highly flexible; accommodates major changes after each loop.
- Suitable for large, complex, mission-critical projects.
- Incorporates prototyping for early validation.

**Disadvantages:**
- Complex to manage; requires expertise in risk assessment.
- Expensive — overhead of extensive planning and risk analysis in each loop.
- Not suitable for small or low-budget projects.
- Difficult to define milestones and completion criteria.

**Best suited for:** Large-scale, high-risk, complex projects (e.g., defense systems, aerospace software).

**Spiral vs. Waterfall:**

- Waterfall is linear and rigid; Spiral is iterative and flexible.
- Waterfall has no explicit risk analysis phase; Spiral centers on risk management.
- Waterfall produces working software only at the end; Spiral delivers incremental versions.
- Waterfall suits stable requirements; Spiral suits evolving, uncertain requirements.
- Waterfall is simpler and cheaper for small projects; Spiral is better for large, complex ones.

### Agile Models

A family of **adaptive, iterative** methodologies that prioritize working software, customer collaboration, and responsiveness to change over rigid plans and documentation.

**Core Agile Values (Agile Manifesto, 2001):**
- **Individuals and interactions** over processes and tools.
- **Working software** over comprehensive documentation.
- **Customer collaboration** over contract negotiation.
- **Responding to change** over following a plan.

**Key Agile Principles:**
- Deliver working software frequently (weeks rather than months).
- Welcome changing requirements, even late in development.
- Business people and developers work together daily.
- Build projects around motivated individuals.
- Face-to-face conversation is the most effective communication.
- Continuous attention to technical excellence.

**Advantages:**
- Highly flexible — changes welcomed at any stage.
- High customer satisfaction through continuous involvement and frequent delivery.
- Early and continuous delivery of working software.
- Encourages team collaboration, transparency, and self-organization.

**Disadvantages:**
- Difficult to predict long-term costs and timelines.
- Less documentation — can challenge long-term maintenance.
- Requires active, continuous stakeholder participation.
- Risk of scope creep if backlog is not properly managed.
- Not ideal for projects with fixed regulatory or compliance constraints.

**Best suited for:** Fast-paced environments, startups, products with evolving requirements, projects needing frequent user feedback.

### Comparison of Process Models

| Factor | Waterfall | Iterative | Spiral | Agile |
|---|---|---|---|---|
| **Approach** | Linear, sequential | Repetitive cycles | Risk-driven loops | Adaptive, incremental |
| **Flexibility** | Low | Moderate | High | Very High |
| **Risk Management** | Poor (late detection) | Moderate | Excellent | Good |
| **Changing Requirements** | Not supported | Partially supported | Well supported | Fully embraced |
| **Client Involvement** | Minimal (start/end) | Periodic | Active each loop | Continuous |
| **Working Software** | End only | After each iteration | After each spiral | After each sprint |
| **Documentation** | Extensive | Moderate | Extensive | Minimal |
| **Best For** | Stable, clear scope | Partially known scope | High-risk, complex | Dynamic, evolving scope |

### How to Choose the Right Model

- **Requirements are clear and stable** → Waterfall.
- **Requirements will evolve, moderate complexity** → Iterative.
- **High-risk, large-scale, uncertain** → Spiral.
- **Rapidly changing requirements, need for speed and feedback** → Agile.
- **Consider also:** team size, client availability, regulatory constraints, budget, timeline, and organizational culture.

### The Vasa Tragedy — A Lesson in Software Engineering

The Vasa was a Swedish warship that sank on its maiden voyage in 1628 due to changing requirements (the king ordered more cannons and a higher deck mid-construction), poor communication between builders and decision-makers, and lack of proper testing.

**SE Lessons:**
- **Changing requirements without proper process control** leads to disasters — supports the use of Agile or Spiral over Waterfall for volatile requirements.
- **Poor stakeholder communication** is a primary cause of project failure.
- **Lack of prototyping/testing** before final delivery is dangerous.
- Modern practices (iterative reviews, risk analysis, continuous testing, clear communication channels) could have prevented the failure.

---

## 1.3 Introduction to Requirements Engineering

> **Past Questions:**
> - **[Internal1]** How do you perform Requirement Elicitation? Explain with an example. Differentiate Functional and Non-Functional Requirements. _(Q1a)_

### What is Requirements Engineering?

Requirements Engineering (RE) is the process of **defining, documenting, and maintaining** the requirements for a software system. It is the foundation of any successful software project — unclear or incomplete requirements are the leading cause of project failure.

RE involves:
- **Elicitation** — gathering requirements from stakeholders through interviews, surveys, workshops, observation, and prototyping.
- **Analysis** — checking requirements for completeness, consistency, feasibility, and clarity.
- **Specification** — documenting requirements formally (e.g., SRS document).
- **Validation** — confirming requirements accurately reflect stakeholder needs.
- **Management** — handling changes to requirements over time (traceability, versioning).

### Functional Requirements

Functional requirements specify **what the system must do** — the specific behaviors, features, and functions it must provide.

**Characteristics:**
- Describe system functionality and user interactions.
- Can be tested for presence or absence (pass/fail).
- Directly derived from user needs and business processes.

**Examples (for an Online Bookstore):**
- The system shall allow users to search for books by title, author, or ISBN.
- The system shall allow customers to add books to a shopping cart.
- The system shall process credit card payments through a payment gateway.
- The system shall send an order confirmation email after purchase.
- The system shall allow bookstore owners to add, update, or remove books from the catalog.

### Non-Functional Requirements (NFRs)

Non-functional requirements specify **how well the system performs** — the quality attributes and constraints under which it operates.

**Common Types:**
- **Performance** — response time, throughput (e.g., "The search results page must load within 2 seconds").
- **Reliability** — uptime, fault tolerance (e.g., "The system must have 99.9% availability").
- **Scalability** — ability to handle growing users/data (e.g., "Must support 10,000 concurrent users").
- **Security** — data protection, access control (e.g., "All passwords must be hashed using bcrypt").
- **Usability** — ease of use, accessibility (e.g., "Must comply with WCAG 2.1 standards").
- **Maintainability** — ease of modification (e.g., "Modules must follow SOLID principles").
- **Portability** — ability to run on different platforms (e.g., "Must work on Chrome, Firefox, and Safari").
- **Compliance** — adherence to legal/industry standards (e.g., "Must comply with GDPR").

### Functional vs. Non-Functional Requirements

| Aspect | Functional Requirements | Non-Functional Requirements |
|---|---|---|
| **Focus** | What the system does | How well it performs |
| **Nature** | Features, behaviors | Quality attributes, constraints |
| **Testing** | Tested by input/output verification | Tested by benchmarks, metrics, load tests |
| **Source** | Business processes, user needs | System architecture, environment, standards |
| **Example** | "User can reset password via email" | "Password reset page loads in < 1 second" |

### Importance of Requirements Engineering

- **Prevents project failure** — most software failures trace back to poor requirements (ambiguous, incomplete, or conflicting).
- **Reduces cost** — fixing a requirements error after deployment costs **100x more** than fixing it during requirements phase (Boehm's cost curve).
- **Aligns stakeholders** — ensures developers, clients, and users share a common understanding of what is being built.
- **Provides a baseline** — documented requirements serve as the contract between client and development team, and as the foundation for test case design.
- **Enables traceability** — each requirement can be traced forward to design, code, and test cases, ensuring nothing is missed.
- **Supports change management** — well-documented requirements make it easier to assess the impact of changes.

### Requirement Elicitation — Example

**Scenario:** Developing an Online Library Management System.

**Elicitation Steps:**
1. **Identify Stakeholders** — librarians, students, faculty, administration.
2. **Conduct Interviews** — ask librarians about daily tasks (issuing books, tracking overdue items); ask students about search and borrowing needs.
3. **Observe Existing Process** — watch how the current manual or legacy system works.
4. **Develop Use Cases** — e.g., "Student searches for a book → views availability → reserves the book → picks up from library."
5. **Create Prototypes** — build a simple UI mockup of the search and reservation screens for feedback.
6. **Document Requirements** — formalize into an SRS with functional requirements (search, borrow, return, fine calculation) and non-functional requirements (support 500 concurrent users, 99.5% uptime).

---

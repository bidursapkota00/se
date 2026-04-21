# Unit III: Requirements Engineering and Elicitation

---

## 3.1 Requirements Elicitation Concepts

> **Past Questions:**
> - **[Old1]** How does effective stakeholder communication influence the success of requirements gathering? Discuss risks of inadequate participation and strategies to improve collaboration. _(Q5b)_

### What is Requirements Elicitation?

Requirements elicitation is the process of **discovering, gathering, and understanding** the needs, goals, and constraints of stakeholders for a software system. It bridges the gap between what users need and what the development team builds.

Elicitation is not simply asking "what do you want?" — it involves probing, observing, analyzing, and iterating to uncover both explicit and hidden requirements.

### Importance of Stakeholder Involvement

Stakeholders are the people who have an interest in or are affected by the system. Their involvement is critical because **they own the problem domain** — the development team owns the solution domain.

**Why stakeholder involvement matters:**
- **Alignment** — ensures the system addresses actual user needs, not developer assumptions.
- **Completeness** — different stakeholders reveal different aspects of requirements (functional, non-functional, business rules, constraints).
- **Conflict detection** — early involvement surfaces conflicting priorities between stakeholder groups before they become costly design problems.
- **Buy-in and acceptance** — stakeholders who participate in defining requirements are more likely to accept the final product.
- **Reduced rework** — requirements errors caught early cost 10–100x less to fix than those caught after deployment.

**Risks of inadequate stakeholder participation:**
- **Missing requirements** — features the system should have are never identified.
- **Incorrect assumptions** — developers build what they think is needed, not what is actually needed.
- **Scope creep** — late-discovered requirements force uncontrolled changes.
- **User rejection** — the delivered system does not match user expectations, leading to poor adoption.
- **Project failure** — studies consistently show that poor requirements are the #1 cause of software project failure.

**Strategies to improve stakeholder collaboration:**
- Identify all stakeholder groups early (not just the client — include end users, administrators, support staff, regulators).
- Use multiple elicitation techniques (interviews for depth, workshops for consensus, observation for tacit knowledge).
- Establish a single point of contact (Product Owner) to prioritize and resolve conflicts.
- Conduct regular review sessions where stakeholders validate documented requirements.
- Use prototypes and mockups to make abstract requirements concrete and easier to discuss.
- Maintain open, ongoing communication channels rather than one-time requirement-gathering sessions.

### Elicitation Techniques

- **Interviews** — one-on-one or group sessions with stakeholders to gather in-depth information. Best for exploring complex, domain-specific knowledge.
- **Workshops/JAD Sessions** — structured collaborative meetings where multiple stakeholders work together to define, discuss, and prioritize requirements.
- **Brainstorming** — free-form group sessions to generate creative ideas without judgment.
- **Observation (Ethnography)** — watching users perform their tasks in their actual work environment to uncover implicit requirements they may not articulate.
- **Prototyping** — building preliminary mockups or working models so stakeholders can interact with a tangible system and provide concrete feedback.
- **Questionnaires/Surveys** — useful for collecting information from a large, geographically distributed group of stakeholders.
- **Document Analysis** — reviewing existing documents (business processes, regulations, legacy system documentation, manuals) to understand the current state.

### Challenges in Requirements Gathering

- **Communication gaps** — stakeholders speak in business terms; developers think in technical terms. Misinterpretation is common.
- **Ambiguity** — requirements stated in natural language are often vague ("the system should be fast" — how fast?).
- **Incompleteness** — stakeholders forget requirements or assume certain things are obvious.
- **Changing requirements** — business needs evolve during the project lifecycle.
- **Conflicting requirements** — different stakeholder groups may have opposing needs (e.g., security vs. usability).
- **Tacit knowledge** — users often cannot articulate what they need because their workflow has become intuitive.
- **Stakeholder availability** — key stakeholders may be too busy for adequate involvement.

---

## 3.2 Detailed Requirements Analysis

> **Past Questions:**
> - **[Internal2]** What key factors do you consider when gathering requirements to ensure completeness and accuracy? _(Q1e)_

### Purpose of Requirements Analysis

After requirements are elicited, they must be **analyzed** for quality before being documented as specifications. Requirements analysis checks whether the gathered requirements are good enough to serve as a reliable foundation for design and development.

### Quality Properties of Good Requirements

**Completeness:**
- All necessary functionality is captured — nothing required is left out.
- Requirements cover normal operations, edge cases, error handling, and boundary conditions.
- Check: "Can this specification be used to build the entire system without guessing?"

**Consistency:**
- No two requirements contradict each other.
- Terminology is used uniformly throughout the document.
- Check: "Does Requirement A conflict with Requirement B?"

**Clarity (Unambiguity):**
- Each requirement has exactly one interpretation.
- Avoid vague terms like "fast," "user-friendly," "efficient" — use measurable criteria instead.
- Check: "Could two developers read this and build different things?"

**Correctness:**
- Each requirement accurately represents a real need of the stakeholder.
- Requirements are validated against the actual business process and user expectations.
- Check: "Does this requirement reflect what the stakeholder actually asked for?"

**Realism (Feasibility):**
- Each requirement can be implemented within the given budget, timeline, and technology constraints.
- Unrealistic requirements (e.g., "100% uptime with zero cost") must be identified and negotiated.
- Check: "Can this actually be built with available resources and technology?"

**Verifiability (Testability):**
- Each requirement can be tested or measured to confirm it has been satisfied.
- A requirement that cannot be tested is useless — there is no way to prove it was implemented correctly.
- Bad: "The system should be easy to use." Good: "A new user should be able to complete a purchase in under 3 minutes without assistance."
- Check: "How would I write a test case for this?"

**Traceability:**
- Each requirement can be traced back to its source (which stakeholder requested it and why) and forward to its implementation (design, code, test case).
- Requirements should have unique identifiers (e.g., FR-001, NFR-015) to enable tracking throughout the project lifecycle.
- Check: "Can I trace this requirement from origin to code to test?"

### How to Ensure Quality in Practice

- Conduct **peer reviews** of requirement documents — have analysts, developers, and testers review for different quality aspects.
- Use **checklists** — verify each requirement against the seven properties above.
- Hold **validation sessions** with stakeholders — read requirements back to confirm correctness.
- Create **prototypes** — demonstrate requirements in action to detect gaps and ambiguities.
- Maintain a **requirements management tool** — track status, priority, source, and changes for each requirement.

---

## 3.3 Elicitation Activities

> **Past Questions:**
> - **[Old1]** Who are the key actors and stakeholders in this system? Describe their roles. _(Q3a)_
> - **[Old1]** Create two scenarios: customer purchasing a book, bookstore owner adding a book. Draft use cases. _(Q3b)_
> - **[Old2]** What are use cases and user stories? Discuss their role in requirement elicitation and how they can be refined. _(Q5a)_
> - **[Internal1]** Who are stakeholders for a software project? Explain with examples. _(Q3a)_
> - **[Internal3]** For an Online Bookstore: list key actors/stakeholders and their interests. _(Q3a)_
> - **[Internal3]** Create use cases for "Purchase a Book" and "Add New Book to Catalog." _(Q3b)_

### Identifying Actors and Stakeholders

**Stakeholder:** Any person, group, or organization that has an interest in or is affected by the system. Stakeholders include both those who interact with the system and those who don't but are impacted by it.

**Actor:** A specific role that directly **interacts with the system** during its operation. Actors can be human users or external systems.

**Key difference:** All actors are stakeholders, but not all stakeholders are actors. For example, a company CEO is a stakeholder (cares about ROI) but is not an actor (doesn't use the system directly).

**Example — Online Bookstore Platform:**

| Stakeholder/Actor | Type | Role/Interest |
|---|---|---|
| **Customer** | Actor | Browse books, search, purchase, track orders, provide reviews |
| **Bookstore Owner** | Actor | Add/update/remove books in catalog, manage inventory, view sales reports |
| **Delivery Personnel** | Actor | View delivery assignments, update delivery status, confirm delivery |
| **System Administrator** | Actor | Manage user accounts, monitor system performance, handle technical issues |
| **Payment Gateway** | External Actor | Process online payments, send payment confirmations |
| **Investors/Management** | Stakeholder (not actor) | Interested in profitability, growth metrics, user satisfaction |
| **Regulatory Bodies** | Stakeholder (not actor) | Ensure compliance with consumer protection and data privacy laws |

### Developing Scenarios and Use Cases

**Scenario:** A specific narrative describing a single path of interaction between an actor and the system. It tells a concrete story of how the system is used.

**Use Case:** A structured, generalized description of how an actor interacts with the system to achieve a specific goal. It includes the main success scenario plus alternate/exception flows.

**Example Scenario — Customer Purchasing a Book:**
1. Customer logs into the bookstore website.
2. Customer searches for "Software Engineering" in the search bar.
3. System displays a list of matching books with titles, authors, prices, and ratings.
4. Customer selects a book and views its details page.
5. Customer clicks "Add to Cart."
6. Customer proceeds to checkout.
7. Customer enters shipping address and selects payment method.
8. System processes the payment through the payment gateway.
9. System confirms the order and sends a confirmation email.
10. Customer receives the book within the estimated delivery time.

**Use Case — Purchase a Book:**

| Element | Details |
|---|---|
| **Use Case Name** | Purchase a Book |
| **Actor** | Customer |
| **Precondition** | Customer has a registered account and is logged in |
| **Main Flow** | 1. Customer searches for a book. 2. System displays matching results. 3. Customer selects a book. 4. Customer adds book to cart. 5. Customer proceeds to checkout. 6. Customer enters shipping and payment details. 7. System validates payment via payment gateway. 8. System confirms order and sends email. |
| **Alternate Flows** | A1: Book is out of stock → system displays "Out of Stock" message and suggests similar books. A2: Payment fails → system notifies customer and asks to retry or use a different method. |
| **Postcondition** | Order is placed, payment is processed, and confirmation email is sent. |

**Use Case — Add New Book to Catalog:**

| Element | Details |
|---|---|
| **Use Case Name** | Add New Book to Catalog |
| **Actor** | Bookstore Owner |
| **Precondition** | Bookstore Owner is logged in with admin privileges |
| **Main Flow** | 1. Owner selects "Add New Book" from the dashboard. 2. Owner enters book details (title, author, ISBN, price, description, cover image, stock quantity). 3. System validates the input fields. 4. System adds the book to the catalog database. 5. System displays confirmation: "Book added successfully." |
| **Alternate Flows** | A1: ISBN already exists → system notifies owner and offers to update the existing entry. A2: Required fields missing → system highlights missing fields. |
| **Postcondition** | New book is visible in the catalog and available for purchase. |

### Refining Use Cases and User Stories

**User Story** — a lightweight, Agile format for expressing requirements from the end-user's perspective:

**Format:** *As a [role], I want [feature], so that [benefit].*

**Examples:**
- As a **customer**, I want to search for books by title or author, so that I can quickly find books I'm interested in.
- As a **bookstore owner**, I want to add new books to the catalog, so that customers can purchase them.
- As a **delivery person**, I want to update the delivery status, so that customers can track their orders in real time.

**Refining use cases involves:**
- Adding **alternate and exception flows** — what happens when things go wrong?
- Specifying **preconditions and postconditions** — what must be true before and after?
- Defining **acceptance criteria** — how do we know this use case is correctly implemented?
- Decomposing large use cases into **smaller, manageable ones** if they become too complex.
- Adding **non-functional constraints** — performance, security, and usability considerations for each use case.

**Refining user stories involves:**
- Adding **acceptance criteria** (Given-When-Then format).
- Breaking large stories into smaller, independently deliverable stories.
- Applying the **INVEST** criteria: Independent, Negotiable, Valuable, Estimable, Small, Testable.

### Identifying Relationships Among Actors and Use Cases

In a use case diagram, relationships show how actors and use cases connect:

**Association:** A solid line connecting an actor to a use case, indicating the actor participates in that use case.

**Include (<<include>>):** A dashed arrow from a base use case to an included use case. Represents **mandatory** shared behavior. The base use case always performs the included use case.
- Example: "Purchase Book" <<include>> "Process Payment" — every purchase must process a payment.

**Extend (<<extend>>):** A dashed arrow from an extending use case to a base use case. Represents **optional** behavior that only occurs under certain conditions.
- Example: "Apply Discount Coupon" <<extend>> "Purchase Book" — applying a coupon is optional, not every purchase uses one.

**Generalization:** A solid line with a triangular arrowhead from a specialized actor/use case to a general one. Represents **inheritance**.
- Actor example: "Premium Customer" generalizes "Customer" — inherits all customer use cases but may have additional ones (e.g., "Access Premium Content").
- Use case example: "Pay by Credit Card" and "Pay by Mobile Wallet" generalize "Process Payment."

---

## 3.4 Managing Requirements

> **Past Questions:**
> - **[Internal1]** What is a traceability matrix? How is it used? _(Q3b)_
> - **[Internal3]** How would you prioritize and manage conflicting requirements from different stakeholders? What techniques/tools would you use? _(Q2a OR)_

### Maintaining Traceability

**Requirements traceability** is the ability to trace a requirement throughout the entire software lifecycle — from its origin (stakeholder need) through design, implementation, testing, and deployment.

**Requirements Traceability Matrix (RTM):**

An RTM is a document (usually a table) that maps each requirement to its related artifacts:

| Req ID | Requirement Description | Source | Design Reference | Code Module | Test Case ID | Status |
|---|---|---|---|---|---|---|
| FR-001 | Customer can search books by title | Client interview | Design-3.2 | search.py | TC-012 | Implemented |
| FR-002 | Customer can add books to cart | Workshop-2 | Design-3.4 | cart.py | TC-015 | In Testing |
| NFR-001 | Search results load within 2 seconds | SLA agreement | Design-7.1 | search.py | TC-050 | Verified |

**Purpose of the RTM:**
- **Forward traceability** — traces from requirements to design/code/tests, ensuring every requirement is implemented and tested.
- **Backward traceability** — traces from design/code back to requirements, ensuring every piece of code exists because of a valid requirement (no "gold-plating").
- **Impact analysis** — when a requirement changes, the RTM shows exactly which design, code, and test artifacts are affected.
- **Completeness verification** — easily spot requirements that have no test cases or no implementation.
- **Audit compliance** — provides evidence that all requirements have been addressed, critical for regulated industries.

### Negotiating Specifications with Clients

Conflicts arise when different stakeholders have **competing or contradictory** requirements. Negotiation is the process of reaching agreement on what the system will and will not do.

**Common conflict scenarios:**
- End users want maximum features; managers want minimum cost and faster delivery.
- Marketing wants a flashy UI; security team wants strict access controls that add complexity.
- Different user groups want different workflows for the same process.

**Negotiation techniques:**
- **Prioritization (MoSCoW Method)** — classify requirements as Must have, Should have, Could have, Won't have (this time). This forces stakeholders to distinguish critical from nice-to-have features.
- **Cost-benefit analysis** — for disputed requirements, estimate the implementation cost and compare it to the expected business value.
- **Prototyping** — build quick prototypes of conflicting alternatives so stakeholders can evaluate them objectively.
- **Timeboxing/Phasing** — agree to implement high-priority requirements first and defer lower-priority ones to future releases.
- **Facilitated workshops** — bring conflicting stakeholders together with a neutral facilitator to discuss trade-offs and reach consensus.
- **Voting/Ranking** — have stakeholders score or rank requirements to quantify priorities democratically.

**Best Practices:**
- Involve a neutral facilitator (Business Analyst, Product Owner) to mediate conflicts.
- Document all negotiation decisions and their rationale for future reference.
- Focus discussions on **business value and risk**, not personal preferences.
- Ensure all stakeholder groups feel heard, even if their specific request is deferred.

### Documenting Requirements

Requirements must be formally documented to serve as a **contract** between stakeholders and the development team, and as the **baseline** for design, testing, and change management.

**Software Requirements Specification (SRS):**

The SRS is the primary requirements document. A standard SRS (IEEE 830) typically includes:

- **Introduction** — purpose, scope, definitions, acronyms, references, overview.
- **Overall Description** — product perspective, product functions, user characteristics, constraints, assumptions, and dependencies.
- **Specific Requirements** — detailed functional requirements (organized by feature or use case), non-functional requirements (performance, security, reliability, usability), and interface requirements (user, hardware, software, communication interfaces).
- **Appendices** — supporting models (use case diagrams, data flow diagrams, entity-relationship diagrams), glossary, index.

**Other documentation formats:**
- **User Stories** (Agile) — lightweight cards with acceptance criteria, stored in a product backlog tool (Jira, Trello).
- **Use Case Documents** — detailed descriptions of each use case with actors, flows, pre/post conditions.
- **Prototypes/Wireframes** — visual representations of the UI that complement textual requirements.

**Documentation best practices:**
- Use **unique IDs** for every requirement (FR-001, NFR-015) to enable traceability.
- Write requirements in **clear, simple language** — avoid jargon and ambiguity.
- Keep requirements **atomic** — each requirement should describe one and only one thing.
- Version-control the requirements document (e.g., Git) to track changes over time.
- Get formal **sign-off** from stakeholders before proceeding to design.
- Maintain a **change log** — every modification to a requirement should be recorded with date, author, reason, and impact.

---

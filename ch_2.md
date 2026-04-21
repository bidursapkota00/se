# Unit II: Software Process Models and Project Management

---

## 2.1 Agile Development Principles

> **Past Questions:**
>
> - **[Old2]** Would Agile be suitable for a government tax filing system with strict compliance? What challenges might arise? _(Q1a)_
> - **[Internal1]** For a small project describe the different agile terminologies. _(Q2a)_
> - **[Internal2]** Would you recommend Agile for a startup with frequently changing requirements? Why? _(Q1a)_
> - **[Internal2]** What advantages might the team experience if they use Agile? _(Q1b)_
> - **[Internal2]** What challenges or disadvantages could arise from using Agile? _(Q1c)_

<!-- **Twelve Agile Principles (selected key ones):**
- Deliver working software frequently (weeks to months, preferring shorter timescales).
- Welcome changing requirements, even late in development.
- Business people and developers must work together daily.
- The best architectures, requirements, and designs emerge from self-organizing teams.
- Working software is the primary measure of progress.
- Continuous attention to technical excellence and good design.
- At regular intervals, the team reflects on how to become more effective. -->

### Key Agile Terminologies

- **Sprint** — a fixed time-box (usually 1–4 weeks) during which a usable product increment is created.
- **User Story** — a short description of a feature from the end-user's perspective (format: _As a [user], I want [feature], so that [benefit]_).
- **Product Backlog** — a prioritized list of all desired features, enhancements, and fixes for the product.
- **Sprint Backlog** — the subset of product backlog items selected for the current sprint.
- **Increment** — the sum of all completed backlog items at the end of a sprint; must be in a "Done" state.
- **Velocity** — the amount of work a team can complete in one sprint (measured in story points).
- **Burndown Chart** — a graph showing remaining work vs. time in a sprint.
- **Daily Standup** — a brief (15-minute) daily meeting where each member shares what they did, what they'll do, and any blockers.
- **Retrospective** — a meeting at the end of each sprint to reflect on what went well, what didn't, and how to improve.

<!-- ### Benefits of Agile Methodologies

- **Flexibility** — accommodates changing requirements at any point without derailing the project.
- **Faster delivery** — working software is delivered in small increments every sprint.
- **Customer satisfaction** — continuous client involvement ensures the product meets actual needs.
- **Early risk detection** — frequent iterations expose problems early when they are cheaper to fix.
- **Team morale** — self-organizing teams, collaboration, and transparency foster ownership.
- **Continuous improvement** — retrospectives drive process refinement after every sprint. -->

<!-- ### Challenges/Disadvantages of Agile

- **Scope creep** — without disciplined backlog management, features keep getting added.
- **Poor documentation** — emphasis on working software may lead to insufficient documentation.
- **Requires high client involvement** — stakeholders must be available continuously, which is not always feasible.
- **Difficult to estimate cost/timeline** — iterative nature makes long-term planning harder.
- **Not ideal for compliance-heavy projects** — strict regulatory environments (e.g., government, healthcare) need extensive documentation and fixed specifications that conflict with Agile's lightweight approach.
- **Team dependency** — success depends heavily on team maturity, communication skills, and self-discipline. -->

### When Agile Is Not Suitable

Agile may not be the best fit for projects with:

- Fixed legal/regulatory requirements that demand upfront, detailed documentation (e.g., tax systems, defense contracts).
- Projects where the client is unavailable for regular feedback.
<!-- - Very large teams distributed across time zones without strong communication tools. -->

**Mitigation if Agile is still chosen:** Use hybrid approaches — combine Agile's iterative delivery with additional documentation practices. Use "Compliance Sprints" dedicated to regulatory review. Maintain a living SRS that evolves with sprints.

---

## 2.2 Scrum and Kanban Methodologies

> **Past Questions:**
>
> - **[Old2]** Explain the key roles, artifacts, and ceremonies in Scrum. How do they contribute to project success? _(Q4a)_

### Scrum Framework

Scrum is an **Agile framework** for managing complex product development. It uses fixed-length iterations called **Sprints** (typically 2–4 weeks) to deliver incremental value.

### Scrum Roles

- **Product Owner** — represents stakeholders, owns the Product Backlog, defines and prioritizes features, ensures the team builds the right product. The single voice of the customer.
- **Scrum Master** — serves the team by facilitating Scrum events, removing impediments, coaching the team on Agile practices, and shielding the team from distractions. Not a traditional manager — a servant-leader.
- **Development Team** — a cross-functional, self-organizing group (typically 5–9 members) responsible for designing, building, testing, and delivering the product increment each sprint.

### Scrum Artifacts

- **Product Backlog** — a single, ordered list of everything needed in the product. Continuously refined by the Product Owner. Items at the top are detailed and ready; items lower are less defined.
- **Sprint Backlog** — the set of Product Backlog items selected for the sprint, plus a plan for delivering them. Owned by the Development Team.
- **Increment** — the usable output at the end of a sprint. Must meet the team's **Definition of Done** (DoD) — a shared checklist of quality criteria (e.g., code reviewed, tests passed, documented).

### Scrum Ceremonies (Events)

All events are **time-boxed** to maintain focus and prevent waste.

- **Sprint Planning** — held at the start of each sprint. The team selects items from the Product Backlog and creates a plan for the sprint. Answers: _What can we deliver?_ and _How will we do it?_
- **Daily Scrum (Standup)** — a 15-minute daily meeting for the Development Team. Each member answers: What did I do yesterday? What will I do today? Are there any blockers?
- **Sprint Review** — held at the end of the sprint. The team demonstrates the completed increment to stakeholders, collects feedback, and updates the Product Backlog accordingly.
- **Sprint Retrospective** — held after the Sprint Review. The team reflects on the process: What went well? What can be improved? What actions will we take in the next sprint?

### How Roles, Artifacts, and Ceremonies Contribute to Success

- **Transparency** — artifacts (backlogs, increment) make work visible to everyone. Daily Scrums expose blockers immediately.
- **Inspection** — Sprint Reviews and Retrospectives provide regular checkpoints to evaluate both the product and the process.
- **Adaptation** — feedback from reviews and retrospectives allows the team to adjust priorities and improve processes continuously.
- **Accountability** — clear roles prevent overlap and confusion. The Product Owner owns _what_ to build; the team owns _how_.
- **Focus** — time-boxed sprints prevent scope creep within an iteration. The sprint goal keeps the team aligned.

### Kanban Methodology

Kanban is a **visual, flow-based** Agile method rooted in Lean manufacturing principles. Unlike Scrum, it has **no fixed iterations** — work flows continuously.

### Kanban Board

A Kanban board visualizes the entire workflow using:

- **Columns** — represent stages of work (e.g., Backlog → To Do → In Progress → Code Review → Testing → Done).
- **Cards** — represent individual work items (user stories, tasks, bugs). Each card moves from left to right across the board.
- **WIP Limits** — a number displayed on each column indicating the maximum items allowed in that stage simultaneously. Prevent multitasking overload, Expose bottlenecks

<!-- ### Kanban Principles

1. **Start with what you do now** — no immediate process overhaul required; map existing workflow first.
2. **Agree to pursue incremental change** — improve gradually, not through drastic transformation.
3. **Respect current roles and responsibilities** — build upon existing structures.
4. **Encourage leadership at all levels** — anyone can propose improvements.

### Kanban Practices

- **Visualize the work** — make all tasks visible on the board.
- **Limit Work-in-Progress (WIP)** — restrict the number of items in each stage to prevent overload and context switching.
- **Manage flow** — monitor how smoothly and quickly items move through the board; identify and resolve bottlenecks.
- **Make policies explicit** — clearly define rules for each column (e.g., "Definition of Done for Testing").
- **Implement feedback loops** — regular standup meetings, retrospectives, and reviews.
- **Improve collaboratively** — use data (lead time, cycle time) to evolve the process. -->

<!-- ### Why WIP Limits Matter

- **Prevent multitasking overload** — forces the team to finish current work before starting new tasks.
- **Expose bottlenecks** — when a column hits its WIP limit, work piles up, making the blockage visible and forcing resolution.
- **Improve throughput** — fewer items in progress means faster completion of each item.
- **Increase predictability** — steady flow allows better forecasting of delivery dates. -->

### Scrum vs. Kanban

| Aspect            | Scrum                                  | Kanban                                   |
| ----------------- | -------------------------------------- | ---------------------------------------- |
| **Cadence**       | Fixed sprints (2–4 weeks)              | Continuous flow                          |
| **Roles**         | Product Owner, Scrum Master, Dev Team  | No prescribed roles                      |
| **Change Policy** | Changes wait until next sprint         | Changes can be made anytime              |
| **Metrics**       | Velocity (story points/sprint)         | Lead time, cycle time                    |
| **Planning**      | Sprint Planning at start               | Continuous replenishment                 |
| **WIP Limits**    | Implicit (sprint capacity)             | Explicit per column                      |
| **Best For**      | Projects needing structured iterations | Support/maintenance, continuous delivery |

---

## 2.3 DevOps Culture and Principles

> **Past Questions:**
>
> - **[Internal3]** What is the role of DevOps culture and CI/CD in modern software development? How do they improve delivery speed and reliability? _(Q1b)_

### What is DevOps?

DevOps is a **cultural and technical movement** that unifies software **Development (Dev)** and IT **Operations (Ops)** into a collaborative, shared-responsibility model. It aims to shorten the development lifecycle and deliver high-quality software continuously.

### Core DevOps Principles

- **Collaboration** — break down silos between Dev and Ops teams. Both share responsibility for the software's performance from development to production.
- **Automation** — automate repetitive tasks (build, test, deploy, monitor) to reduce human error and increase speed.
- **Continuous Improvement** — learn from failures, optimize processes, minimize waste.
- **Shared Responsibility** — end the "throw it over the wall" mentality. Developers care about operations; operations care about development.
- **Measurement and Feedback** — use metrics (deployment frequency, lead time, failure rate, mean time to recovery) to drive data-informed decisions.

### Continuous Integration / Continuous Deployment (CI/CD)

**CI/CD** is the technical backbone of DevOps, enabling frequent, reliable software releases.

**Continuous Integration (CI):**

- Developers merge code changes into a shared repository **multiple times a day**.
- Each merge triggers an **automated build and test** pipeline.
- **Goal:** detect integration issues early, keep the codebase stable, and prevent "integration hell."

**Continuous Delivery (CD):**

- An extension of CI where every code change that passes automated tests is **automatically prepared for release** to production.
- Deployment to production requires a **manual approval** step.

**Continuous Deployment (CD):**

- Goes further — every change that passes all automated tests is **automatically deployed to production** without manual intervention.
- Enables multiple production releases per day.

**CI/CD Pipeline (typical flow):**

1. Developer commits code → 2. Automated build triggered → 3. Unit tests run → 4. Integration tests run → 5. Code quality checks → 6. Package/containerize → 7. Deploy to staging → 8. Acceptance tests → 9. Deploy to production

### How DevOps and CI/CD Improve Delivery

- **Speed** — automated pipelines drastically reduce time from code commit to production deployment.
- **Reliability** — automated testing catches defects early; automated deployments reduce human error.
- **Frequency** — enables deploying multiple times per day instead of quarterly/yearly releases.
- **Quick recovery** — if a deployment fails, automated rollback mechanisms restore the previous version rapidly.
- **Feedback loops** — monitoring in production provides immediate feedback for the next development cycle.
- **Quality** — continuous testing at every stage ensures higher code quality and fewer production bugs.

### Collaboration Between Development and Operations

**Traditional approach (pre-DevOps):**

- Dev team writes code → throws it to Ops for deployment → Ops struggles with environment differences → blame game when things break.

**DevOps approach:**

- Dev and Ops work together throughout the lifecycle.
- **Shared tools** — both teams use the same CI/CD pipelines, monitoring dashboards, and incident management systems.
- **Infrastructure as Code (IaC)** — infrastructure is defined in version-controlled code (e.g., Terraform, Ansible), treated like application code.
- **Shared on-call** — developers participate in on-call rotations, giving them direct exposure to production issues.
- **Blameless postmortems** — when failures occur, the focus is on systemic causes and preventive measures, not individual blame.

---

## 2.4 Project Organization Concepts

> **Past Questions:**
>
> - **[Old1]** How do project organization factors (roles, task distribution, scheduling) interact with communication practices to shape project success? _(Q2a)_
> - **[Internal3]** Explain how roles, task distribution, and communication influence project success. Give an example of a communication breakdown. _(Q2a)_

### Project Organizations and Roles

A project organization defines the **structure, roles, and reporting relationships** within a software project team.

**Common Organizational Structures:**

- **Functional Organization** — team members grouped by specialization (e.g., all testers together, all developers together). Expertise is deep but cross-team communication is weak.
- **Project-based Organization** — team members from different specializations are organized around a specific project. Better communication but may lose functional expertise depth.
- **Matrix Organization** — combines both; team members report to both a functional manager and a project manager. Flexible but can create confusion with dual reporting.

**Key Roles in a Software Project:**

- **Project Manager** — overall planning, scheduling, risk management, resource allocation, stakeholder communication.
- **Team Lead / Tech Lead** — provides technical direction, reviews architecture decisions, mentors developers.
- **Developer** — implements features, writes code, performs unit testing.
- **QA/Tester** — verifies that the software meets requirements through systematic testing.
- **Business Analyst** — translates business needs into technical requirements.
- **Product Owner** (Agile) — prioritizes backlog, represents stakeholders.
- **Scrum Master** (Agile) — facilitates Scrum process, removes blockers.

### Task Assignment and Work Products

**Task Assignment** involves distributing work to team members based on:

- **Skills and expertise** — match tasks to the most qualified person.
- **Availability and workload** — avoid overburdening individuals.
- **Dependencies** — consider which tasks must finish before others can start.
- **Ownership** — encourage team members to take ownership of tasks for accountability.

**Work Products** at the project management level include:

- Project plan (schedule, milestones, budget)
- Work Breakdown Structure (WBS) — hierarchical decomposition of the project into manageable tasks
- Risk register — documented risks with mitigation strategies
- Status reports — regular updates on progress, blockers, and metrics
- Meeting minutes — documented outcomes of all formal meetings

### Scheduling and Time Management

**Scheduling** is the process of mapping tasks to timelines and resources.

**Key Techniques:**

- **Work Breakdown Structure (WBS)** — decompose the project into phases → activities → tasks.
- **Gantt Charts** — visual timeline showing tasks, durations, dependencies, and milestones.
- **Critical Path Method (CPM)** — identify the longest sequence of dependent tasks; any delay on the critical path delays the entire project.
- **PERT (Program Evaluation and Review Technique)** — uses optimistic, pessimistic, and most likely time estimates to calculate expected duration.
- **Milestones** — key checkpoints that mark the completion of significant deliverables.

**Time Management Practices:**

- Set realistic deadlines based on estimation techniques (not guesswork).
- Build buffer time for unforeseen risks.
- Track progress regularly against the baseline schedule.
- Re-prioritize tasks when requirements or resources change.

### How Roles, Tasks, and Scheduling Interact

- **Clear roles** prevent duplication of effort and ensure accountability.
- **Proper task assignment** ensures the right person does the right work, reducing rework.
- **Effective scheduling** shows dependencies and deadlines, enabling the team to coordinate.
- **When these are misaligned:** tasks fall through the cracks, team members block each other, deadlines are missed, and quality suffers.

**Example of Communication Breakdown:** A developer assumes a UI change is purely cosmetic and implements it without informing the tester. The tester's existing test cases become invalid, causing wasted effort and delayed testing. **Prevention:** establish a practice where any requirement or design change must be communicated to all affected roles via a shared tracking tool (e.g., Jira ticket update, Slack channel notification).

---

## 2.5 Project Communication

> **Past Questions:**
>
> - **[Internal1]** Communication is key to successful software development. Do you agree? Justify. Describe how formal and informal communication impacts development. _(Q2b)_

### Why Communication Matters

Communication is the **single most critical factor** in software project success. Studies consistently show that poor communication is a leading cause of project failure — not technical incompetence.

Software projects involve diverse stakeholders (clients, developers, testers, managers) with different vocabularies, priorities, and expectations. Effective communication ensures everyone shares a common understanding of goals, requirements, progress, and risks.

### Planned (Formal) Communication

Planned communication is **structured, scheduled, and documented**. It provides a reliable information flow.

**Examples:**

- **Sprint Planning / Kickoff Meetings** — align the team on goals and deliverables at the start of each iteration.
- **Daily Standups** — brief sync to share progress and surface blockers.
- **Sprint Reviews / Demos** — demonstrate completed work to stakeholders for feedback.
- **Retrospectives** — reflect on process improvements.
- **Status Reports** — written updates (weekly/monthly) to management and clients on progress, risks, and metrics.
- **Design Reviews / Code Reviews** — formal examination of technical work for quality and correctness.
- **Client Meetings** — scheduled sessions for requirement clarification, feedback, and sign-off.

**Impact on Development:**

- Ensures alignment between team and stakeholders.
- Creates documented decisions that can be referenced later.
- Provides regular checkpoints to catch deviations early.

### Unplanned (Informal) Communication

Unplanned communication is **spontaneous and undocumented**. It happens naturally during collaboration.

**Examples:**

- Hallway / desk-side conversations between developers.
- Quick Slack/Teams messages asking for clarification.
- Pair programming sessions where knowledge is exchanged organically.
- Casual discussions during coffee breaks that resolve design ambiguities.

**Impact on Development:**

- Resolves issues quickly without waiting for the next scheduled meeting.
- Fosters team bonding and trust.
- Facilitates rapid knowledge transfer.
- **Risk:** important decisions made informally may be lost if not documented. Can lead to miscommunication if only some team members are involved.

### Communication Mechanisms and Tools

- **Synchronous** — meetings (in-person or video), phone calls, live chat — for real-time discussion.
- **Asynchronous** — email, project management tools (Jira, Trello), documentation wikis (Confluence), version control comments — for non-urgent communication across time zones.
- **Visual tools** — Kanban boards, dashboards, burndown charts — for at-a-glance project status.

### Best Practices for Project Communication

- Define a **communication plan** at project start — who communicates what, to whom, how often, and through which channel.
- Document all important decisions (even if made informally).
- Prefer **async-first** — use written communication for non-urgent matters to minimize meeting overload.
- Keep meetings focused with a clear agenda and time-box.
- Use a **single source of truth** (shared project management tool) to avoid information fragmentation.

---

## 2.6 Introduction to DevOps Tools

> **Past Questions:**
>
> - **[Old1]** What is Docker, and in what ways does it simplify deployment and management across diverse environments? _(Q2b)_
> - **[Internal3]** Explain containerization. How does Docker simplify deployment? Mention one benefit over traditional VMs. _(Q2b)_

### Overview of Jenkins, Docker, and Kubernetes

These three tools are complementary — they work together in a modern DevOps CI/CD pipeline.

### Jenkins — Automation Server

**What it is:** An open-source automation server that orchestrates CI/CD pipelines.

**What it does:**

- Monitors source code repositories (e.g., GitHub) for changes.
- Automatically triggers builds when new code is committed.
- Runs automated tests (unit, integration, acceptance).
- Packages the application for deployment.
- Triggers deployment to staging or production environments.

**Key Features:**

- **Pipeline as Code** — CI/CD workflows defined in a `Jenkinsfile` stored in version control.
- **Plugin ecosystem** — 1,800+ plugins for integration with virtually any tool (Git, Docker, Kubernetes, Slack, Jira).
- **Distributed builds** — can distribute build workloads across multiple machines (master-agent architecture).

**Role in DevOps:** Jenkins is the **orchestrator** — it coordinates the entire build → test → deploy pipeline.

### Docker — Containerization Platform

**What it is:** A platform that packages applications and their dependencies into lightweight, portable **containers**.

**The Problem Docker Solves:** _"It works on my machine"_ — where software behaves differently in development, testing, and production due to environment differences (OS versions, library versions, configurations).

**How Docker Works:**

- A **Dockerfile** defines the application's environment (base OS, dependencies, configuration, startup command).
- Docker builds this into an **image** — a read-only template containing everything needed to run the application.
- An image is run as a **container** — a lightweight, isolated instance of the application.

**Key Benefits:**

- **Environment consistency** — the same container runs identically on a developer's laptop, test server, and production cloud.
- **Isolation** — each container runs in its own isolated environment, preventing conflicts between applications.
- **Portability** — containers can run on any system with Docker installed (Linux, Windows, cloud providers).
- **Lightweight** — containers share the host OS kernel, unlike VMs which need a full guest OS.
- **Fast startup** — containers start in seconds, unlike VMs which take minutes.

### Containerization: Docker vs. Virtual Machines

| Aspect             | Docker Containers          | Virtual Machines                   |
| ------------------ | -------------------------- | ---------------------------------- |
| **Virtualizes**    | Operating system           | Hardware                           |
| **Includes**       | App + dependencies only    | Full guest OS + app + dependencies |
| **Size**           | Megabytes                  | Gigabytes                          |
| **Startup Time**   | Seconds                    | Minutes                            |
| **Resource Usage** | Lightweight, shared kernel | Heavy, dedicated resources         |
| **Isolation**      | Process-level              | Hardware-level (stronger)          |
| **Density**        | Many containers per host   | Fewer VMs per host                 |

**Key benefit over VMs:** Docker containers are far more lightweight and efficient because they share the host OS kernel instead of running a full guest operating system, enabling faster startup, lower resource usage, and higher density on the same hardware.

### Kubernetes (K8s) — Container Orchestrator

**What it is:** An open-source platform (originally developed by Google) that automates the deployment, scaling, and management of containerized applications across clusters of machines.

**The Problem Kubernetes Solves:** Docker runs containers on a single machine. In production, applications need to run across multiple servers with automatic scaling, load balancing, and fault tolerance. Kubernetes manages this complexity.

**Key Features:**

- **Auto-scaling** — automatically adds or removes container instances based on CPU/memory usage or traffic.
- **Self-healing** — automatically restarts containers that crash, replaces unhealthy containers, and reschedules them onto healthy nodes.
- **Load Balancing** — distributes incoming network traffic evenly across container instances.
- **Rolling Updates** — deploys new versions gradually (replacing old containers one by one) to achieve zero-downtime deployments.
- **Service Discovery** — containers can find and communicate with each other automatically.

**Role in DevOps:** Kubernetes is the **production runtime manager** — it ensures containerized applications run reliably at scale.

### How Jenkins, Docker, and Kubernetes Work Together

A typical CI/CD pipeline flow:

1. **Developer pushes code** to a Git repository.
2. **Jenkins** detects the change, triggers the pipeline.
3. **Jenkins uses Docker** to build a container image of the application.
4. **Jenkins runs automated tests** inside temporary containers.
5. On success, the **Docker image is pushed** to a container registry (e.g., Docker Hub).
6. **Jenkins instructs Kubernetes** to deploy the new image.
7. **Kubernetes** performs a rolling update — pulls the new image, spins up new containers, shuts down old ones with zero downtime.

> **Jenkins** builds and tests → **Docker** packages → **Kubernetes** deploys and manages at scale.

---

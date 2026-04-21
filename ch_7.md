# Unit VII: Configuration Management and DevOps Tools

---

## 7.1 Configuration Management Planning

> **Past Questions:**
> - **[Old1]** Explain the importance of configuration items, baselines, and change management processes. How do these ensure controlled updates? _(Q6b)_
> - **[Old2]** Define Configuration Items and Baselines. How do they help control changes and maintain software integrity? _(Q6b)_

### What is Software Configuration Management (SCM)?

SCM is a discipline that provides **systematic control over the changes** made to a software system throughout its lifecycle. It ensures that the software product maintains its integrity, consistency, and traceability from development through deployment and maintenance.

SCM answers: *What changed? When did it change? Who changed it? Why was it changed? Can we go back?*

### Importance of Configuration Management

- **Prevents chaos** — without SCM, teams lose track of which version is current, what changes were made, and who made them.
- **Enables collaboration** — multiple developers can work on the same codebase simultaneously without overwriting each other's work.
- **Ensures traceability** — every change is linked to a reason (requirement, bug report, enhancement request).
- **Supports reproducibility** — any previous version of the software can be rebuilt from the repository at any time.
- **Reduces risk** — unauthorized or untested changes are prevented from entering the production system.
- **Regulatory compliance** — provides an audit trail required in regulated industries (healthcare, finance, aviation).

### Configuration Items (CIs)

A **Configuration Item** is any artifact that is placed under configuration management — any component that must be uniquely identified, version-controlled, and tracked.

**Examples of CIs:**
- Source code files and modules.
- Requirements specifications (SRS).
- Design documents and UML models.
- Test plans, test cases, and test data.
- Build scripts and configuration files.
- User manuals and release notes.
- Database schemas.
- Third-party libraries and dependencies.

Each CI has a **unique identifier**, a **version number**, and a **change history**. CIs are stored in a **configuration management repository** (e.g., a Git repository).

### Baselines

A **baseline** is a formally reviewed, approved, and frozen snapshot of a set of configuration items at a specific point in time. Once established, a baseline can only be changed through a formal change control process.

**Types of Baselines:**
- **Functional Baseline** — approved requirements specification (SRS). Captures *what* the system must do.
- **Design Baseline (Allocated Baseline)** — approved design documents. Captures *how* the system will be built.
- **Product Baseline** — the approved, tested, and released software product. Captures the *final delivered system*.

**Why Baselines Matter:**
- Provide a **stable reference point** — all subsequent changes are tracked against the baseline.
- Enable **rollback** — if a new change introduces defects, the team can revert to the last stable baseline.
- Support **impact analysis** — when a change is proposed, the baseline shows exactly what will be affected.
- Ensure **consistency** — all team members work from the same agreed-upon version of each artifact.

### SCM Planning (The SCM Plan)

An SCM Plan defines how configuration management will be conducted for a project. It includes:

- **Configuration Identification** — which artifacts are CIs, naming conventions, versioning scheme.
- **Configuration Control** — the process for requesting, evaluating, approving, and implementing changes.
- **Configuration Status Accounting** — recording and reporting the current state and history of all CIs (version, status, change log).
- **Configuration Audits** — formal verification that the product matches its documentation and that all changes were properly authorized.

---

## 7.2 Change Management

> **Past Questions:**
> - **[Old2]** How is a change request managed in the SCM process? Write the procedure. _(Q2b)_
> - **[Old2]** How can version and release management help a team with frequent updates? Discuss tools and strategies. _(Q6b OR)_
> - **[Internal1]** What is SCM? Describe the process of incorporating change during software development. _(Q5b)_
> - **[Internal1]** Write short notes on: Versioning software. _(Q7b)_

### Managing Change Requests

Change is inevitable in software projects — requirements evolve, bugs are discovered, and new features are requested. **Change management** ensures these changes are handled in a **controlled, traceable, and systematic** manner rather than ad-hoc.

**Change Request Process:**

1. **Change Request Submission** — a stakeholder, developer, or tester submits a formal Request for Change (RFC) describing: what needs to change, why, expected impact, priority, and urgency.

2. **Impact Analysis** — the technical team evaluates: which CIs are affected, the effort required, risks involved, effects on schedule and budget, and dependencies with other modules.

3. **Evaluation and Approval** — a **Change Control Board (CCB)** reviews the change request and the impact analysis. The CCB decides to approve, reject, or defer the change. The CCB typically includes the project manager, technical lead, QA lead, and sometimes the client.

4. **Implementation** — if approved, the change is assigned to a developer who implements it in a separate branch. The change follows standard coding and review practices.

5. **Verification and Testing** — the change is tested (unit, integration, regression) to ensure it works correctly and has not broken existing functionality.

6. **Release and Closure** — the change is merged into the mainline, a new baseline is established, and the change request is formally closed with documentation of what was done.

**Change Categories:**
- **Standard** — routine, low-risk, pre-approved changes (e.g., minor UI fixes, dependency updates).
- **Normal** — medium-to-high risk changes requiring CCB review and formal approval.
- **Emergency** — critical fixes for production-breaking issues, using an expedited approval process.

### Version Management

**Version management** tracks the evolution of each configuration item through successive revisions.

**Version Numbering Convention (Semantic Versioning):**
- Format: **MAJOR.MINOR.PATCH** (e.g., v2.3.1)
- **MAJOR** — incremented for incompatible API changes or significant feature overhauls.
- **MINOR** — incremented for backward-compatible new features or enhancements.
- **PATCH** — incremented for backward-compatible bug fixes.

**Versioning Practices:**
- Every CI is stored in a version control system (Git, SVN) with a complete change history.
- Each version is associated with a commit message describing what changed and why.
- Tags are used to mark specific versions as releases (e.g., `v1.0.0`, `v2.1.0-beta`).
- Branching strategies (Git Flow, Trunk-Based Development) organize parallel development streams.

### Release Management

**Release management** governs the process of packaging, testing, and deploying a specific version of the software to users.

**Release Process:**
1. **Release Planning** — define scope (which features/fixes are included), schedule, and acceptance criteria.
2. **Build and Integration** — compile code, merge all approved changes, produce a deployable package.
3. **Testing** — rigorous testing on the release candidate (functional, integration, performance, security, UAT).
4. **Deployment** — move the release to production using a deployment strategy:
   - **Blue-Green** — maintain two identical environments; switch traffic from old (blue) to new (green).
   - **Canary** — release to a small percentage of users first; monitor for issues before full rollout.
   - **Rolling** — gradually replace old instances with new ones across the server cluster.
5. **Post-Release Monitoring** — monitor production for errors, performance degradation, or user-reported issues.
6. **Rollback Plan** — if critical issues are found, revert to the previous stable release.

**How Version and Release Management Help Teams:**
- Provides a clear history of what changed between releases.
- Enables parallel development (feature branches) without destabilizing the main codebase.
- Allows rapid rollback to a known-good state if a release causes problems.
- Facilitates multi-environment management (development → staging → production).

---

## 7.3 System Building

### Build Automation

**System building** is the process of compiling source code, linking libraries, running tests, and packaging the software into a deployable artifact. **Build automation** replaces manual build steps with scripts and tools.

**Build Tools:**
- **Make** — classic build tool using Makefiles (C/C++ projects).
- **Maven/Gradle** — Java build tools handling compilation, dependency management, testing, and packaging.
- **npm/yarn** — JavaScript build and dependency management.
- **MSBuild** — .NET build tool.

**What a Build Script Typically Does:**
1. Fetch dependencies from a package repository.
2. Compile source code into executable code.
3. Run automated unit tests.
4. Perform static code analysis and linting.
5. Package the application (JAR, WAR, Docker image, installer).
6. Generate build reports (test results, code coverage).

**Benefits of Build Automation:**
- **Repeatability** — same build script produces the same output every time.
- **Speed** — automated builds are faster than manual compilation.
- **Error reduction** — eliminates human mistakes in the build process.
- **Integration with CI/CD** — automated builds are triggered on every commit.

### Continuous Integration Practices

**Continuous Integration (CI)** is the practice of merging all developer working copies into a shared mainline multiple times per day, with each merge triggering an automated build and test.

**CI Best Practices:**
- **Commit frequently** — developers integrate code at least once per day, ideally multiple times.
- **Maintain a single source repository** — all code lives in one version-controlled repository.
- **Automate the build** — every commit triggers an automated build-and-test cycle.
- **Make the build self-testing** — include automated tests in the build process.
- **Fix broken builds immediately** — a failing build is the team's top priority.
- **Keep the build fast** — slow builds discourage frequent integration.
- **Test in a clone of production** — the CI environment should mirror production to catch environment-specific bugs.

---

## 7.4 CASE Tools for Configuration Management

> **Past Questions:**
> - **[Internal3]** Evaluate the use of VCS in managing requirements documents. How does a central repository improve collaboration, reduce risks, and ensure compliance? _(Q6b)_

### Overview of Git and Subversion

**CASE (Computer-Aided Software Engineering) tools** automate tasks across the SDLC. For configuration management, version control systems are the most critical CASE tools.

### Git (Distributed VCS)

**Architecture:** Every developer has a **full local copy** of the entire repository, including its complete history.

**Key Concepts:**
- **Repository (Repo)** — the database storing all files, branches, commits, and history.
- **Commit** — a snapshot of all tracked files at a point in time, with a message describing the change.
- **Branch** — an independent line of development. Default branch is `main` (or `master`).
- **Merge** — combining changes from one branch into another.
- **Pull Request (PR) / Merge Request** — a formal request to merge a branch, with code review and approval.
- **Clone** — creating a local copy of a remote repository.
- **Push/Pull** — sending local commits to / fetching remote commits from the remote repository.

**Basic Git Workflow:**
1. `git clone` — get a copy of the repository.
2. `git checkout -b feature-x` — create and switch to a new branch.
3. Make changes, then `git add .` and `git commit -m "description"`.
4. `git push origin feature-x` — push the branch to the remote.
5. Create a Pull Request → code review → approval → merge into main.
6. CI pipeline runs automated tests on the merged code.

**Branching Strategies:**
- **Git Flow** — separate branches for features, releases, hotfixes, and development. Structured but complex.
- **Trunk-Based Development** — developers work on short-lived branches and merge into main frequently. Simpler, preferred for CI/CD.
- **GitHub Flow** — simplified: main branch is always deployable; feature branches merge via PRs.

### Subversion (SVN) — Centralized VCS

**Architecture:** A **single central repository** on a server. Developers check out files, modify them, and commit changes back to the server.

**Key Differences from Git:**
- No local repository — requires network access for most operations.
- Linear history — branching and merging are less flexible than Git.
- Simpler access control — directory-level permissions are easier to manage.
- Better for large binary files — SVN handles binary assets more efficiently than Git.

### How VCS Improves Collaboration and Compliance

- **Central repository** — single source of truth; all team members access the same codebase.
- **Change tracking** — every modification is recorded with author, date, message, and diff.
- **Audit trail** — provides a complete history for compliance and regulatory audits.
- **Parallel development** — branching allows multiple features/fixes to be developed simultaneously.
- **Conflict resolution** — merge tools detect and help resolve conflicting changes.
- **Backup and recovery** — the repository preserves every version; any past state can be restored.
- **Code review** — pull requests enforce review and approval before changes enter the main branch.

---

## 7.5 DevOps Tools in Configuration Management

### Advanced Use of Jenkins, Docker, and Kubernetes

In Configuration Management, Jenkins, Docker, and Kubernetes extend beyond basic CI/CD (covered in Chapter 2) to provide **infrastructure-level configuration control**.

**Jenkins in CM:**
- **Pipeline as Code** — Jenkinsfiles stored in version control define the entire build/test/deploy pipeline as a CI. Changes to the pipeline go through the same review process as application code.
- **Environment configuration** — Jenkins manages environment-specific settings (dev, staging, production) through parameterized pipelines.
- **Artifact management** — Jenkins archives build artifacts with version numbers, enabling traceability between source code and deployed binaries.

**Docker in CM:**
- **Infrastructure as Code** — Dockerfiles define the entire runtime environment (OS, libraries, dependencies). The Dockerfile itself is a configuration item under version control.
- **Immutable infrastructure** — once a Docker image is built, it doesn't change. The same image deployed in staging is identical to what runs in production.
- **Environment consistency** — eliminates configuration drift between environments.
- **Reproducibility** — any version of the application can be reproduced by building its tagged Dockerfile.

**Kubernetes in CM:**
- **Declarative configuration** — Kubernetes manifests (YAML files) declare the desired state of the system (how many replicas, which image version, resource limits). These files are stored in version control.
- **Configuration management** — Kubernetes ConfigMaps and Secrets manage application configuration separately from code.
- **Automated rollback** — if a new deployment fails health checks, Kubernetes automatically rolls back to the previous version.
- **GitOps** — a practice where the Git repository is the single source of truth for both application code and infrastructure configuration. Tools like ArgoCD or Flux automatically sync the cluster state with the Git repository.

**Together:** Jenkins automates the pipeline, Docker packages the application and environment, and Kubernetes manages the deployment configuration — all version-controlled, auditable, and reproducible.

---

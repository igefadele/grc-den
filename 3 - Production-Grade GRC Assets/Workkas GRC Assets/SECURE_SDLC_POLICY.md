# Standard Operating Procedure: Secure Software Development Lifecycle (SDLC)

**Document Reference:** SOP-SDLC-WORK-002
**Version:** 2026.1
**Target Scope:** Workkas Core Engineering & DevOps Squads
**Enforcement Level:** Mandatory

---

## 1. Objective
To treat secure coding metrics, strict data isolation boundaries, and international regulatory compliance constraints as absolute development requirements from design to runtime deployment, systematically preventing vulnerability creation.

---

## 2. Phase-by-Phase Secure Engineering Lifecycle

[System Design] ──► [Hardened Coding] ──► [CI/CD Security Screening] ──► [Continuous CCM Verification]


### Phase 1: Planning & Architecture (Threat Modeling)
Before writing code for any expansion (such as escrow management modifications, KYC upgrades, identity mapping tools, or wallet configurations), teams must execute a comprehensive threat model. Engineering squads must document:
* Precision categorization of data vectors passing through the component.
* Applied structural access bounds matching the principle of least privilege.
* Security isolation perimeters covering external immigration and banking gateways.

### Phase 2: Implementation (Secure Coding Standards)
* All software modules must implement native framework protections to neutralize the OWASP Top 10 web application vulnerabilities and vulnerabilities associated with international processing networks.
* Third-party software dependencies must pass automated verification gates before installation. Software modules presenting inactive upkeep history or unpatched security vulnerabilities are banned from the codebase.

### Phase 3: Review & Automated Code Screening (GitHub Branch Protection Rules)
The core code repository enforces robust branch protection rules to block unauthorized code modifications:
* Direct pushes to the `main` or stable production execution branches are programmatically blocked.
* All code updates must arrive via an isolated feature branch Pull Request (PR).
* **Mandatory Peer Review:** A minimum of one senior engineer must review and explicitly approve the engineering adjustments.
* **Automated Screening Gating:** The integration pipeline executes automated security scans on every push event. If code updates contain leaked secrets, insecure configurations, or high-risk dependencies, the deployment pipeline locks automatically.

---

## 3. Automated Compliance-as-Code Pipeline Architecture

Workkas utilizes continuous automation within its GitHub Actions workflows to verify the security of the framework codebase:

### Static Application Security Testing (SAST)
* **Tooling:** Semgrep / SonarQube
* **Trigger:** Every single Pull Request execution loop.
* **Constraint:** The pipeline rejects code changes and stops compilation if it flags insecure patterns, cross-tenant authorization issues, or dangerous configuration mappings.

### Automated Dependency Analysis (Software Supply Chain Security)
* **Tooling:** Snyk / Dependabot
* **Trigger:** Nightly automated audits and PR push events.
* **Constraint:** If an active dependency reports an open vulnerability tracking score of CVSS >= 8.0, the build pipeline blocks releases until a patch or mitigation is applied.

### Automated Secrets Identification Hook
* **Tooling:** TruffleHog / GitGuardian Engine
* **Trigger:** Executed on local pre-commit parameters and remote integration runs.
* **Constraint:** Scans all configuration files, markdown docs, and scripts for leaked developer authentication keys, testing profiles, or API parameters, rejecting the commit if a match is found.

---

## 4. Container Hardening Policies
* Production container builds (including NestJS API nodes and Redis stream processors) must build using verified, minimal base distributions (Alpine / Distroless).
* Operational runtime profiles must enforce non-root execution frameworks programmatically to prevent container breakout risks.

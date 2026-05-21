# Standard Operating Procedure: Open-Source Secure SDLC Policy

**Document Reference:** SOP-SDLC-SAVV-002
**Version:** 2026.1
**Target Scope:** Savv Core Framework Maintainers & Contributors
**Enforcement Level:** Mandatory

---

## 1. Objective
To guarantee that the Savv Core codebase maintains absolute architectural integrity, ensuring that secure coding standards, framework-level guardrails, and supply-chain protections are programmatically validated across every pull request.

---

## 2. Phase-by-Phase Secure Engineering Lifecycle

[Feature Proposal] ──► [Secure Core Coding] ──► [Automated CI/CD Gates] ──► [Cryptographic Release]
### Phase 1: Planning & Architecture Review
Prior to introducing new design structures or modifying core packages (such as template processors or routing components), maintainers must evaluate the potential security implications on downstream web applications.

### Phase 2: Secure Coding Implementation
* All code additions must comply with modern PHP security standards, utilizing cryptographically secure pseudo-random number generation functions (`random_bytes()`) and strong hashing standards.
* Third-party package integrations are restricted. The framework prioritizes lightweight, verified, native solutions to minimize the dependency attack vector.

### Phase 3: Pull Request Verification (GitHub Branch Protection Rules)
The central core repository enforces robust branch protection rules to block unauthorized code modifications:
* Direct commits to the `main` or stable release branches are programmatically blocked.
* All code changes must arrive via a verified feature branch Pull Request (PR).
* **Mandatory Maintainer Approval:** A minimum of two core framework maintainers must perform architectural reviews and sign off on the changes.
* **Automated Security Gates:** The continuous integration pipeline runs automated security scans on every push event. If code changes fail automated linting, expose secret footprints, or introduce high-risk dependencies, the merge pipeline locks automatically.

---

## 3. Automated Compliance-as-Code Pipeline Architecture

Savv utilizes continuous automation within its GitHub Actions workflows to verify the security of the framework codebase:

### Static Application Security Testing (SAST)
* **Tooling:** PHPStan (Level 9 / Security Rules) / Semgrep
* **Trigger:** Every single Pull Request execution.
* **Constraint:** The pipeline rejects code changes and stops compilation if it flags insecure patterns, unvalidated variable usage, or dangerous functions.

### Automated Software Supply Chain Security
* **Tooling:** Snyk / Roave Security Advisories
* **Trigger:** Nightly automated audits and PR push events.
* **Constraint:** If an active dependency reports an open vulnerability tracking score of CVSS >= 7.5, the build pipeline blocks releases until a patch or mitigation is applied.

### Automated Secrets Identification Hook
* **Tooling:** TruffleHog Engine
* **Trigger:** Executed on commit tracking lines and integration runs.
* **Constraint:** Scans all configuration files, markdown docs, and scripts for leaked developer authentication keys, testing profiles, or API parameters, rejecting the commit if a match is found.

---

## 4. Cryptographic Artifact Hardening
* Final framework releases and distribution packages are cryptographically signed using GPG keys held exclusively by root maintainers.
* Release configurations strip all testing profiles, documentation blocks, and developmental configuration scripts to minimize the downstream distribution size and attack footprint.

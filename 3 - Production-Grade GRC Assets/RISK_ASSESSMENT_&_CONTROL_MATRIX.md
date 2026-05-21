# Corporate Information Security Risk Assessment & Controls Matrix

**Target Environment:** Cloud-Native Distributed B2B SaaS Platform (Next.js / Node.js / PostgreSQL on AWS)
**Last Reviewed:** May 2026

---

## 1. Risk Scoring Methodology

| Level | Likelihood (Probability of Occurrence) | Impact (Severity of Business Damage) |
| :--- | :--- | :--- |
| **5** | Almost Certain (Happens weekly/monthly) | Catastrophic (Business failure, massive legal fines) |
| **4** | Likely (Happens a few times a year) | Major (Severe data breach, customer churn) |
| **3** | Possible (Could happen under specific conditions)| Moderate (Temporary downtime, minor data exposure) |
| **2** | Unlikely (Rare, requires multi-system failure) | Minor (Short service disruption, low internal impact) |
| **1** | Rare (Highly improbable) | Insignificant (No operational or financial impact) |

* **Inherent Risk:** The risk level before any security controls are applied.
* **Residual Risk:** The remaining risk level *after* implementing technical mitigations.

---

## 2. Risk & Controls Register

| Risk ID | Risk Description | Inherent L | Inherent I | Inherent Score | Technical Mitigation & Controls (The Remedy) | Residual L | Residual I | Residual Score | Verified By (Automation) |
| :--- | :--- | :---: | :---: | :---: | :--- | :---: | :---: | :---: | :--- |
| **RSK-01** | **Leaked Secrets / API Keys:** Developer accidentally commits production third-party API keys or DB credentials to a public GitHub repository. | 4 | 4 | **16 (High)** | 1. Implement secret scanning hooks locally.<br>2. Use AWS Secrets Manager for runtime injection.<br>3. Strict `.gitignore` linting in CI/CD pipeline. | 1 | 4 | **4 (Low)** | `TruffleHog / GitGuardian GitHub Action` run on every Push. |
| **RSK-02** | **Broken Object Level Authorization (BOLA):** Malicious user manipulates API request IDs (e.g., `/api/user/102/data` to `/103`) to view cross-border customer records. | 4 | 5 | **20 (Critical)**| 1. Enforce a robust middleware layer inspecting JWT claims against resource ownership.<br>2. Replace sequential auto-incrementing integer database IDs with secure **UUIDv4**. | 1 | 5 | **5 (Low)** | `Postman/Bruno Automated Integration Tests` checking cross-tenant authorization barriers. |
| **RSK-03** | **Supply Chain Vulnerability:** A direct or transitive open-source NPM/Composer package dependency introduces a known remote code execution (RCE) exploit. | 4 | 4 | **16 (High)** | 1. Automated software bill-of-materials (SBOM) scanning.<br>2. Continuous blocking of builds containing dependencies with CVSS scores $\ge 8.0$. | 2 | 3 | **6 (Low)** | `Snyk / Dependabot` security gating integrated into the master branch pull request pipeline. |
| **RSK-04** | **Data Loss via Infrastructure Failure:** Primary production database suffers corruption or region-wide hosting outage, losing active customer transactions. | 3 | 5 | **15 (High)** | 1. Automated multi-AZ (Availability Zone) database replication.<br>2. Point-in-Time Recovery (PITR) enabling continuous backups retained for 30 days.<br>3. Semiannual automated disaster recovery drill. | 1 | 5 | **5 (Low)** | `AWS CloudWatch Alarms` monitoring backup success metrics and replication lag status. |

---

## 3. Continuous Compliance Enforcement Strategy

Rather than relying on periodic manual reviews, this environment treats compliance as a continuous engineering constraint. Every Pull Request triggers the automated test suite specified in the "Verified By" column. If a security control check fails, the deployment pipeline is blocked automatically, maintaining an uninterrupted state of compliance.
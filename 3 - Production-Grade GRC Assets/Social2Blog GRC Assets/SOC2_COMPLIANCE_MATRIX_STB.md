# STB Master Compliance Matrix: SOC 2 & ISO 27001 Controls Mapping

**Evaluation Context:** AI-SaaS Audit Alignment & Automated Architecture Mapping

**Operating Status:** Continuous Compliance Monitoring Active

**Target Scope:** STB Cloud Ecosystem & Automation Pipelines

---

## 1. Integrated Framework Controls Matrix

| SOC 2 Criteria | ISO 27001 Control | System Policy Description | Technical Control Design (How We Enforce It) | Real-Time Audit Evidence Configuration |
| :--- | :--- | :--- | :--- | :--- |
| **CC6.1** (Access Identity Verification) | **A.9.2.1** (User registration and de-registration) | Access to core operational architectures and pipeline orchestration tools tracks strict least privilege principles. | STB implements central directory controls. Access to production servers, databases, or n8n workflow systems requires MFA validation. | Continuous checks verification showing complete identity enforcement across all system profiles. |
| **CC6.3** (Perimeter Access Defense) | **A.13.1.1** (Network controls) | Edge routing systems process and filter incoming text traffic to catch runtime exploits and injection strings. | Cloudflare Web Application Firewall (WAF) filters traffic payloads, stripping script attributes and known parameter manipulation threats. | Live logging streams showing dropped malicious requests at the edge firewall tier. |
| **CC6.6** (Multi-Tenant Data Boundaries) | **A.14.1.1** (Information security requirements analysis and specification) | Text data arrays and high-speed semantic index records maintain complete segregation between platform accounts. | STB configures cryptographic namespace separation rules inside the vector database tier, filtering lookups by validated organizational tokens. | Cloud system checks verifying complete tenant segregation inside vector databases. |
| **CC7.1** (Vulnerability Patch Tracking) | **A.12.6.1** (Management of technical vulnerabilities) | Repositories, microservices, and parsing scripts undergo continuous automated vulnerability analysis. | Automated SAST (Semgrep) and package dependency evaluation (Snyk) checks run inside GitHub Actions on every code commit. | Automated integration metrics recording deployment blocks when dependencies present known unpatched flaws. |
| **CC8.1** (System Configuration Management) | **A.12.1.2** (Change management) | Every production release or automation configuration update requires staging validation and peer verification. | Source control management settings programmatically block unreviewed pull requests, requiring successful automated runs and engineering approval. | Repository histories capturing the linkage between verified user approvals and production system deployments. |

---

## 2. Continuous Controls Monitoring (CCM) Operations

STB configures system parameters directly into automated compliance tracking architectures. Rather than waiting for periodic manual system checks, the compliance engine automatically performs continuous audits of security boundaries, storage parameters, and encryption rules. If a configuration drifts out of policy compliance, the system triggers real-time alerts to the security squad, ensuring rapid remediation to maintain data protection baselines.

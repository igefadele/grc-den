# Workkas Master Compliance Matrix: SOC 2 & ISO 27001 Controls Mapping

**Evaluation Context:** International Talent Platform Audit Alignment & Architecture Mapping
**Operating Status:** Continuous Compliance Monitoring Active
**Target Scope:** Global Workkas Cloud Ecosystem

---

## 1. Integrated Framework Controls Matrix

| SOC 2 Criteria | ISO 27001 Control | System Policy Description | Technical Control Design (How We Enforce It) | Real-Time Audit Evidence Configuration |
| :--- | :--- | :--- | :--- | :--- |
| **CC6.1** (Access Identity Verification) | **A.9.2.1** (User registration and de-registration) | Access to backend servers, payment systems, and sensitive user identification data matches strict least privilege definitions. | Workkas enforces centralized user directories. Access to administrative systems and cloud management dashboards requires multi-factor authentication. | Automated reports verifying complete MFA enforcement across all core team members. |
| **CC6.3** (Perimeter Access Defense) | **A.13.1.1** (Network controls) | Public entry vectors are monitored and filtered at the network edge to block exploitation strategies. | Cloudflare Web Application Firewall (WAF) rule layers drop unauthorized request arrays and drop common web threats before processing. | Real-time tracking streams tracking edge firewall block indicators and inbound request profiles. |
| **CC6.6** (Data Transmission Safety) | **A.10.1.1** (Policy on the use of cryptographic controls) | Highly confidential contractor verification assets and passport files use advanced encryption models at rest. | Uploaded documents use application-layer envelope encryption via Cloud KMS before being written to encrypted AWS S3 buckets. | Cloud configuration checks verifying complete storage encryption across all active asset repositories. |
| **CC7.1** (Vulnerability Screening) | **A.12.6.1** (Management of technical vulnerabilities) | Repositories and application code components undergo continuous automated scanning for dependencies and code flaws. | Automated SAST (Semgrep) and package dependency tracking (Snyk) checks run inside GitHub Actions on every code commit. | Automated integration metrics recording deployment blocks when dependencies present known unpatched flaws. |
| **CC8.1** (System Configuration Management) | **A.12.1.2** (Change management) | Changes affecting production architecture must clear staging verification and win peer approval. | Source code management rules programmatically block unreviewed commits. Code merges require passing tests and senior engineer validation. | GitHub Actions logs capturing full execution records linking pull request approvals to production releases. |

---

## 2. Continuous Controls Monitoring (CCM) Operations

Workkas incorporates an automated GRC monitoring model that continuously evaluates production controls. Rather than executing simple manual point-in-time reviews, the security infrastructure performs real-time checks across active security settings, access configurations, encryption parameters, and system behaviors. Any configuration drift or out-of-bounds parameter change triggers high-priority security notifications to ensure swift remediation and maintain platform data safety rules.

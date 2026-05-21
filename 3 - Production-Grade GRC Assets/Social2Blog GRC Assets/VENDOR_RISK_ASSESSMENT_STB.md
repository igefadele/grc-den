# STB Vendor Risk Assessment Questionnaire & Scorecard

**Target Vendor Entity:** [Insert Third-Party Vendor Name]  
**Functional System Scope:** [e.g., LLM Model API Provider, Vector Database Vendor]  
**Reviewing Coordinator:** STB Technical GRC Unit  
**Status Assignment:** Pending Technical Evaluation  

---

## 1. Architectural Security Questionnaire

### Section A: Governance & Security Framework Alignment
* **Q1:** Do you possess a validated, third-party audited **SOC 2 Type II** or **ISO/IEC 27001** certification? (If yes, please attach current certification documentation covering active operating periods).
* **Q2:** Do you execute annual independent network penetration testing assessments? Provide the executive summary and remediation summaries from your most recent assessment.

### Section B: Data Protection & Infrastructure Hardening
* **Q3:** Detail your technical standards for data encryption. Explain your procedures for safeguarding customer profiles at rest and handling payload delivery over transit pathways.
* **Q4:** How do you guarantee secure data separation across multi-tenant cloud storage structures to block cross-tenant exposure anomalies?

### Section C: AI Governance & Data Safeguards
* **Q5:** Do you enforce a Zero-Data-Retention (ZDR) policy for payloads processed via your API endpoints? Confirm whether customer inputs are utilized for model optimization or training routines.
* **Q6:** Outline your infrastructure monitoring safeguards to intercept prompt injection vulnerabilities and prevent data leakage within your system environments.

---

## 2. Technical Evaluation Scorecard

Evaluate vendor feedback across target controls, applying numeric score designations:
* **5 points:** Complete automated control validation matching enterprise safety rules.
* **3 points:** Partial compliance or manual policy alignment lacking real-time automated enforcement.
* **0 points:** Missing control structure, creating system risks.

| Evaluation Category | Target Compliance Requirement | Max Score | Vendor Score | Notes / Gaps Found |
| :--- | :--- | :--- | :--- | :--- |
| **Framework Maturity** | Validated SOC 2 Type II / ISO certification covering scope. | 5 | | |
| **AI Data Protection** | Explicit Zero-Data-Retention contract for API data inputs. | 5 | | |
| **Cryptographic Standards** | Enforces AES-256 storage encryption and TLS 1.3 pipelines. | 5 | | |
| **Access Control Controls** | Enforces mandatory user MFA across operational environments. | 5 | | |
| **Supply Chain Security** | Executes automated vulnerability patching schedules. | 5 | | |
| **Total Evaluation** | Summary Matrix Performance Index | **25** | | |

---

## 3. Decision Matrix & Sign-off Boundaries

* **Score 21 - 25:** **Approved.** Low risk profile; vendor clears system security benchmarks.
* **Score 15 - 20:** **Conditional Approval.** Medium risk profile; requires specific legal safeguards and periodic manual compliance logging.
* **Score Below 15:** **Rejected.** High risk profile; vendor architecture fails data safety requirements.

**Reviewing GRC Engineer Signature:** ___________________________ Date: ____________

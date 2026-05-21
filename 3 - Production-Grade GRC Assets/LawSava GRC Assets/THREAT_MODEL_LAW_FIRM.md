# Product Threat Model & Data Flow Analysis: LawSava Core Engine

**Target Environment:** Secure Legal Practice Management Platform (Case, Hearing, Document, & Invoice Systems)
**Architecture Baseline:** Multi-Tenant Laravel Core, Isolated AWS S3 Encrypted Storage, Dedicated PostgreSQL Row-Level Isolation
**Classification:** Confidential Internal Security Documentation

---

## 1. Core Data Flow Diagram (DFD) Mapping

The following pipeline describes the lifecycle of an uploaded legal document or case note through the infrastructure layers:

[Lawyer / Client Browser]
│ (HTTPS TLS 1.3 Request via Authenticated Session)
▼
[Cloudflare WAF / Advanced Edge Protective Layer]
│ (Malicious Payload Drops / OWASP Top 10 Filtering)
▼
[Laravel Application Nodes] ───► [n8n Automation Engine (AI Document Content Processing)]
│
├─► [KMS Key Vault Engine] (Just-In-Time Application-Layer Envelope Encryption)
├─► [AWS S3 Protected Bucket] (Encrypted At Rest via AES-256, Protected by Object Lock)
▼
[PostgreSQL Database Engine] (Row-Level Security Enforced via Explicit Firm Org ID Context)


---

## 2. Threat Analysis & Programmatic Countermeasures (STRIDE Mapping)

### Spoofing Identity
* **Threat:** An external malicious actor spoofs the session of a lawyer or judicial officer to access private litigation discovery documents.
* **Technical Control:** Enforce mandatory context-aware Multi-Factor Authentication (MFA). Sessions are bound to hardware keys or application tokens. Application middlewares terminate sessions automatically upon detecting simultaneous geographic velocity shifts (e.g., logging in from two distant regions within an hour).

### Tampering with Data
* **Threat:** An adversary intercepts and alters a billing invoice PDF file or bank routing details on a trust payment gateway to divert escrow balances.
* **Technical Control:** Every generated legal invoice generates an immutable SHA-256 cryptographic hash value at production run. Before any payment transaction processes, the system cross-validates the invoice's live hash against the database baseline record. Any variance locks the payment execution loop and triggers a critical security event.

### Repudiation
* **Threat:** A user modifies or deletes a critical case event, court hearing deadline, or client trust ledger record and claims the action never occurred.
* **Technical Control:** LawSava records all actions to an append-only, centralized logging architecture. Audit entries are written to an isolated, immutable storage bucket configured with Write-Once-Read-Many (WORM) compliance boundaries that prevent log modification even by corporate administrative accounts.

### Information Disclosure
* **Threat:** Cross-Tenant Case Leakage. A lawyer from "Firm A" alters an active integer URL parameter (`/cases/view/5001` to `5002`) and successfully reads private case strategy and evidence belonging to competitive "Firm B".
* **Technical Control:** Complete deprecation of all predictable sequential auto-incrementing integer identifiers across public-facing APIs. Enforce unique **UUIDv4 parameters** globally. Enforce native PostgreSQL Row-Level Security (RLS) constraints that dynamically intercept database interactions to ensure records are strictly filtered by the verified organization ID context found in the user's active JWT claims.

### Denial of Service
* **Threat:** Opposing malicious forces or botnets target a specific firm's public portal during a high-profile litigation window, making case data inaccessible during a trial.
* **Technical Control:** Implement advanced rate-limiting at the Cloudflare edge layer. Integrate Redis token bucket algorithms at the Laravel routing tier to restrict API consumption rates, ensuring resource availability during high-volume spikes.

### Elevation of Privilege
* **Threat:** A low-level firm paralegal or external client portal user modifies request attributes to gain access to corporate administrative settings or other firms' client data.
* **Technical Control:** Programmatic verification of explicit permission schemas utilizing a strict Role-Based Access Control (RBAC) model. Access vectors verify functional rights on every single request lifecycle before processing.

---

## 3. Vulnerability Remediation Validation

All vulnerabilities identified during routine system evaluations or code repository scans are tracked through a rigorous verification cycle:
1. **Triaging:** The technical compliance team verifies the vulnerability in an isolated staging instance.
2. **Mitigation:** Development teams implement structural architectural fixes (such as escaping parameters to eliminate injection vectors).
3. **Automated Testing:** Regression and unit tests execute via automated pipeline filters to confirm the issue is resolved.
4. **Validation Sign-off:** The GRC engineer logs the validation evidence within the continuous compliance index before archiving the ticket.

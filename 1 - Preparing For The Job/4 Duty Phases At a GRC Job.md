# 4 Duty Phases At A GRC Job

As a Technical GRC Analyst / Information Security Engineer, your job bridges the gap between high-level company strategy and technical code execution. You are the translation layer ensuring that developers, cloud engineers, and product teams build systems that are secure and compliant by design.

To master this role, think of your responsibilities not as a static list of tasks, but as a continuous cycle divided into four repeating operational phases.

## Phase 1: Governance & Alignment (The Policy Blueprint)
This is where the rules are established. Your primary responsibility is translating massive compliance frameworks (like ISO 27001, SOC 2, or NIST) into practical engineering standards that developer teams can follow.

### Day-to-Day Tasks & Deliverables:

#### Drafting and Updating SOPs: 
You write and maintain clear Standard Operating Procedures (SOPs). Instead of a vague policy saying "We protect data," you write the specific technical standard: "All production databases must utilize AES-256 encryption at rest, and all API interactions must force TLS 1.3."

#### Asset Management Mapping: 
Ensuring the company has a verified, real-time inventory of all tech assets—from AWS S3 buckets to external APIs and internal code repositories. You cannot protect what you don't track.

#### Security Training Alignment: 
Designing training paths for the engineering team regarding secure coding practices (like mitigating the OWASP Top 10 vulnerabilities).


## Phase 2: Risk Identification & Treatment (The Assessment)
In this phase, you actively look for gaps between your active engineering infrastructure and your compliance policies.

### Day-to-Day Tasks & Deliverables:

#### Product Security Assessments: 
Before a software engineer pushes a massive structural update to production, you review the architecture. You inspect how access is authorized, how logs are handled, and how third-party APIs are integrated.

#### Qualitative & Quantitative Risk Modeling: 
Running risk assessments. You identify threats (such as data exposure, credential leaks, or dependency vulnerabilities), calculate their score, and establish the formal "Risk Treatment" strategy:

* **Mitigate:** Implement a technical control to fix it.

* **Accept:** Acknowledge a low risk if the fix impedes vital business operations and has minor impact.

* **Transfer:** Buy cyber insurance or offload the processing to a compliant vendor.

#### Third-Party Vendor Risk Management (TPRM): 
Evaluating the security posture of any new service provider the development team wants to integrate into the core app.



## Phase 3: Technical Control Implementation & Automation (The Execution)
This is where your software engineering background turns into an elite asset. Instead of using manual spreadsheets, you use code and engineering pipelines to continuously enforce compliance.

### Day-to-Day Tasks & Deliverables:

#### Enforcing Access Control & Identity Management (IAM): 
Auditing permissions across cloud providers and databases. You implement Role-Based Access Control (RBAC) and verify the Principle of Least Privilege so that employees only access the specific assets required to perform their daily duties.

#### Building Compliance-as-Code Pipelines: 
Setting up automated tools within your deployment workflows. For example, integrating secret scanners (like TruffleHog) and static code analyzers (like Snyk) directly into GitHub Actions. If a developer accidentally leaves an API key in the source code, your automated control blocks the build instantly.

#### Configuring GenAI & Workflow Guardrails: 
Reviewing automation pipelines (like n8n or internal LLM integrations) to ensure sensitive customer or company data is sanitized, logs are securely recorded, and prompt-injection vectors are mitigated.

## Phase 4: Audit Management & Continuous Monitoring (The Verification)
Compliance is not a one-time event. This phase focuses on proving to internal stakeholders and external, independent auditors that your security controls are actively operating over time.

### Day-to-Day Tasks & Deliverables:

#### Continuous Controls Monitoring (CCM): 
Utilizing modern GRC automation platforms (such as Vanta, Drata, or custom logging indices via cloud monitoring tools) to dynamically track control performance and instantly alert the security team of any compliance drift.

#### Evidence Collection & Log Auditing: 
Reviewing authentication logs, database backup histories, and change management records. You organize these items systematically so that when an official external audit (like a SOC 2 Type II assessment) occurs, the evidence is immediately accessible.

#### Remediation Tracking: 
If an internal scan or an external audit uncovers an active vulnerability or a control exception, you log it, assign a technical owner to fix it, and verify the patch before closing out the issue.
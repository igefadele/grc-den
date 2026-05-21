# Architectural Blueprint: Centralized Immutable Logging Infrastructure

**Document Reference:** ARCH-LOG-004  
**Framework Alignment:** SOC 2 CC7.2, ISO 27001 Control A.12.4  
**Data Category:** Append-Only System Audit Trails  

---

## 1. Stream Delivery & Aggregation Model

To prevent malicious system administrators or external attackers from altering trace records following an incident, Workkas runs an append-only log collection pipeline.

[NestJS Compute Nodes] ────► [CloudWatch Transit Log Stream]
│
[Redis Queue Processors] ──►             ▼
[Centralized Aggregation Hub]
│
▼
[Immutable WORM S3 Storage]
(Object Lock Compliance Enabled)


### Log Transit Requirements
* Core microservice nodes, routing gateways, and queue workers forward operational transaction summaries via encrypted system hooks to a central monitoring node.
* System events use standard log signatures containing precise timestamps, caller contexts, tracking keys, and result codes.

### Storage Immutability Controls
* Consolidated log indexes are committed directly into an isolated cloud storage repository configured with Write-Once-Read-Many (WORM) compliance protection profiles.
* The system configuration prevents modification or truncation of records for a mandatory retention span of **365 days**, preventing deletion commands even from root account users.

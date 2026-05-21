# System Infrastructure & Application Topology Manual

**Document Reference:** TECH-TOPO-001  
**Operating State:** Multi-Region Production Baseline  
**Environment Sync:** Cloud-Native Cluster Configurations  

---

## 1. Network Perimeter & Cluster Interconnectivity Matrix

Workkas uses a tier-isolated architecture where microservices are segregated into specific network subnets inside a virtual private cloud (VPC):

                   [Public Internet Traffic]
                              │
                              ▼
                [Cloudflare Edge Protection]
                              │
                              ▼
                 [VPC Boundary Perimeter]
                              │
     ┌────────────────────────┴────────────────────────┐
     ▼                                                 ▼
[Public Web Subnet]                              [Isolated Ingress Gateway]
(Static Landing Assets)                          (Load Balancing Arrays)
│
▼
[Private Compute Subnet]
(NestJS API Cluster Nodes)
(Redis Stream Queues)
│
▼
[Isolated Data Subnet]
(PostgreSQL Master DB)
(AWS S3 Document Vault)


---

## 2. Component Subnet Security Controls

### Public Web Subnet
* Holds static marketing assets and public platform elements.
* Open to public traffic channels, passing inputs through edge firewall filtering rules.

### Private Compute Subnet
* Runs core NestJS API components and parallel Redis scheduling queues.
* Banned from receiving direct connections from the public internet. Communication passes exclusively via authorized load-balancing gateways.

### Isolated Data Subnet
* Holds database nodes and secure cloud object storage instances.
* Access rules block all external parameters. Query inputs must arrive via authenticated application-layer microservices passing through verified database routing parameters.

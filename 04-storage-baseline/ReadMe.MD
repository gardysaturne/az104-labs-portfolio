# AZ-104 – Week 4: Implement & Manage Storage  
## Global Remote-First Storage Baseline (US East + West DR + EU Read Scenario)

---

# Executive Summary

Week 4 focuses on designing and validating a production-ready Azure Storage baseline for a global remote-first organization.

This is not a “create a storage account” lab.

This week addresses precision gaps in:

- Access tier decision logic (Hot vs Cool vs Cold vs Archive)
- Replication behavior (LRS, GRS, RA-GRS, GZRS vs Object Replication)
- Lifecycle policy boundaries
- Naming constraints and operational discipline
- Pricing mechanics and billing triggers
- Storage account type strategy (Standard vs Premium)

The objective was to move from conceptual understanding to **exam-grade precision and architect-level clarity**.

---

# Architecture Context

Platform Scenario:

- Primary Region: East US
- Disaster Recovery: West US
- EU Media Read Scenario
- Mixed workloads:
  - Media (frequent reads)
  - Logs (aging + compliance)
  - Legal archive (long retention)
  - High-performance workloads (Premium candidate)

This week reinforces the storage dimension of the broader Azure Spine platform:

- Identity → Entra ID + RBAC
- Authorization → Scoped role assignments
- Security baseline → Encryption + secure transfer
- Cost governance → Tier selection + lifecycle
- Replication strategy → Durability vs distribution
- Operational readiness → Monitoring + validation evidence

---

# Exercises Overview

## EX01 – Access Tier Ladder (Cost + Retention + Latency)

Validated:

- Hot = highest storage cost, lowest access cost  
- Cool = 30-day minimum retention  
- Cold = 90-day minimum retention  
- Archive = 180-day minimum retention + rehydration required  

Key insight:

Cooler tiers reduce storage cost but increase access and transaction cost.  
Archive cannot be read directly and introduces rehydration latency.

This exercise corrected default “performance-first” bias and enforced cost-pattern modeling.

---

## EX02 – Replication Strategy vs Object Replication

Validated precise differences:

### Redundancy Models
- LRS – single datacenter
- ZRS – 3 availability zones
- GRS – secondary region (read after failover)
- RA-GRS – read secondary anytime
- GZRS – zones + geo
- RA-GZRS – zones + geo + read access

### Object Replication
- Requires versioning enabled
- Asynchronous
- Replicates content + metadata + versions
- Does NOT replicate snapshots

Key insight:

Geo-redundancy provides durability and failover.  
Object replication provides controlled distribution at container scope.

They solve different problems.

---

## EX03 – Lifecycle Policy Mechanics

Implemented IF(days) → THEN(action) automation.

Allowed actions:
- Move to Cool
- Move to Cold
- Move to Archive
- Delete

Clarified lifecycle boundaries:

Lifecycle does NOT:
- Change blob type
- Replicate data
- Override legal hold
- Modify container structure

This prevents scope confusion under exam pressure.

---

## EX04 – Naming & Limits Discipline

Enforced container rules:

- 3–63 characters
- Lowercase only
- Numbers allowed
- Hyphens allowed
- Must begin with letter or number

Captured error messages for invalid cases to reinforce operational discipline.

Naming is not cosmetic — it directly impacts automation, CI/CD, and governance policy enforcement.

---

## EX05 – Pricing & Billing Mechanics

Clarified cost drivers:

Cost depends on:
- Volume stored
- Operations (transactions)
- Redundancy option

Tier transition charges:
- Cool → Hot = read charge
- Hot → Cool = write charge

Key insight:

Cooler tiers are cheaper for storage but more expensive for usage.  
Billing spikes often occur during tier transitions — not from storage growth alone.

This exercise strengthened cost-governance reasoning.

---

## EX06 – Storage Account Type Strategy

Validated:

- Standard = HDD
- Premium = SSD
- Cannot convert between them
- Premium supports:
  - Premium block blobs
  - Premium file shares
  - Premium page blobs

Key insight:

Account type selection is a design-time decision.  
Choosing incorrectly results in migration, not configuration change.

---

# Identity & Access Model (Spine Alignment)

All exercises used:

- Authentication: Microsoft Entra ID
- Authorization: Azure RBAC (least privilege at RG or subscription scope)
- No Shared Key reliance (maturity milestone)
- Activity Log validation for audit evidence

This reinforced separation of:

- Identity
- Authorization
- Token delegation (SAS)
- Account-level secrets

Architectural clarity improved significantly this week.

---

# Security Baseline

Across exercises:

- Secure transfer required
- Encryption at rest (PMK default)
- Versioning enabled where required
- Public access disabled unless explicitly required

Security maturity focus areas:

- Understanding CMK regional dependency
- Recognizing infrastructure encryption (double encryption)
- Understanding SAS clock skew implications

---

# Cost Governance Controls

Implemented:

- Tier selection based on workload pattern
- Lifecycle automation to reduce manual operations
- Explicit documentation of redundancy cost impact
- Clear understanding of transaction-based billing

Storage cost is not just GB/month — it is behavior-based billing.

---

# Operations & Monitoring

Operational risks identified:

- Rehydration latency impacting SLAs
- Incorrect lifecycle thresholds deleting data prematurely
- Object replication misconfiguration (versioning disabled)
- Tier transitions triggering unexpected charges

Monitoring sources:

- Azure Monitor metrics (transactions)
- Activity Log (configuration changes)
- Replication policy status

Every exercise includes:

- Before state
- Configuration blade
- After state
- Audit evidence

Proof, not assumptions.

---

# Risk & Tradeoff Summary

| Area | Risk | Tradeoff |
|------|------|----------|
| Archive Tier | Latency during rehydration | Lower storage cost |
| RA-GRS | Higher cost | Readable secondary region |
| Premium Account | Higher baseline cost | Predictable low latency |
| Cool Tier | High transaction charges | Reduced storage cost |

Director-level storage design is always balancing:

Cost  
Durability  
Performance  
Latency  
Operational overhead  

---

# Interview Readiness

After Week 4, I can clearly explain:

- Hot vs Cool vs Cold vs Archive including minimum retention and latency
- GRS vs RA-GRS vs GZRS vs RA-GZRS
- Object replication vs geo-replication
- What lifecycle management cannot do
- Why cost spikes after tier transitions
- When Premium is required and why it cannot be converted later

---

# Week 4 Outcome

This week corrected:

- Dimensional confusion (account vs tier vs redundancy)
- Replication imprecision
- Pricing mechanics gaps
- Naming and numeric recall weaknesses

The result is not just exam readiness.

It is platform-level storage design thinking aligned with the broader Azure Spine.

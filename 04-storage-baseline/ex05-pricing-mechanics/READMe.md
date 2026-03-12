# EX05 — Pricing Mechanics (Cooler ≠ Cheaper)

## Purpose

The purpose of this lab was to understand how Azure Storage pricing actually works in practice. A common mistake in cloud architecture is assuming that colder storage tiers automatically reduce cost. In reality, Azure storage pricing is influenced by multiple factors including storage volume, transaction operations, redundancy configuration, and lifecycle policies.

This exercise focuses on thinking like an infrastructure engineer by designing storage configurations that balance **cost, durability, and access patterns**.

---

## Storage Account Configuration

**Storage Account:** stex03lifecycle01  

| Setting | Value |
|---|---|
Subscription | SMG-Lab |
Resource Group | rg-lab-storage |
Region | UK South |
Performance | Standard |
Redundancy | Locally Redundant Storage (LRS) |
Account Type | StorageV2 (General Purpose v2) |

LRS was selected for this lab to keep costs low while still simulating a realistic enterprise storage configuration.

LRS maintains **three copies of the data within a single datacenter**, protecting against hardware failure while minimizing storage cost.

---

## Redundancy Design

The storage account uses **Locally Redundant Storage (LRS)**.

This option was chosen because:

- It is the **lowest cost replication option**
- Suitable for **lab environments or non-critical data**
- Provides **basic durability with three replicated copies**

In production environments, redundancy options such as **ZRS or GRS** may be required depending on disaster recovery requirements.

---

## Lifecycle Management

Lifecycle rules were implemented to automatically manage data aging and reduce long-term storage cost.

| Rule | Action |
|---|---|
move-to-cool-30-days | Move blobs to Cool tier after 30 days |
move-to-archive-90-days | Move blobs to Archive tier after 90 days |
delete-after-180-days | Delete blobs after 180 days |

These policies simulate a typical enterprise storage lifecycle.

Hot → Cool → Archive → Delete

Hot tier stores frequently accessed data, while older data transitions to cheaper storage tiers. Data that is no longer required is automatically deleted after 180 days.

---

## Outcome

This lab demonstrates how Azure storage cost is influenced by:

- Storage volume
- Transaction operations
- Redundancy configuration
- Data lifecycle policies

By implementing lifecycle automation and selecting appropriate storage tiers, organizations can significantly reduce long-term storage costs while maintaining data durability.

---

## Key Takeaways

- Cooler storage tiers are **not automatically cheaper** if data is frequently accessed.
- Storage redundancy levels directly affect overall cost.
- Lifecycle policies help **automatically optimize storage usage over time**.
- Proper storage design requires understanding **access patterns and retention requirements**, not just selecting the lowest storage tier.

This exercise reinforces the importance of designing **cost-aware and scalable storage architectures in Azure**.

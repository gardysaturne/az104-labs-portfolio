# EX03 — Lifecycle Boundaries

## Purpose

This exercise demonstrates how **Azure Blob Storage Lifecycle Management** can automate data tiering and deletion policies. The goal is to understand both how lifecycle rules work and the boundaries of what they can and cannot control.

In large cloud environments, storage accounts often accumulate large volumes of data such as application logs, images, backups, and exported reports. Lifecycle management helps control storage costs by automatically moving older data to cheaper storage tiers and eventually deleting it when it is no longer required.

---

## Lab Resources

**Resource Group**

- `rg-lab-storage`

**Storage Accounts**

- `stex03lifecycle01`
- `stlablifecycleuks01`

**Container**

- `lifecycle-boundaries`

**Test Blobs Uploaded**

- `archive-candidate-001.txt`
- `img-001.txt`
- `logs-001.txt`

These files simulate different types of application data that might exist in a real environment.

---

## Lifecycle Rules Configured

Three lifecycle management rules were created for the storage account.

| Rule | Condition | Action |
|-----|-----|-----|
| move-to-cool-30-days | Blob last modified > 30 days | Move to Cool tier |
| move-to-archive-90-days | Blob last modified > 90 days | Move to Archive tier |
| delete-after-180-days | Blob last modified > 180 days | Delete blob |

This creates a lifecycle pipeline for aging data:
Hot Tier
↓ 30 Days
Cool Tier
↓ 90 Days
Archive Tier
↓ 180 Days
Delete


---

## Validation

After uploading the blobs, the access tier remained **Hot (Inferred)**.

This is expected because the lifecycle conditions have not yet been met. The blobs were created during the lab and therefore have an age of **0 days**.

Lifecycle management evaluates rules in the background and only applies actions once the configured conditions are satisfied.

---

## Lifecycle Boundaries (What It Cannot Do)

This exercise also highlights the limitations of lifecycle management.

Lifecycle rules **can**:

- Move blobs between storage tiers
- Delete blobs after a retention period
- Apply conditions based on blob metadata
- Target containers or blob prefixes

Lifecycle rules **cannot**:

- Replicate data between storage accounts
- Modify container structures
- Change blob types
- Override legal hold or immutability policies
- Replace backup or disaster recovery strategies

Lifecycle management is primarily used for **automated storage cost optimization and data lifecycle governance**.

---

## Real-World Use Case

In global cloud environments, lifecycle policies are commonly used for managing application logs and operational data.

For example:

- Application logs remain in **Hot storage** for 30 days while they are actively analyzed.
- After 30 days, logs move to the **Cool tier** because they are rarely accessed.
- After 90 days, logs move to **Archive storage** for long-term retention.
- After 180 days, the logs are automatically deleted.

This allows organizations to maintain required retention periods while keeping storage costs predictable and controlled.

---

## Key Takeaways

- Lifecycle management automates **data aging and storage tier optimization**
- Rules operate using **time-based conditions**
- Lifecycle policies run as **background evaluations**, not immediate actions
- Engineers must design lifecycle policies carefully to avoid unintended data deletion


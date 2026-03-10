# AZ-104 – Week 4: Implement & Manage Storage
## Azure Blob Object Replication Lab

---

# Executive Summary

This lab validates **Azure Blob Object Replication** between two storage accounts and demonstrates how **blob versioning interacts with replication events**.

The objective was to confirm that blob updates in a **source storage account** generate replicated versions in a **destination storage account** using an **Object Replication Policy**.

This lab verifies:

- Container-to-container replication
- Blob overwrite replication behavior
- Version creation mechanics
- Asynchronous replication events

---

# Architecture

Source Storage Account  
stex02srcuks01  
Container: data  

│  
│ Object Replication Policy  
│  

Destination Storage Account  
stex02dstuks01  
Container: data  

Key characteristics:

- Replication is **asynchronous**
- Replication occurs **container → container**
- Blob versioning must be **enabled**
- Blob updates are replicated automatically
- **Blob deletions are not replicated**

---

# Storage Accounts

## Source Storage Account

Name: `stex02srcuks01`

Configuration:

- StorageV2 (General Purpose v2)
- Replication: LRS
- Blob Versioning: Enabled
- Change Feed: Enabled
- Blob Soft Delete: Enabled
- Container Soft Delete: Enabled

Containers:

- `$logs`
- `$blobchangefeed`
- `data`

---

## Destination Storage Account

Name: `stex02dstuks01`

Configuration:

- StorageV2 (General Purpose v2)
- Replication: LRS
- Blob Versioning: Enabled
- Blob Soft Delete: Enabled
- Container Soft Delete: Enabled

Containers:

- `$logs`
- `data`

---

# Object Replication Configuration

Replication Policy configured on:

Source Account: `stex02srcuks01`

Replication Mapping:

data → data

Policy characteristics:

- One-way replication
- Container-level mapping
- No prefix filters
- Asynchronous replication

---

# Replication Validation

Test blob created:

replication-test-v1.txt

Initial content:

Azure Object Replication Test  
Version 1

The file was uploaded to the **source container**, which automatically replicated the blob to the **destination container**.

---

# Version Replication Test

The blob was downloaded, edited, and re-uploaded to force a version update.

Updated content:

Azure Object Replication Test  
Version 2

Overwrite process triggered the following sequence:

Blob Write  
↓  
Blob Version Created  
↓  
Replication Event Triggered  
↓  
Version Replicated to Destination Storage Account  

The destination storage account shows **multiple blob versions**, confirming successful replication.

---

# Key Concepts Demonstrated

- Azure Blob Versioning
- Azure Object Replication
- Asynchronous Storage Replication
- Container-level replication policies
- Replication-based data protection

---

# Lab Completion

✔ Storage accounts created  
✔ Blob versioning enabled  
✔ Object replication policy configured  
✔ Container replication validated  
✔ Blob overwrite replication confirmed  
✔ Version replication verified

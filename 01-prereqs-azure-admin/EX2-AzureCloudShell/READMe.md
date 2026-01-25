
## Exercise 2 — Azure Cloud Shell: Admin-from-Anywhere Scenario

**Goal:**  
Demonstrate browser-based, identity-aware Azure administration using Azure Cloud Shell, simulating a real-world remote or on-call operations scenario.

---

## Scenario (Real-World Context)

A global operations team supports workloads across multiple regions. During an on-call incident, an administrator must quickly validate Azure resources from a non-corporate device without access to pre-installed tooling or a trusted workstation.

Azure Cloud Shell provides secure, audited access to Azure using identity-based authentication, enabling rapid response without local setup.

---

## What I Did

Using **Azure Cloud Shell (PowerShell mode)**, I:

- Launched Cloud Shell directly from the Azure Portal
- Verified the active subscription and tenant context (`Get-AzContext`)
- Confirmed CloudDrive persistence across sessions
- Uploaded and executed a PowerShell script from Cloud Shell
- Enumerated Azure resources without using a local workstation
- Validated identity-scoped access and RBAC enforcement

All actions were performed entirely within the browser.

---

## Evidence (Screenshots)

This folder contains screenshots demonstrating:

- Cloud Shell startup from the Azure Portal
- Verified subscription and tenant context
- Persisted files stored in CloudDrive
- Script execution returning Azure resource data

---

## Why Cloud Shell Matters

Azure Cloud Shell is designed for:

- Incident response
- On-call troubleshooting
- Emergency access scenarios
- Secure admin access from untrusted devices

It removes dependency on local tooling while enforcing Azure identity, RBAC, and logging.

---

## Admin Takeaway

Cloud Shell is **not** a daily development environment.

It is an **admin-grade, identity-aware control plane** designed for rapid response, validation, and operational continuity when traditional access paths are unavailable.


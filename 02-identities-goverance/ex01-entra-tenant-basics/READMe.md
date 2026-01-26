## Exercise 1 — Entra Tenant & Subscription Association  
*(Identity Boundary)*

### Purpose

This exercise establishes a foundational Azure identity concept: **the Microsoft Entra tenant is the security and identity boundary**, not the subscription.

You validate how subscriptions are associated with a single Entra tenant and how that relationship impacts **access control, governance, and organizational design** in Azure.

---

### Scenario

A **10,000-user global organization** operates with:
- **One Microsoft Entra tenant** for all regions (Americas, EMEA, APAC)
- **Multiple Azure subscriptions** for environment separation (prod/dev) and cost management

Your task is to verify and document this identity-to-subscription relationship using the Azure Portal.

---

### What This Exercise Demonstrates

- How **Microsoft Entra ID** functions as the identity control plane for Azure
- Why an Azure subscription is **tied to exactly one Entra tenant**
- How identity boundaries influence **RBAC scope, governance, and access inheritance**
- How to visually **validate tenant and subscription relationships** in the Azure Portal

---

### Actions Performed (Azure Portal)

- Review **Microsoft Entra ID tenant overview** (tenant name and tenant ID)
- Confirm **subscription directory association**
- Inspect **resource group structure and naming conventions** for governance readiness

---

### Evidence Captured

- Microsoft Entra ID **Overview** page  
- **Subscriptions** page showing directory (tenant) association  
- **Resource Groups** list demonstrating governance-friendly naming  

All screenshots are stored to support **auditing, interviews, and consulting walkthroughs**.

---


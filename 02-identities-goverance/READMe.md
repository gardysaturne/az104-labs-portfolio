## Purpose

This lab series focuses on **identity and governance operations in Azure**, aligned to **AZ-104** and modeled after how a **10,000-user global organization** manages access, security, and compliance at scale.

Rather than isolated commands, these exercises emphasize **real-world administrative decision-making**, including scope selection, least-privilege access, auditing, and policy enforcement across regions.

---

## What This Lab Demonstrates

Each exercise is designed to reinforce how **Azure identity and governance actually work in production**:

- How **Microsoft Entra ID** acts as the identity control plane for users, groups, and access  
- How **Azure RBAC** is applied using **least-privilege principles** across scopes  
- How **Azure Policy and initiatives** enforce organizational standards at scale  
- How administrators **audit, validate, and govern changes** in a distributed environment  

All work is performed using the **Azure Portal (PWA)** with supporting documentation and screenshots suitable for **audits, interviews, and consulting walkthroughs**.

---

## Labs Overview

- **EX1 – Entra ID Tenant & Subscription Context**  
  Validate tenant-to-subscription relationships and understand **identity boundaries** in Azure.

- **EX2 – Users & Groups for Global Operations**  
  Create and manage **Entra ID users and security groups** to model regional IT operations (Americas, EMEA, APAC).

- **EX3 – Azure RBAC & Least Privilege Access**  
  Assign **built-in roles** at the correct scope to enforce controlled access to Azure resources.

- **EX4 – RBAC Auditing & Activity Logs**  
  Track and validate **role assignment changes** using Azure Activity Logs for governance and compliance.

- **EX5 – Azure Policy & Governance Initiatives**  
  Deploy and assign **policy initiatives** to enforce location restrictions and required tagging standards.

- **EX6 – Self-Service Password Reset (SSPR)**  
  Implement **identity self-service controls** to reduce helpdesk dependency while maintaining security.

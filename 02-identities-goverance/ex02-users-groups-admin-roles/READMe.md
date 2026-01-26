## Exercise 2 — Create Users & Groups + “Region Ops” Model  
*(Global Organization Design)*

### Purpose

This exercise demonstrates how **Microsoft Entra ID users and security groups** are used to design a **scalable, global identity model** for day-to-day IT operations.

Instead of assigning permissions directly to individuals, this lab reinforces **group-based access management**, which is the foundation for **least privilege, RBAC, and governance at scale**.

---

### Scenario

A **10,000-user global organization** operates across multiple regions:
- **Americas** (Tampa / New York)
- **EMEA** (Europe / Africa)
- **APAC** (Asia)

Regional IT operations teams require access based on **role and geography**, not individual user assignments.

Your task is to create users and security groups that reflect how access is managed in a real production environment.

---

### What This Exercise Demonstrates

- How **Microsoft Entra ID** manages cloud identities using users and security groups
- Why **group-based access** scales better than direct user assignments
- How regional group design supports **RBAC, auditing, and operational clarity**
- How identity structure impacts downstream controls like **Azure RBAC and Policy**

---

### Actions Performed (Azure Portal)

- Create regional **security groups** for IT operations:
  - `grp-az-ops-americas`
  - `grp-az-ops-emea`
  - `grp-az-ops-apac`
- Create **test users** representing regional IT staff
- Assign users to the appropriate regional group
- Document the operational reasoning behind group-based management

---

### Evidence Captured

- Security group list showing all regional operations groups
- Group membership page demonstrating user-to-group assignment
- Users list showing test identities created for the lab

All screenshots support **auditing, interview discussions, and consulting walkthroughs**.

---


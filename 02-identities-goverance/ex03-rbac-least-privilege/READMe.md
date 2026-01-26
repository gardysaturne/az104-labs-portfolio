## Exercise 3 — Azure RBAC Least Privilege at Resource Group Scope  
*(Access Control & Authorization)*

### Purpose

This exercise demonstrates how **Azure Role-Based Access Control (RBAC)** is used to enforce **least-privilege access** by assigning permissions at the **correct scope**.

Rather than granting broad permissions at the subscription level, this lab focuses on **resource group–level access**, which is how real organizations reduce risk and limit blast radius.

---

### Scenario

A **global organization** operates regional IT teams with scoped responsibilities.

- The **Americas operations team** should be able to manage **virtual machines**
- Access must be **limited to a single resource group**
- No access should exist outside that scope

Your task is to implement RBAC using the three core elements:
- **Who** – Security principal (group)
- **What** – Role
- **Where** – Scope

---

### What This Exercise Demonstrates

- How **Azure RBAC** controls access to Azure resources
- Why **least privilege** should be applied at the **lowest effective scope**
- How **security groups** integrate with RBAC assignments
- How to validate and audit role assignments in the Azure Portal

---

### Actions Performed (Azure Portal)

- Create a resource group:
  - `rg-app-americas-dev`
- Navigate to **Access control (IAM)** at the resource group scope
- Assign the **Virtual Machine Contributor** role
- Grant access to the **grp-az-ops-americas** security group
- Verify role assignment visibility and scope behavior

---

### Evidence Captured

- Resource Group **Access control (IAM)** → Role assignments view
- **Add role assignment** wizard (role, member, and review)
- Final role assignment listing confirming scope and permissions

All screenshots demonstrate **controlled access**, **scope awareness**, and **RBAC validation**.

---

### Interview Readiness

After completing this exercise, you should be able to explain:

- The three RBAC components: **who, what, and where**
- Differences between **Owner, Contributor, Reader, and User Access Administrator**
- Why assigning **Owner** broadly is a security risk
- How **Inherited vs This resource** role assignments affect access


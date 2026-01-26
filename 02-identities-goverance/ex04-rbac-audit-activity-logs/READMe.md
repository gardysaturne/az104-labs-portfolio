## Exercise 4 — RBAC Auditing: Activity Log for Role Assignment Changes

### Purpose

This exercise demonstrates how to **audit Azure RBAC changes** using the Azure **Activity Log**, a critical skill for **security, compliance, and incident response** in large organizations.

Rather than granting access, this lab focuses on **proving accountability** — answering **who changed access, what changed, where it applied, and when it happened**.

---

### What This Exercise Demonstrates

By completing this lab, you will show that you can:

- **Audit RBAC changes** at the resource group level using Azure Activity Log  
- **Identify role assignment events** (create / delete) with proper filtering  
- **Trace governance actions back to a specific identity (caller)**  
- **Produce evidence** suitable for audits, access reviews, and troubleshooting  

This mirrors real-world **quarterly access reviews** and compliance workflows.

---

### Scenario

**Quarterly access review**  
Security leadership requests proof of:
- Who granted RBAC access
- What role was assigned
- The scope of the change
- The exact time the change occurred

You are responsible for producing that evidence from Azure.

---

### Actions Performed (Azure Portal)

1. Navigate to **Monitor → Activity log** (scoped to the target resource group).
2. Filter activity by:
   - **Timespan:** Last 7 days or Last 30 days
   - **Operation name contains:** `role`
3. Identify RBAC-related events such as:
   - Create role assignment
   - Delete role assignment
4. Review event details to confirm:
   - **Caller (who made the change)**
   - **Operation name**
   - **Timestamp**
   - **Scope (subscription vs resource group)**
5. (Optional) Export activity results to **CSV** for audit documentation.

---

### Evidence Captured

Screenshots included in this exercise:

- **Activity Log filtered to RBAC operations**
- **Detailed view of a role assignment change event**

Optional artifact:
- CSV export of RBAC activity for the selected timeframe

---

### Key Concepts (Interview & Audit Talk Track)

- **Azure Activity Log** is the authoritative source for **control-plane auditing**
- RBAC changes appear as **Administrative events**
- Proper filtering is required to isolate **governance actions**
- Auditing answers four questions:
  - *Who* made the change
  - *What* changed
  - *Where* it applied (scope)
  - *When* it occurred
- This process supports:
  - Compliance audits
  - Incident investigations
  - Access reviews
  - Least-privilege enforcement

---

### Why This Matters

In enterprise Azure environments, **access without auditability is a security risk**.

This exercise proves you can:
- Defend access decisions
- Support compliance requirements
- Investigate permission-related incidents
- Operate Azure at scale with governance discipline


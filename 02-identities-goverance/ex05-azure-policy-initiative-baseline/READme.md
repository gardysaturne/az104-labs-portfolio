# Exercise 5 — Azure Policy Initiative Baseline (Governance at Scale)

## Purpose

The purpose of this exercise is to demonstrate how **Azure Policy and Policy Initiatives** are used to enforce **organization-wide governance standards** at scale.

Rather than relying on manual reviews or individual administrators to follow rules, this lab shows how governance can be **codified and automatically enforced** across an Azure subscription. This approach is critical in global, remote-first organizations where teams operate across regions, time zones, and regulatory environments.

---

## Scenario

**Global Governance Baseline**

The organization operates across multiple regions (Americas, EMEA, APAC) and requires a consistent baseline that:

- Allows resource deployment **only in approved Azure regions**
- Enforces **mandatory tagging standards** for cost management, ownership, and environment tracking
- Applies these rules **centrally at the subscription scope**

This ensures compliance, cost visibility, and architectural consistency without slowing down engineering teams.

---

## Governance Model Applied

This exercise implements a **Policy Initiative** (policy set) named:


The initiative bundles multiple policies into a single, reusable baseline that can be assigned once and enforced everywhere.

### Included Governance Controls

- **Allowed Locations**
  - Restricts resource deployment to approved Azure regions
- **Required Resource Tags**
  - `costCenter`
  - `owner`
  - `environment`

Together, these policies prevent non-compliant resources from being created while providing clear accountability and financial traceability.

---

## Azure Portal Actions (High Level)

1. Define individual Azure Policies:
   - Allowed locations
   - Require specific resource tags
2. Create a Policy Initiative (`init-governance-baseline-v1`)
3. Assign the initiative at the **subscription scope**
4. Validate that non-compliant deployments are blocked

---

## Screenshots Captured

- Policy assignment scope selection (subscription-level)
- Initiative definition showing included policies
- Initiative assignment confirmation

These screenshots provide visual proof of governance being enforced at scale.

---

## Key Concepts Demonstrated

### RBAC vs Azure Policy

- **RBAC** controls **who can do what**
- **Azure Policy** controls **what is allowed to exist**

Even users with high permissions (Contributor/Owner) are still subject to Policy enforcement.

### Why Policy Initiatives Matter

Policy Initiatives allow organizations to:

- Bundle governance standards into reusable baselines
- Apply controls consistently across subscriptions
- Scale governance without manual enforcement
- Support compliance, security, and cost management goals

This approach is foundational for enterprise Azure environments.

---

## Real-World Relevance

This governance model reflects how large organizations enforce standards across global teams while still enabling agility. By shifting governance left and enforcing rules through code, cloud environments remain secure, compliant, and predictable as they scale.

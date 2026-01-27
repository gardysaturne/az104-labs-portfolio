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


# EX01 - Unexpected Azure Cost Analysis & Remediation

## 🧭 Purpose

This lab demonstrates how to identify, analyze, and remediate unexpected Azure costs caused by mismanaged cloud resources in a lab environment.

## 🧪 Scenario

While building networking labs for AZ-104 preparation, an unexpected charge of $191.04 was incurred within a single billing cycle.

The goal was to:
- Identify the root cause of the cost
- Analyze cost distribution across services and resources
- Safely decommission unnecessary infrastructure
- Implement cost control guardrails

---

## 🔍 Step 1 - Cost Analysis

Navigated to:

Cost Management + Billing → Cost Analysis

Key Findings:
- Application Gateway: $148.42
- Load Balancer: $12.90
- Disk: $3.66
- Public IP: $2.58
- Traffic Manager: $0.75

---

## 🔍 Step 2 - Resource Group Isolation

Identified highest-cost resource group:

rg-az104-week3b-networking → $168.31

---

## 🔍 Step 3 - Resource Breakdown

Resources deployed:

- Application Gateway (WAF)
- Load Balancer
- Virtual Machine
- Managed Disk
- Public IP Address
- Traffic Manager Profile
- Network Security Group
- Route Table
- Network Interface
- WAF Policy

---

## ⚠️ Root Cause

The Application Gateway (WAF_v2 SKU) remained provisioned and running after lab completion.

This service incurs:
- Hourly infrastructure charges
- Capacity-based scaling costs

Unlike VMs, it does not require active usage to generate cost.

---

## 🛠️ Step 4 - Remediation

Performed full cleanup by:

- Navigating to Resource Groups
- Selecting: rg-az104-week3b-networking
- Executing: Delete Resource Group

This ensured:
- Removal of all dependent resources
- No orphaned billable components

---

## 📉 Outcome

- Prevented further cost accumulation
- Identified high-cost Azure services
- Reinforced importance of resource lifecycle management

---

## 🧠 Key Takeaways

- Always delete lab environments after completion
- Application Gateway and WAF are high-cost services
- Cost Analysis is critical for identifying billing anomalies
- Resource Groups should be used as isolation boundaries
- Cleanup strategy should be defined before deployment

---

## 🔐 Preventive Controls Implemented

- Created budget alerts in Cost Management
- Adopted lab lifecycle rule:
  CREATE → USE → DOCUMENT → DELETE
- Avoid deploying high-cost services without purpose

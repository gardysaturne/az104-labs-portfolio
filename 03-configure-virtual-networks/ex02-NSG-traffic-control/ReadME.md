# Exercise 2 — Network Security Groups + Traffic Control  
*(Least-privilege networking)*

---

## Purpose

This exercise demonstrates how to **control inbound and outbound network traffic in Azure using Network Security Groups (NSGs)**, applying **least-privilege principles** with clear intent, correct scope, and audit-friendly rule design.

Rather than relying on default behavior, this lab focuses on **explicit traffic rules** that reflect how production environments secure web and data tiers.

---

## Scenario

A web application consists of:

- A **frontend tier** exposed to the internet
- A **backend database tier** containing sensitive data

Security requirements:

- Frontend must accept **HTTPS (443)** from the internet
- Backend must **only accept traffic from the frontend**
- Administrative access must be **restricted, intentional, and auditable**

---

## What This Exercise Demonstrates

This exercise reinforces how Azure networking security works **in real environments**:

- How **NSGs enforce traffic control at the subnet level**
- How to design **least-privilege inbound rules** instead of relying on implicit trust
- Why **scope matters** (subnet-level NSGs vs NIC-level)
- How **rule priority and evaluation order** affect traffic flow
- How administrators document intent for **audits, troubleshooting, and interviews**

---

## High-Level Design

- **Frontend subnet**
  - Allows HTTPS from the internet
  - Optional restricted admin access (SSH/RDP from a known IP)

- **Backend subnet**
  - Allows database traffic **only from frontend subnet**
  - No direct internet exposure

Each subnet uses its **own NSG**, aligned to its role.

---

## Administrative Actions (Portal)

1. Create two Network Security Groups:
   - `nsg-frontend`
   - `nsg-backend`

2. Configure inbound rules:
   - **Frontend NSG**
     - Allow HTTPS (443) from Internet
     - (Optional) Allow SSH (22) or RDP (3389) from your public IP only

   - **Backend NSG**
     - Allow database port (example: 1433) **from frontend subnet CIDR**
     - Rely on default deny for all other inbound traffic

3. Associate NSGs to subnets:
   - Attach `nsg-frontend` to `snet-frontend`
   - Attach `nsg-backend` to `snet-backend`

4. Validate rule evaluation:
   - Review **Priority values**
   - Inspect **Effective security rules**


Network security in Azure is not about blocking traffic randomly —  
it is about **explicitly allowing only what is required**, at the **correct scope**, with rules that can be **explained, audited, and defended**.

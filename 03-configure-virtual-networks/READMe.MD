## Purpose

This lab series focuses on **Azure Virtual Network operations**, aligned to **AZ-104** and modeled after how a **global, remote-first organization** designs, secures, and operates network connectivity at scale.

Rather than treating networking as isolated resources, these exercises emphasize **real-world administrative decision-making**, including IP address planning, subnet segmentation, traffic control, private connectivity, and name resolution across regions and environments.

---

## What This Lab Demonstrates

Each exercise is designed to reinforce how **Azure networking actually works in production**:

- How **Azure Virtual Networks and subnets** define security and operational boundaries
- How **Network Security Groups (NSGs)** control traffic using **least-privilege principles**
- How **VNet peering** enables private, backbone-only communication between environments
- How **Azure DNS (public and private)** supports scalable, identity-first name resolution
- How administrators **design, validate, and govern network changes** in distributed environments

All work is performed using the **Azure Portal (PWA)** with supporting documentation and screenshots suitable for **architecture reviews, audits, interviews, and consulting walkthroughs**.

---

## Labs Overview

- **EX1 – Virtual Network & Subnet Architecture Design**  
  Design and configure **Azure virtual networks and subnets** with intentional IP addressing to support future growth, service requirements, and regional expansion.

- **EX2 – Network Security Groups & Traffic Control**  
  Apply **Network Security Groups (NSGs)** at the subnet and NIC level to enforce controlled inbound and outbound traffic using clear, auditable rules.

- **EX3 – Virtual Network Peering (Private Connectivity)**  
  Configure **VNet peering** between isolated environments to enable secure, low-latency communication over the **Azure backbone** without exposing traffic to the public internet.

- **EX4 – Azure DNS & Name Resolution Strategy**  
  Implement **Azure DNS (public and private)** to support reliable name resolution for Azure resources while aligning with **identity-first, private-by-default networking principles**.

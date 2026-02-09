## Purpose

This lab series focuses on **virtual networking operations in Azure**, aligned to **AZ-104** and modeled after how a **10,000-user global organization** designs, secures, and operates network infrastructure at scale.

Rather than isolated networking tasks, these exercises emphasize **real-world administrative decision-making**, including IP address planning, segmentation by trust boundary, least-privilege traffic control, private connectivity, DNS strategy, and operational diagnostics across regions.

---

## What This Lab Demonstrates

Each exercise is designed to reinforce how **Azure virtual networking actually works in production**:

- How **virtual networks and subnets** establish scalable IP design and trust boundaries
- How **Network Security Groups (NSGs)** enforce least-privilege traffic control
- How **VNet peering** enables private connectivity over the Microsoft backbone
- How **Azure DNS (public and private)** supports external and internal name resolution
- How **user-defined routes (UDRs)** control traffic flow independently of security rules
- How administrators **validate, troubleshoot, and audit network behavior** using Azure Network Watcher

All work is performed using the **Azure Portal (PWA)** with supporting documentation and screenshots suitable for **audits, interviews, and consulting walkthroughs**.

---

## Labs Overview

- **EX1 – Virtual Network & Subnet Architecture Design**  
  Design a scalable VNet and subnet layout with intentional IP planning, segmentation by trust boundary, and reserved capacity for Azure platform services.

- **EX2 – Network Security Groups & Least-Privilege Traffic Control**  
  Implement NSGs at the correct scope to restrict traffic between application tiers while maintaining controlled and auditable administrative access.

- **EX3 – Virtual Network Peering (Hub-and-Spoke Foundation)**  
  Configure private VNet peering between application and hub networks to enable secure connectivity without routing traffic over the public internet.

- **EX4 – Azure DNS: Public & Private Name Resolution Strategy**  
  Deploy public DNS zones for external services and private DNS zones for internal name resolution across peered virtual networks.

- **EX5 – User Defined Routes (Traffic Flow Control)**  
  Create and associate route tables to control how traffic flows through the network, reinforcing the distinction between routing decisions and security enforcement.

- **EX6 – Azure Network Watcher Diagnostics & Visibility**  
  Use Azure Network Watcher tools to validate connectivity, inspect routing behavior, and diagnose traffic filtering issues in IaaS environments.


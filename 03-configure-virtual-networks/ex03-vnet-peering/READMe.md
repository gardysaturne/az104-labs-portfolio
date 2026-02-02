# Exercise 3 — Virtual Network Peering (Private Backbone Connectivity)

## Purpose
This exercise demonstrates how to securely connect Azure Virtual Networks using **VNet Peering** to enable private, high-performance communication without exposing traffic to the public internet.

This is a foundational building block for **hub-and-spoke architecture** in Azure.

---

## Scenario
A global, remote-first organization is designing a hub-and-spoke network model.

- The **app VNet (spoke)** hosts application workloads
- The **hub VNet** hosts shared services (firewall, monitoring, future gateways)
- All communication must remain on Azure’s private backbone
- No public internet routing between VNets

---

## What This Lab Demonstrates
- How to create **VNet peering** between two Azure VNets
- How traffic flows privately between peered VNets
- How Azure enables **low-latency, private connectivity** across VNets
- How hub-and-spoke networking is established at the network layer

---

## Architecture Overview
- **app-vnet** (spoke)
  - Application subnets (frontend / backend)
- **hub-vnet**
  - Shared services subnet (AzureFirewallSubnet reserved)

Traffic between VNets:
- Stays on the Microsoft backbone
- Does **not** traverse the public internet
- Respects NSGs and routing rules

---

## Steps Performed (Portal)

### 1. Create Peering from app-vnet to hub-vnet
- Navigate to **app-vnet**
- Select **Peerings** → **Add**
- Name: `peer-app-to-hub`
- Remote virtual network: `hub-vnet`
- Allow VNet access: **Enabled**

### 2. Confirm Reverse Peering
- Navigate to **hub-vnet**
- Select **Peerings**
- Confirm `peer-hub-to-app` exists
- If not auto-created, create it manually

### 3. Validate Connectivity
- Confirm peering status shows **Connected** on both VNets

### 4. (Optional) Connectivity Test
- Deploy a small test VM in:
  - `app-vnet` (frontend subnet)
  - `hub-vnet` (shared subnet)
- Validate connectivity using:
  - Ping
  - Port test (if NSGs allow)

---

## Why This Design Matters
- Enables **secure, private communication** between environments
- Prevents unnecessary exposure to the public internet
- Scales cleanly as more spokes are added
- Aligns with real-world enterprise Azure architectures

---

## Key Interview Talking Points
- Why VNet peering uses Azure’s private backbone
- Difference between peering vs VPN vs public routing
- Why hub-and-spoke simplifies security and governance
- How NSGs still control traffic across peered VNets
- Why address space planning is critical before peering

---

## Screenshots Captured
- app-vnet peering configuration
- hub-vnet reverse peering
- Peering status showing **Connected**
- (Optional) VM connectivity validation

---

## Outcome
A secure, scalable, enterprise-ready Azure network foundation using VNet peering.

# Exercise 3 — Virtual Network Peering

## Purpose
Demonstrate how to securely connect Azure Virtual Networks using **VNet Peering** to enable private communication over Azure’s backbone without exposing traffic to the public internet.

---

## Scenario
An application VNet (spoke) must securely communicate with a hub VNet that hosts shared services.  
This design supports a **hub-and-spoke architecture** and prevents public internet routing between environments.

---

## What This Lab Demonstrates
- Private connectivity between VNets using Azure VNet Peering
- Hub-and-spoke network design fundamentals
- Secure traffic flow that remains on Azure’s private backbone
- Foundation for shared services (firewall, monitoring, future gateways)

---

## Outcome & Why This Design Matters
- VNets can communicate privately with **low latency** and **no public exposure**
- Network boundaries are clearly defined between application and shared services
- Design scales cleanly as additional spokes are added
- Aligns with real-world enterprise Azure networking patterns

---

## Screenshots Captured
- app-vnet peering configuration
- hub-vnet reverse peering
- Peering status showing **Connected**
- (Optional) VM-to-VM connectivity validation

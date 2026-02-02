# Exercise 4 — Azure DNS & Name Resolution Strategy  
**(Public DNS + Private DNS)**

## Purpose
Demonstrate how Azure DNS is used for both **public-facing services** and **private internal name resolution** across virtual networks.

This lab shows how DNS supports secure application architecture by separating external access from internal service communication.

---

## Scenario
A company operates:
- A **public website** accessible from the internet
- **Private internal services** that must resolve names across VNets without exposing traffic publicly

Azure DNS is used for public records, while **Private DNS Zones** handle internal name resolution between VNets.

---

## What This Lab Demonstrates
- Creation of an **Azure Public DNS Zone** for external name resolution
- Creation of **DNS record sets** (A records) for public services
- Use of **Private DNS Zones** for internal-only name resolution
- Linking multiple VNets (hub + app) to a Private DNS Zone
- Clear separation of public vs private DNS responsibilities

---

## Outcome & Why This Design Matters
- Public users resolve services via **Azure Public DNS**
- Internal workloads resolve private services using **Private DNS Zones**
- No internal IPs are exposed to the internet
- VNets can communicate using **DNS names instead of IP addresses**
- This design supports **hub-and-spoke architectures**, zero-trust networking, and scalable platform operations

---

## Screenshots Captured
- Public DNS zone showing **A record (www)**
- Public DNS zone showing **NS record set** (Azure name servers)
- Private DNS zone showing **virtual network links** for:
  - app-vnet
  - hub-vnet
- (Optional) Private DNS zone showing internal **A record (api)**


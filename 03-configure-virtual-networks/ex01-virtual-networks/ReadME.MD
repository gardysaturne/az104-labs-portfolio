## Exercise 1 — Virtual Network + Subnet Architecture Design  
*(Platform segmentation)*

### Purpose

Design a **scalable Azure virtual network and subnet architecture** with intentional IP planning, clear segmentation boundaries, and room for future growth.

This exercise demonstrates that virtual networking is not about “creating a VNet,” but about **establishing security, operational, and expansion boundaries** that support long-term platform operations.

---

### Scenario

A **global, remote-first organization** is expanding into a second region. The platform team needs a **hub-and-spoke-ready network foundation** that:

- Separates application tiers (web, data, management)
- Reserves address space for future Azure platform services
- Avoids IP overlap to support future peering and hybrid connectivity
- Can scale without requiring a full network redesign

---

### What This Exercise Demonstrates

This exercise reinforces how **Azure virtual networking works in real production environments**, including:

- How **address space planning** enables future growth and multi-region expansion
- How **subnets define trust and operational boundaries**, not just IP ranges
- Why certain Azure services require **dedicated subnets** (firewall, gateway, bastion)
- How early design decisions directly impact **security, governance, and operability**

---

### Architecture Overview

The design uses a **hub-and-spoke-ready model**:

- **Spoke VNet (app-vnet)**  
  Hosts application workloads, segmented by role:
  - Frontend subnet
  - Backend subnet
  - Optional management subnet

- **Hub VNet (hub-vnet)**  
  Reserved for shared and platform services, with address space intentionally carved out for future use (firewall, connectivity, shared services).

All IP ranges are planned to **avoid overlap** and allow for seamless peering, service expansion, and future hybrid connectivity.

---

### Key Design Decisions (Director-Level Context)

- **/16 address spaces** are used at the VNet level to prevent early exhaustion.
- **/24 subnets** provide sufficient capacity while maintaining clear segmentation.
- Platform-required subnets (e.g., `AzureFirewallSubnet`) are **planned upfront**, not retrofitted later.
- The design assumes **identity-driven access** and **private-by-default traffic flow**, not flat internal trust.

---

### Validation & Evidence

Screenshots and diagrams captured for this exercise demonstrate:

- Intentional address space allocation
- Subnet segmentation aligned to workload roles
- Reserved capacity for platform services
- Readiness for hub-and-spoke expansion

These artifacts are suitable for **architecture reviews, audits, interviews, and consulting walkthroughs**.

---

### Outcome

At the end of this exercise, the Azure environment has a **clean, scalable network foundation** that reflects **platform thinking**, not lab-driven configuration.

This design can safely support additional workloads, regions, and services without breaking existing assumptions.

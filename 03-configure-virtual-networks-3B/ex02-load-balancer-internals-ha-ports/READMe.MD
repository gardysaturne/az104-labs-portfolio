# Exercise 2 — Azure Load Balancer Internals

*(Frontend IP, Backend Pool, Health Probes, Load Balancing Rules, HA Ports, Session Persistence)*

---

## Purpose

This exercise focuses on **understanding and configuring Azure Load Balancer internals**, aligned to **AZ-104**, with emphasis on **exam-accurate wording and real-world design patterns**.

Rather than treating Load Balancer as a single object, this lab breaks it down into its **core components** and demonstrates how they work together to provide **high availability**, **traffic distribution**, and **fault detection** for internal service tiers and network virtual appliance (NVA) scenarios.

---

## Scenario

An internal application or network virtual appliance (NVA) tier must be **highly available** and capable of accepting traffic across **many ports simultaneously**.

The platform team requires:
- A **Standard Azure Load Balancer**
- Internal traffic distribution
- **Health-based traffic decisions**
- Support for **all ports** without creating individual rules per port

This design must meet enterprise requirements for **resiliency**, **scalability**, and **simplified operations**, using Azure-native networking services.

---

## What This Exercise Demonstrates

This exercise reinforces how **Azure Load Balancer actually works in production**, including:

- How a **Standard Load Balancer** operates as a **Layer 4 (TCP/UDP) regional dataplane**
- The functional role of each Load Balancer component:
  - **Frontend IP configuration** (entry point)
  - **Backend pool** (traffic destinations)
  - **Health probes** (backend availability validation)
  - **Load balancing rules** (traffic mapping logic)
- How **health probes** determine which backends receive traffic
- How **HA Ports** enable *all-port* load balancing using a single rule
- When and why **HA Ports** are used in **NVA and service-tier designs**
- The meaning and purpose of **session persistence** (client affinity) and when to use or avoid it

All configuration is performed using the **Azure Portal (PWA)** with screenshots suitable for **exam review, architecture discussions, and interviews**.

---

## Real-World Relevance

This design pattern is commonly used for:
- **Internal service tiers** that expose multiple ports
- **Network virtual appliances (firewalls, proxies, IDS/IPS)**
- Scenarios where creating individual port rules is operationally inefficient
- High-throughput environments requiring **simple, resilient L4 traffic distribution**

Understanding these internals ensures you can:
- Interpret **exact AZ-104 exam wording** (HA Ports, probes, persistence)
- Design load balancing solutions that scale cleanly
- Explain *why* a Load Balancer behaves the way it does — not just how to click through it

---


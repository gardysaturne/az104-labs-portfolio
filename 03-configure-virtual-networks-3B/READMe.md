## Purpose

This lab series focuses on **Azure virtual networking operations**, aligned to **AZ-104** and modeled after how a **10,000-user global, remote-first organization** designs, secures, and operates network connectivity at scale.

Rather than treating networking as isolated resources, these exercises emphasize **real-world administrative decision-making**, including service selection, IP address planning, segmentation by trust boundary, traffic control, private connectivity, global routing, and operational diagnostics across regions and environments.

---

## What This Lab Demonstrates

Each exercise is designed to reinforce how **Azure virtual networking actually works in production**:

- How **Azure networking services** are selected based on scope, OSI layer, and service boundaries  
- How **Load Balancer, Application Gateway, and Traffic Manager** differ in purpose and use cases  
- How **Azure Load Balancer internals** (frontend IPs, backend pools, probes, rules, HA Ports, and session persistence) function together  
- How **user-defined routes (UDRs)** and **virtual appliance next hops** control traffic flow independently of security rules  
- How **Azure Network Watcher** tools are used to validate, troubleshoot, and audit network behavior  
- How administrators interpret **exam-specific wording** and translate it into correct architectural decisions

All work is performed using the **Azure Portal (PWA)** with supporting documentation and screenshots suitable for **architecture reviews, audits, interviews, and consulting walkthroughs**.

---

## Labs Overview

- **EX1 – Azure Traffic Service Differentiation**  
  Evaluate and compare **Azure Load Balancer, Application Gateway, and Traffic Manager** to understand service boundaries, scope (regional vs global), and OSI layer responsibilities.

- **EX2 – Azure Load Balancer Internals & HA Ports**  
  Configure and examine Load Balancer components including frontend IPs, backend pools, health probes, load-balancing rules, **HA Ports**, and session persistence behavior.

- **EX3 – Application Gateway Core Configuration & Session Affinity**  
  Build an Application Gateway to understand Layer 7 routing concepts such as listeners, rules, backend settings, TLS termination, and **cookie-based session affinity**.

- **EX4 – Traffic Manager Global Routing Strategy**  
  Configure Traffic Manager profiles to demonstrate **DNS-based global routing**, health probes, and routing methods such as Performance and Failover.

- **EX5 – User Defined Routes & Virtual Appliance Traffic Control**  
  Implement UDRs using the **Virtual appliance** next hop to control traffic paths and reinforce the distinction between routing decisions and security enforcement.

- **EX6 – Azure Network Watcher Diagnostics & Tool Selection**  
  Use Network Watcher tools to identify traffic flow, routing decisions, and security rule evaluation, reinforcing correct tool selection based on troubleshooting scenarios.

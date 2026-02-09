# Exercise 1 — Azure Traffic Service Differentiation  
*(Service boundaries & architectural decision-making)*

---

## Purpose

The purpose of this exercise is to **evaluate and differentiate Azure traffic management services**—specifically **Azure Load Balancer**, **Application Gateway**, and **Traffic Manager**—based on **scope, OSI layer, and service responsibility**.

Rather than deploying services blindly, this exercise reinforces that **traffic services are architectural decisions**, and selecting the wrong service can introduce scalability, security, or availability risks in production environments.

---

## Scenario

A **global, remote-first organization** is operating applications across multiple Azure regions and must design a traffic strategy that meets the following requirements:

- Internal application services require **high-performance, low-latency traffic distribution**
- Public-facing web applications require **Layer 7 routing**, **TLS termination**, and **WAF readiness**
- Users must be routed to the **closest healthy region globally**, with automatic failover during outages
- Traffic decisions must align with **clear service boundaries** to support long-term scalability

The platform team must determine **which Azure traffic service is appropriate for each requirement**, without overlapping responsibilities or introducing unnecessary complexity.

---

## What This Exercise Demonstrates

This exercise reinforces how **Azure traffic services are designed to solve different problems**, including:

- How **Azure Load Balancer** operates at **Layer 4 (TCP/UDP)** for regional, high-throughput traffic distribution
- How **Application Gateway** operates at **Layer 7 (HTTP/HTTPS)** for advanced web routing, TLS termination, and WAF integration
- How **Traffic Manager** performs **DNS-based global routing** without acting as a data-plane proxy
- How service **scope (regional vs global)** impacts architecture decisions
- How exam-specific wording maps directly to real architectural boundaries

This exercise emphasizes **why these services are not interchangeable**, even though they all influence traffic flow.

---

## Architecture Overview

The solution architecture uses **three distinct traffic services**, each operating at a different boundary:

- **Azure Load Balancer**  
  Handles internal or public **Layer 4 traffic distribution** within a single Azure region.

- **Azure Application Gateway**  
  Provides **Layer 7 HTTP(S) routing**, TLS termination, and optional Web Application Firewall (WAF) for web workloads.

- **Azure Traffic Manager**  
  Uses **DNS-based routing** to direct users to the closest or healthiest regional endpoint, without inspecting or proxying traffic.

Each service is placed intentionally based on **protocol awareness, routing responsibility, and operational scope**, ensuring no overlap in function.

---

## Why This Is a Real-World Solution

In global production environments, traffic design mistakes often occur when services are selected based on familiarity rather than **architectural fit**.

This approach solves real-world problems by:

- Preventing **misuse of Layer 7 services** for Layer 4 workloads
- Avoiding the assumption that global routing requires a global proxy
- Ensuring **security features (WAF, TLS)** are applied only where appropriate
- Supporting **regional scale-out and global failover** without redesign
- Aligning Azure services with how **enterprise networking teams actually operate**

By clearly separating **global routing**, **regional load distribution**, and **application-layer routing**, this design supports **scalability, resilience, and long-term maintainability** for global organizations.

---

## Outcome

After completing this exercise, you should be able to:

- Select the correct Azure traffic service based on **OSI layer and scope**
- Explain **why Load Balancer, Application Gateway, and Traffic Manager are different**
- Translate **AZ-104 exam wording** into real architectural decisions
- Defend traffic service choices in **architecture reviews and interviews**


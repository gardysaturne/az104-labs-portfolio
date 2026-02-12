# EX03 – Application Gateway Core Build (WAF_v2 + Session Affinity)

## 🎯 Purpose

This exercise demonstrates how to deploy and configure an Azure **Application Gateway (WAF_v2)** with:

- Public frontend IP
- Backend pool
- HTTP listener and routing rule
- Backend HTTP settings
- Cookie-based session affinity enabled

The objective is to prove understanding of **Layer 7 (L7) load balancing**, listener-to-backend mapping, and session persistence behavior in Azure.

---

## 📖 Scenario

A public web application requires:

- TLS termination at the edge (Application Gateway)
- Consistent session behavior during login/checkout
- A WAF-ready architecture for traffic inspection

Security requires centralized inspection before traffic reaches backend servers.

---

## 🏗 Architecture Components Configured

### 1️⃣ Application Gateway (WAF_v2)

- Name: `agw-ex03-core`
- Tier: `WAF_v2`
- Region: East US
- Autoscaling enabled
- Dedicated subnet: `snet-appgw (10.10.3.0/24)`
- Public IP: `pip-appgw-ex03`

> Application Gateway requires a **dedicated subnet** and cannot share it with other resources.

---

### 2️⃣ Frontend Configuration

- Frontend IP type: Public
- Protocol: HTTP
- Port: 80
- Listener name: `lis-ex03-http`

This is the entry point for internet traffic.

---

### 3️⃣ Backend Pool

- Name: `bp-ex03-web`
- Current targets: 0

This backend pool is designed to contain:
- VM private IP addresses
- VM Scale Sets
- App Services
- FQDN targets

At this stage, no backend targets were added.

---

### 4️⃣ Backend HTTP Settings

- Name: `bhs-ex03-http-80`
- Backend protocol: HTTP
- Backend port: 80
- Cookie-based affinity: **Enabled**
- Request timeout: 20 seconds

Enabling cookie-based affinity inserts:


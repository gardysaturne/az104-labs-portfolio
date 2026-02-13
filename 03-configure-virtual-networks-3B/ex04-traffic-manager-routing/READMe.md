# EX04 – Traffic Manager Global Routing (DNS-Based)

## 🎯 Purpose

This exercise demonstrates how to deploy and configure Azure Traffic Manager using DNS-based global routing.

The objective is to prove understanding of:

- DNS-based routing vs proxy-based routing
- Performance (closest region) routing
- Failover (primary/secondary) routing
- Endpoint health monitoring behavior
- Service boundary clarity (Traffic Manager vs Application Gateway)

---

## 📘 Scenario

A company runs its application in East US and is launching a second region in Central US.

Requirements:

- Users must be directed to the closest region
- Failover must occur automatically if a region becomes unhealthy
- Routing must be DNS-based (not proxy-based)

---

## 🧠 Core Concept

Traffic Manager returns DNS answers.  
It does NOT proxy or terminate traffic.

Traffic Manager:
- Does NOT terminate TLS
- Does NOT inspect HTTP traffic
- Does NOT sit in the data path
- Only responds to DNS queries with the best endpoint

---

# 🏗 Architecture Built

## 1️⃣ Traffic Manager Profile

- Name: tm-ex04-perf
- Routing Method: Performance
- Location: Global
- DNS Name: tm-ex04-perf.trafficmanager.net
- DNS TTL: 60 seconds

---

## 2️⃣ Endpoints Configured

| Name | Type | Location | Purpose |
|------|------|----------|----------|
| ep-eastus-primary | External endpoint | East US | Closest region target |
| ep-centralus-secondary | External endpoint | Central US | Secondary region |

Endpoint Monitor Settings:

- Protocol: HTTP
- Port: 80
- Path: /
- Expected Status Code: 200
- Probe Interval: 30 seconds
- Tolerated Failures: 3
- Probe Timeout: 10 seconds

---

# 🔁 Routing Method Behavior

## Performance Routing (Used in This Lab)

Traffic Manager selects the endpoint based on:

- Lowest network latency from the user
- Microsoft global network latency table
- Only healthy endpoints are returned in DNS response

If both regions are healthy:
→ User is routed to closest region.

If closest region becomes unhealthy:
→ Traffic Manager returns next closest healthy endpoint.

---

## Failover Routing (Active/Passive Model)

If routing method is set to Failover:

- Primary endpoint is always returned if healthy.
- If primary becomes unhealthy:
  → Traffic Manager returns secondary endpoint.
- Failback occurs automatically once primary becomes healthy again.

---

# 🩺 Health Monitoring Logic

Traffic Manager continuously probes each endpoint using configured monitor settings.

Endpoint Status States:

- CheckingEndpoint → Initial probing phase
- Online → Endpoint responding successfully
- Degraded → Endpoint failing health checks
- Disabled → Manually disabled

Only endpoints marked healthy are returned in DNS responses.

---

# 📸 Screenshots Captured

- Traffic Manager profile overview showing routing method
- Endpoints list showing type and region
- Endpoints monitor status (Checking / Degraded)
- Configuration page showing monitor settings

---

# 🎤 Interview Talking Points

Traffic Manager is:

- A DNS-based global load balancer
- Not an L4 or L7 proxy
- Not in the data path
- Does not terminate TLS

Use Performance routing when:
- You want users sent to the closest region.

Use Failover routing when:
- You want active/passive disaster recovery.

Boundary clarity:

Traffic Manager decides WHERE users go.  
Application Gateway decides HOW traffic is processed.

---

# 🏁 Exercise Outcome

Successfully deployed and configured:

- Traffic Manager profile
- Performance-based global routing
- Multi-region endpoints
- Health monitoring configuration
- DNS-based automatic failover behavior


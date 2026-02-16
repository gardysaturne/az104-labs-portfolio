# EX05 – Enforcing Traffic Inspection with UDR (Virtual Appliance Next Hop)

## 🎯 Purpose

This exercise demonstrates how to control traffic flow inside an Azure Virtual Network by using a **User Defined Route (UDR)** to force subnet traffic through a Network Virtual Appliance (NVA).

The goal is to show how Azure route tables override system routes and enforce inspection paths using the **Virtual appliance** next hop type.

---

## 🧠 Scenario

After a security incident, the cloud team must ensure that all traffic between subnets is inspected by a firewall/NVA before reaching backend resources.

The requirement:

- Traffic destined for the **backend subnet (10.10.1.0/24)** must route through an NVA
- The NVA must be capable of forwarding traffic
- The routing decision must override Azure's default system routes

---

## 🏗 Architecture Overview

| Component | Configuration |
|------------|---------------|
| Virtual Network | `app-vnet` |
| Backend Subnet | `snet-backend (10.10.1.0/24)` |
| Management Subnet (NVA location) | `snet-management (10.10.2.0/24)` |
| NVA VM Private IP | `10.10.2.4` |
| Route Table | `rt-inspection-path` |
| UDR Name | `to-backend-via-nva` |
| Next Hop Type | `Virtual appliance` |

---

## ⚙️ Implementation Steps

### 1️⃣ Created Route Table
- Name: `rt-inspection-path`
- Region: East US
- Associated to: `snet-backend`

---

### 2️⃣ Created User Defined Route

| Setting | Value |
|----------|--------|
| Route Name | `to-backend-via-nva` |
| Address Prefix | `10.10.1.0/24` |
| Next Hop Type | `Virtual appliance` |
| Next Hop IP | `10.10.2.4` |

This overrides Azure's system route for the backend subnet.

---

### 3️⃣ Enabled IP Forwarding on the NVA NIC

IP forwarding was enabled on the VM NIC (`vm-nva-placeholder`).

Without this setting:
- Azure drops forwarded packets
- The VM cannot act as a router/firewall

This is required for any VM acting as an NVA.

---

### 4️⃣ Associated Route Table to Backend Subnet

Route table `rt-inspection-path` was attached to:

- `snet-backend`

This ensures traffic originating from that subnet follows the UDR.

---

## 📸 Screenshots Captured

- `ex05-route-table-created.png`
- `ex05-udr-route-to-backend-via-nva.png`
- `ex05-route-table-associated-to-snet-backend.png`
- `ex05-nva-nic-ip-forwarding-enabled.png`
- *(Optional)* `ex05-backend-nic-effective-routes.png`

---

## 🔎 Route Selection Logic (Interview Notes)

Azure selects routes using:

1. **Longest prefix match**
2. Route priority order:
   - UDR
   - BGP
   - System routes

Because `10.10.1.0/24` is explicitly defined in the UDR, it overrides the default system route.

---

## 🔐 NSG vs UDR (Key Concept)

| NSG | UDR |
|------|------|
| Controls traffic (Allow/Deny) | Controls path selection |
| Layer 4 filtering | Layer 3 routing decision |
| Does NOT change route path | Overrides default routes |

NSGs filter traffic.
UDRs determine *where* traffic flows.

---

## ✅ Outcome

- Backend subnet traffic is now forced through the NVA.
- Default system routes have been overridden.
- IP forwarding is enabled, allowing the VM to function as a virtual appliance.
- Traffic inspection architecture is enforced at the subnet level.

This demonstrates practical control over Azure traffic flow using UDRs and custom next hop configurations.

---

## 🧩 Real-World Use Cases

- Forced tunneling
- Firewall insertion
- Hub-and-spoke inspection models
- East-west traffic inspection
- Zero-trust segmentation strategies

---

## 💰 Cost Optimization Note

The NVA VM was stopped (deallocated) after validation to prevent ongoing compute charges.

---

## 📌 Key Takeaway

In Azure:

> NSGs filter traffic.  
> UDRs decide the path.  
> Longest prefix match wins.

This lab reinforces how to control and inspect internal network traffic using Azure-native routing capabilities.

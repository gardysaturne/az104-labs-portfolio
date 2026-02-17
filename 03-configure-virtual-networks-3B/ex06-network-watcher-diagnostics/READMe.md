# EX06 – Azure Network Watcher: Connectivity, NSG, and Routing Diagnostics

## 📌 Purpose

The purpose of this lab was to validate and troubleshoot network connectivity using **Azure Network Watcher**.  

This exercise focused on:

- Verifying effective security rules applied to a VM
- Testing outbound and inbound connectivity
- Validating NSG rule behavior
- Analyzing next hop routing
- Understanding Azure system routes
- Comparing topology across regions

This lab reinforces how Azure evaluates traffic through **NSGs, system routes, and diagnostic tools**.

---

## 🧠 Scenario

A virtual machine (`vm-az104-utility`) was deployed in the **UK South** region inside resource group:

```
rg-az104-utilities
```

The goal was to validate:

1. Whether the VM could reach the public internet (8.8.8.8 over TCP 443)
2. How outbound traffic is evaluated through NSGs
3. Why inbound traffic is denied by default
4. What route Azure selects for internet-bound traffic
5. How effective security rules reflect applied NSGs

---

## 🛠 Tools Used

- Azure Network Watcher
- Connection Troubleshoot
- IP Flow Verify
- Effective Security Rules
- Next Hop
- Topology View

---

# 🔎 Exercise Breakdown

---

## 1️⃣ Network Watcher Overview

Validated that Network Watcher was enabled in:

- East US
- UK South

Confirmed diagnostic tools were available per region.

📸 Screenshot:  
`ex06-network-watcher-overview.png`

---

## 2️⃣ Topology Analysis

Compared infrastructure layout between:

- East US (hub-spoke architecture with load balancer & app gateway)
- UK South (single VNet deployment)

This demonstrates regional resource isolation and architectural differences.

📸 Screenshots:
- `ex06-eastus-topology.png`
- `ex06-uksouth-topology.png`

---

## 3️⃣ Effective Security Rules

Used **Effective Security Rules** to validate which NSGs were applied to the VM NIC.

Confirmed:

- NSG attached at the network interface level
- Rules reflected merged evaluation logic
- Default deny inbound behavior exists

📸 Screenshot:
`ex06-effective-rules-no-nsg-uksouth.png`

---

## 4️⃣ Connection Troubleshoot (Outbound Test)

Tested connectivity from:

Source:
```
vm-az104-utility
```

Destination:
```
8.8.8.8 : 443 (TCP)
```

Result:

- ✅ Connectivity: Reachable
- ✅ Outbound NSG Diagnostic: Allow
- ✅ Next Hop: Internet
- ✅ Route Table: System Route

This confirms:

- Azure automatically injects system routes for internet-bound traffic.
- Default outbound access is permitted unless explicitly denied.

📸 Screenshot:
`ex06-connection-troubleshoot-8.8.8.8-443-reachable.png`

---

## 5️⃣ IP Flow Verify – Outbound (Allowed)

Tested outbound TCP traffic:

```
Local IP: 172.18.0.4
Remote IP: 8.8.8.8
Port: 443
Direction: Outbound
```

Result:

```
Access Allowed
Security Rule: AllowInternetOutBound
```

This confirms the NSG rule allowing internet egress traffic.

📸 Screenshot:
`ex06-ip-flow-verify-access-allowed.png`

---

## 6️⃣ IP Flow Verify – Inbound (Denied)

Tested inbound TCP traffic without a specific allow rule.

Result:

```
Access Denied
Security Rule: DenyAllInBound
```

This demonstrates Azure’s default security posture:

> All inbound traffic is denied unless explicitly allowed.

📸 Screenshot:
`ex06-ip-flow-verify-access-denied.png`

---

## 7️⃣ IP Flow Verify – Explicit Allow Rule (SSH)

Tested inbound SSH (TCP 22) after defining an allow rule.

Result:

```
Access Allowed
Security Rule: Allow_SSH_Inbound
NSG: vm-az104-utility-nsg
```

This confirms rule evaluation order and proper NSG configuration.

📸 Screenshot:
`ex06-ipflowverify-alllow-ssh-inbound.png`

---

## 8️⃣ Next Hop Analysis

Tested next hop for destination:

```
8.8.8.8
```

Result:

```
Next Hop Type: Internet
Route Table: System Route
```

Key Takeaway:

Azure automatically injects system routes into subnets.  
Unless overridden by a User Defined Route (UDR), internet-bound traffic uses the default system route.

📸 Screenshot:
`ex06-nexthop-systemroute-internet.png`

---

# 🧠 Key Infrastructure Concepts Reinforced

- Azure injects default system routes automatically.
- NSGs evaluate traffic before routing decisions.
- Default inbound traffic is denied.
- Outbound internet traffic is allowed by default.
- Effective security rules reflect combined subnet + NIC policies.
- Network Watcher provides control-plane visibility into data-plane behavior.
- Routing and security must both succeed for connectivity.

---

# 🏆 Outcome

By completing this lab, I demonstrated the ability to:

- Troubleshoot VM connectivity
- Interpret NSG rule behavior
- Validate routing paths
- Use Azure diagnostic tooling effectively
- Analyze security posture
- Understand Azure's default networking behavior

This lab reflects practical infrastructure engineering workflows used in real-world environments.

---

# 🔥 Summary

Azure networking is not just about creating resources —  
it’s about understanding how traffic is evaluated, routed, and secured.

This exercise validated:

- Connectivity
- Security
- Routing
- Observability

End-to-end.

---



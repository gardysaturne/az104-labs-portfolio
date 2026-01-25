# EX4 — Bash + Azure CLI: Cross-Platform Automation

## Scenario

As an on-call cloud administrator supporting a globally distributed environment, I needed a fast, platform-agnostic way to audit Azure resources from a browser without relying on PowerShell or a local workstation.

Using Azure Cloud Shell in Bash mode, I enumerated resource groups, virtual machines, and public IPs, filtered runtime states using standard Unix tooling (`grep`), and generated an auditable snapshot of the environment while intentionally keeping all lab VMs deallocated to control costs.

## What I did

- Verified subscription and tenant context using `az account show`
- Enumerated resource groups and virtual machines via Azure CLI
- Filtered VM power states using Bash pipelines
- Exported results to files for audit and documentation
- Validated public IP exposure without running workloads

## Evidence

Screenshots in this folder show:
- Azure CLI context validation
- Resource group enumeration
- VM inventory and power state filtering
- Cost-aware decision-making (deallocated VMs)
- Final audit-style output

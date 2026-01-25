# EX1 — Azure Portal: Manual Deployment & Visibility (Ops View)

## Scenario (real-world / global remote)
You’re the on-call cloud admin supporting a distributed team across multiple time zones. A service owner reports degraded performance, and you need to quickly validate what was deployed, confirm resource state, and verify recent changes — all using the Azure Portal as the fastest “single pane of glass” before you automate anything.

## Goal
Demonstrate day-to-day operational visibility and one-off resource actions using the Azure Portal:
- Create and validate resources
- Confirm deployment success
- Review auditability via Activity Log
- Build a lightweight “Ops View” dashboard for fast status checks

## What I did (Portal)
- Created / validated a resource group (`rg-az104-week1`)
- Deployed a Storage Account (manual deployment flow)
- Deployed a Linux VM (wizard-based creation)
- Stopped (deallocated) the VM after validation
- Reviewed **Activity Log** events for traceability
- Built a dashboard (“AZ 104 Week 1 - Ops View”) for quick visibility

## Evidence (Screenshots)
- `ex1-03-rg-az104-week1.png` — Resource group overview
- `ex1-04.png` — Deployment completion confirmation
- `ex1-01-activity-log.png` — Activity Log showing create/update/deallocate operations
- `ex1-02-dashboard.png` — Ops dashboard view
- `ex1-05-vm-stopped.png` — VM stopped (deallocated) state verification

## Admin takeaway
The Azure Portal is perfect for fast triage, validation, and one-off operational tasks — especially when you’re responding to incidents from anywhere. But anything repeatable should move toward automation (CLI/PowerShell/IaC) to reduce human error and create

# Exercise 6 — Self-Service Password Reset (SSPR) + Governance Controls

## Purpose
Implement a real-world Identity & Access Management (IAM) control that reduces helpdesk password reset tickets while maintaining secure identity verification. This exercise demonstrates how to roll out SSPR safely using a phased, group-based approach.

## Scenario
A global organization with users across **Americas / EMEA / APAC** needs password resets to be self-service (not dependent on IT), but the rollout must be controlled and auditable.

## Objectives
- Enable SSPR for a **pilot security group** (example: `grp-sspr-pilot`)
- Configure required **authentication methods** for password reset
- Document a phased rollout strategy: **Pilot → Americas → EMEA → APAC**
- Capture user communication points for adoption and support readiness

## Implementation Summary (Portal)
1. Create a pilot security group: `grp-sspr-pilot`
2. Enable SSPR for **Selected** users/groups (pilot first)
3. Configure authentication methods required for reset (based on tenant options)
4. Validate user impact (registration prompt / registration status if visible)
5. Document rollout phases and user comms



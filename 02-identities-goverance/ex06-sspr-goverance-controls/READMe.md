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

## Rollout Approach (Phased)
- **Phase 1:** Pilot group (`grp-sspr-pilot`) — validate user experience + support process
- **Phase 2:** Americas — expand to regional ops/users after pilot success
- **Phase 3:** EMEA — expand with compliance + comms alignment
- **Phase 4:** APAC — expand with time zone support coverage and adoption tracking

## User Communication (Example)
- “You’ll be prompted to register security info for Self-Service Password Reset. Registration is required to reset your password without IT support.”
- “If you do not register, password resets may take longer and require helpdesk verification.”

## Evidence (Screenshots)
Place screenshots in: `./screenshots/`

- `ex06-01-sspr-enabled-selected-group.png`  
  *Shows SSPR enabled for the pilot group (Selected users)*

- `ex06-02-auth-methods-configuration.png`  
  *Shows reset authentication methods configuration*

- `ex06-03-user-registration-prompt.png`  
  *Shows user registration prompt or registration experience (if visible)*

## Teach-Back
SSPR is an IAM operational control that:
- Reduces helpdesk workload and password reset downtime
- Improves security by enforcing verified identity methods for reset
- Scales globally using **group-based enablement** and phased rollout


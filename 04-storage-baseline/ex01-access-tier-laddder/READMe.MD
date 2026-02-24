# EX01 — Access Tier Ladder (Hot vs Cool vs Cold vs Archive)

## 1) Purpose (Business Outcome)
- **Scenario:** A global remote-first org stores media (frequent reads), business reports (monthly reads), audit logs (rare reads), and legal archives (near-zero reads). The team must optimize cost without breaking latency expectations or compliance retention.
- **Outcome:** Correctly assign blob access tiers based on **access frequency + retention minimums + latency**.
- **Why it matters:** Wrong tier selection causes **unexpected billing spikes** (transactions + early deletion penalties) and **performance complaints** (Archive rehydration delay).

---

## 2) Architecture (Where it fits in the platform)
- **Platform Link:** ../../00-AZURE-SPINE/01-Architecture.md
- **This exercise adds/changes:**
  - Creates a **GPv2 (Standard)** storage account and a single container for tier testing
  - Uploads sample blobs and applies tier changes
  - Captures tier logic + validation evidence
- **Scope:** Resource Group

**Proposed design intent (storage behavior):**
- **Hot:** frequent access (media landing zone)
- **Cool:** infrequent access (monthly reports)
- **Cold:** rare access (audit logs with retention)
- **Archive:** long-term legal archive (rehydration required)

---

## 3) Identity & Access (No confusion allowed)
- **Authentication:** Microsoft Entra ID
- **Authorization (RBAC):**
  - `Storage Blob Data Contributor` (scope: RG or Storage Account)
- **Token/Secret Used:** None (no Shared Key / no SAS for primary workflow)
- **Audit Evidence to capture:** Activity Log entries for storage account updates (and any tier-related configuration events)

> **Spine Link:** ../../00-AZURE-SPINE/02-Access-Control.md

---

## 4) Security Baseline (What is prevented by default)
- **Public exposure:** Denied (no anonymous blob access)
- **Network controls:** None (baseline for this exercise; Private Endpoint comes later)
- **Data protection:**
  - Secure transfer required = **Enabled**
  - Encryption at rest = **Enabled (PMK default)**

> **Spine Link:** ../../00-AZURE-SPINE/03-Security-Baseline.md

---

## 5) Operations / Day-2 (How this is run)
### What breaks first
- Archive reads fail expectations due to **rehydration latency**
- Early deletion / tier changes trigger **minimum retention penalties**
- Transaction volume increases cost for Cool/Cold workloads if access pattern changes

### How to detect
- Azure Monitor metrics:
  - **Transactions**
  - **Egress**
  - **Availability**
- Cost signals:
  - Cost analysis shows spikes correlated to reads + tier transitions

### How to fix (high-level)
- Reclassify data by access pattern (Hot/Cool/Cold/Archive)
- Adjust lifecycle thresholds to prevent frequent manual tier changes
- Educate stakeholders: Archive is not “cheap hot storage”

> **Spine Link:** ../../00-AZURE-SPINE/04-Operations-Day2.md

---

## 6) Cost & Governance (How you avoid spend stupidity)
### Primary cost drivers
- Storage capacity (GB-month)
- Read/write operations (transactions)
- Data retrieval / rehydration behavior (Archive)
- Tier transitions (one-time charges)

### Controls used (Week 4 baseline)
- Tags: `env=lab`, `dataClass=<hot|cool|cold|archive>`
- Lifecycle policy (introduced in EX03; referenced here as next step)

### Shutdown / cleanup plan
- Delete test blobs
- Delete storage account or entire RG when done

> **Spine Link:** ../../00-AZURE-SPINE/05-Cost-Governance.md

---

## 7) Automation (Manual is temporary)
- **Deployment method (today):** Portal (validation-first)
- **What is automated today:** None
- **Next automation step:** Deploy storage account via **Bicep** with:
  - secure transfer required
  - public access disabled
  - tagging standards

> **Spine Link:** ../../00-AZURE-SPINE/06-Automation-IaC.md

---

## 8) Validation (Proof, not vibes)

### Tests performed
1. Upload 4 blobs and assign tiers:
   - `media-hot.zip` → Hot
   - `report-cool.pdf` → Cool
   - `audit-cold.csv` → Cold
   - `legal-archive.bin` → Archive
2. Change tier on one blob (Hot → Cool) and confirm tier property updates
3. Attempt to “use” the Archive blob expectation: document rehydration requirement and latency implication (no pretending)

### Evidence captured (required)
- `01-before.png` — container view before tier changes
- `02-tier-config.png` — blob properties showing tier settings
- `03-after.png` — after tier changes reflected
- `04-audit.png` — activity log / config evidence

> **Spine Link:** ../../00-AZURE-SPINE/07-Validation-Evidence.md

---

## 9) Risks & Tradeoffs (Director-level thinking)
- **Risk:** Placing frequently accessed data in Cool/Cold reduces storage cost but increases transaction and retrieval cost.
- **Mitigation:** Use lifecycle automation + periodic access review to keep tiers aligned to real usage.
- **Tradeoff:** Archive dramatically reduces storage cost but introduces operational latency (rehydration) and cannot be treated as interactive storage.

> **Spine Link:** ../../00-AZURE-SPINE/08-Risk-Register.md

---

## 10) Interview Talk Track (30 seconds)
“I built a tiering model for Azure Blob Storage based on access frequency, minimum retention, and latency. Hot is for frequent reads, Cool/Cold reduce storage cost but increase access costs, and Archive is long-term retention with rehydration latency. Operationally, I monitor transactions and cost trends and use lifecycle policies to keep data in the right tier automatically.”

> **Spine Link:** ../../00-AZURE-SPINE/09-Interview-Talk-Track.md

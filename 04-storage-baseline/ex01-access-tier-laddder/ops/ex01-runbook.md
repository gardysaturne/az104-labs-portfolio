# EX01 – Access Tier Ladder Runbook

## Scenario
Unexpected billing spike after tier transitions.

---

## Detection

1. Go to Cost Analysis → Filter by Storage Account
2. Check transaction volume increase
3. Review Activity Log for tier changes
4. Validate lifecycle policy configuration

---

## Root Causes

- Frequent reads from Cool/Cold
- Rehydration from Archive
- Manual tier oscillation
- Incorrect lifecycle thresholds

---

## Immediate Fix

- Move frequently accessed blobs back to Hot
- Adjust lifecycle rule timing
- Inform stakeholders of Archive latency behavior

---

## Prevention

- Implement lifecycle policy
- Tag dataClass
- Monthly cost review
- Avoid manual tier flipping

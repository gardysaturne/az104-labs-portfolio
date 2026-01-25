## Exercise 3 — PowerShell: Object-Based Resource Management

**Goal:** Demonstrate Azure administration using PowerShell cmdlets and object-based output instead of text parsing.

### What I did (PowerShell)

- Authenticated to Azure using `Connect-AzAccount`
- Verified active subscription and tenant context
- Enumerated Azure resources using `Get-AzResource`
- Scoped resource queries to a specific resource group
- Inspected returned objects using `Get-Member`
- Managed VM state using PowerShell (`Stop-AzVM`)

### Evidence (Screenshots)

See `/EX3-PowerShell/` for:

- Authentication and context verification
- Resource enumeration (subscription-wide and scoped)
- Object model inspection via `Get-Member`
- VM lifecycle management via PowerShell

### Admin takeaway

Azure PowerShell returns **rich objects**, not plain text.  
This enables filtering, inspection, and automation without brittle string parsing.

Understanding object properties and pipelines is more important than memorizing syntax — a core concept tested on the AZ-104 exam.

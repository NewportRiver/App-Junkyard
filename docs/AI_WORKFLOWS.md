# AI Workers and Control Boundaries

## Proposed roles

### Salvage Inspector

**Input:** Quarantined source package and ownership documentation.  
**Checks:** Archive integrity, provenance, license mapping, potential infringement, secrets/PII, malware indicators, software bill of materials (SBOM), dependency vulnerabilities, build and smoke tests.  
**Output:** Dated inspection JSON and buyer-friendly summary; recommendation to reject, quarantine, or review for listing.

### AI Mechanic

**Input:** Approved isolated work item with clear scope and source license.  
**Tasks:** Dependency modernization, bug fixes, isolated builds, tests, documentation, salvage extraction.  
**Output:** Patch, tests, provenance and license carry-forward, changelog, candidate repaired package.

### Yard Manager

**Input:** Approved inspection reports, listing drafts, inventory statuses.  
**Tasks:** Search metadata, queue prioritization, draft product copy and estimated grade/pricing, low-stock alerts, service intake.  
**Output:** Proposed listings and work queue for human approval.

## Control rules

1. All incoming archives begin in **quarantine** with no credentials or unrestricted network access.
2. Do not execute untrusted build scripts on host machines; use disposable sandboxing and narrowly scoped time/resource limits.
3. Secrets and customer data must be removed and confirmed absent before any sale.
4. An AI worker cannot declare legal title or publish a new listing without a human decision and retained evidence.
5. AI-generated code changes must go through tests and independent review before release.
6. Agents never receive production payment secrets or unrestricted marketplace payout privileges.
7. Record item ID, task ID, input hash, model/tool version, decision rationale, test results, reviewer, and publication status.
8. Do not allow external tools to ingest private customer code absent explicit authorization.

## State machine

`SUBMITTED -> QUARANTINED -> INSPECTED -> RIGHTS_REVIEW -> HUMAN_APPROVED -> LISTED -> SOLD/ARCHIVED`

An item may transition to `REJECTED` from any review stage, or back to `QUARANTINED` if a new security/ownership issue is discovered.

## Useful metrics

- Inspection cost and duration per package.
- Percentage rejected for rights and security issues.
- Average days from intake to publishable asset.
- Rebuild success and regression rate.
- Download/fulfillment support contacts per order.
- Conversion and gross margin per grade/category.

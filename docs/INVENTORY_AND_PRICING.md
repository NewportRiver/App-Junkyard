# Inventory, Grading, and Pricing

## Allowed source categories

- Code and assets wholly owned by the company.
- Third-party software licensed **specifically for the intended sale/distribution model**.
- Consigned software for which the seller is verified as authorized to license or transfer rights.
- Eligible open-source components, with license notices, attribution, source delivery, and other applicable obligations met.

**Not enough:** An app-store listing, a public GitHub repository, a copy found online, or possession of a binary does not by itself prove a right to sell the source or represent it as exclusive.

## Condition grading checklist

- **A — Runs Great:** Build reproducible in stated environment, documented launch verification, no unresolved *known critical* blocker, license reviewed.
- **B — Mechanic's Special:** Reproducible partial build or functional core; known repair backlog prominently listed.
- **C — Parts Only:** Modules or assets extracted and packaged, with boundaries and dependencies identified; full app does not need to run.
- **D — Totaled:** Code/data damaged or nonfunctional; content description and salvage feasibility disclosed; never represent as runnable.
- **R — Restored Classic:** Repaired from earlier condition, provenance preserved, tests rerun, repair changelog available.

A grade must not substitute for vulnerability findings, support promises, or license eligibility. Quarantine and reject any item with unresolved high-severity security or ownership risk rather than listing it in a low grade.

## Illustrative price hypotheses (USD)

| Grade | Price hypothesis |
|---|---:|
| A | $25–$99 |
| B | $5–$25 |
| C | $1–$15 |
| D | Free–$5 |
| R | $49–$199 |

Test each price band against inspection time, payment costs, storage/bandwidth, support overhead, rights cost, and customer value.

## Listing metadata (minimum)

- Unique inventory ID, name, category, platform, runtime/language, archive version.
- Source of supply, seller/rights-holder identity, documentary proof of rights (private).
- License type, redistribution permissions, exclusivity scope, dependencies, obligations.
- Condition grade, build status, test environment and date, known issues.
- Security scan status, critical findings and resolution state, secrets check result.
- Download content description, package checksum, docs link, screenshots.
- Price, taxes/fees disclosures, refund terms, and supported delivery format.
- Approval state, human reviewer and approval timestamp.

## Example catalog

The included JSON examples are **fictional placeholders**, not available listings. They intentionally have `published: false`, `is_demo: true`, and `rights_verified: false`.

# 🛠️ App Junkyard

**Software salvage, repair, and reuse.**  
*A Newport River Company venture concept.*

> **Working tagline:** "Don't build it. Salvage it."

## What is App Junkyard?

An online software-salvage marketplace where legitimate owners and rights-holders can sell or consign abandoned applications, unfinished prototypes, games, components, and unused source code. Customers can buy inexpensive, clearly graded starter projects or individual parts, and optionally hire an AI-assisted repair service.

Think of a pull-a-part automotive yard for software: **inspect it, tag it, strip it for parts, fix it, and put it back to work.**

**Status:** Ideation / planning. Pricing, policies, and marketplace mechanics are hypotheses, not live offers.

## Business model

1. **Intake:** Owners submit their own code or properly licensed material, with documentation of their right to transfer or license it.
2. **Inspection:** Automated and human checks document build status, vulnerabilities, dependencies, licensing, secrets, and known issues.
3. **Salvage:** Package whole apps, templates, modules, themes, graphics, game systems, and other transferable components.
4. **Sales:** Direct inventory sales; later, commission-based consignments and seller listings.
5. **Service:** Paid repairs, modernization, integration, and installation support.

## Salvage grades (proposed)

| Grade | Label | Meaning | Illustrative starting price |
|---|---|---|---|
| A | Runs Great | Builds and passes a defined smoke test | $25–$99 |
| B | Mechanic's Special | Functional foundation; documented issues | $5–$25 |
| C | Parts Only | Extracted/usable modules or assets | $1–$15 |
| D | Totaled | Nonworking software with recoverable value | Free–$5 |
| R | Restored Classic | Previously broken; repaired and validated | $49–$199 |

*Prices are examples for testing customer interest, not research-backed market rates. A grade describes inspection findings, not a security or fitness guarantee.*

## AI-assisted workforce (future)

- **Salvage Inspector:** License and provenance triage, malware/secret scanning, dependency inventory, build checks, and condition reports.
- **AI Mechanic:** Isolated repairs, dependency updates, component extraction, test generation, and documentation.
- **Yard Manager:** Catalog administration, listing drafts, queue priority, proposed prices, seller communication, and inventory history.

AI agents **recommend**, while humans approve license decisions, publication, code access, payouts, and external distribution.

## MVP direction

**HTML-first responsive web application** with a small *company-owned inventory* before inviting third-party sellers. Initial experience: searchable salvage listings, inspection report, license terms, digital delivery after payment, and repair-service request. A playful digital junkyard theme can differentiate the marketplace without obscuring key disclosures.

### Proposed files

- [`docs/CONCEPT.md`](docs/CONCEPT.md) — mission, audience, revenue, product positioning
- [`docs/MVP_PLAN.md`](docs/MVP_PLAN.md) — MVP scope, workflows and acceptance criteria
- [`docs/DEVELOPMENT_PLAN.md`](docs/DEVELOPMENT_PLAN.md) — detailed architecture, milestones, API sketch, QA, launch gates and first sprint
- [`docs/INVENTORY_AND_PRICING.md`](docs/INVENTORY_AND_PRICING.md) — grading, catalog metadata, example listings
- [`docs/AI_WORKFLOWS.md`](docs/AI_WORKFLOWS.md) — agent duties, approvals, safeguards
- [`docs/RIGHTS_AND_SECURITY.md`](docs/RIGHTS_AND_SECURITY.md) — rights, licenses, safety, buyer disclosures
- [`data/example-inventory.json`](data/example-inventory.json) — fictitious catalog examples; not for sale

## Boundaries

**No scraping proprietary applications for resale, no redistribution without rights, and no release of code containing private keys, tokens, personal data, or unresolved malicious behavior.** Marketplace terms, payment handling, taxes, refund policies, intellectual property rights, and open-source compliance require legal review before commercial launch.

## Planning and publishing

See [`FEATURES.md`](FEATURES.md), [`CHANGELOG.md`](CHANGELOG.md), and [`PUBLISH_TO_GITHUB.md`](PUBLISH_TO_GITHUB.md). This project is documentation and sample data only; no app has been built or launched.

## Ownership and licensing

Concept prepared for **Newport River Company**. This planning repository does **not** grant a blanket license to reuse its code, documentation, trademarks, or any third-party assets. Individual salvage listings must specify their own verified rights and licenses.

# App Junkyard — HTML-First MVP Plan

## Objective

Prove that developers will browse, trust, and purchase low-cost software salvage accompanied by clear condition and rights information.

## Phase 0 — Validate before construction

- Interview 10+ potential buyers/sellers and note which categories they would pay for.
- Define rights-transfer contracts and terms with legal counsel.
- Source 5–10 company-owned or expressly authorized demonstration assets.
- Document what "tested" means for each asset type, including expected environment.
- Estimate storage, payment processing, support, and refund economics.

## Phase 1 — Catalog-only MVP

**Suggested stack:** responsive HTML/CSS/TypeScript frontend; simple API and relational DB once persistence is needed. Use static fixtures for the first prototype. Avoid premature framework or vendor commitments.

### Pages

1. **Home:** Brand, search, price bands, featured salvage aisles.
2. **Inventory:** Filters for platform, category, condition grade, license, price, language, and last verified date.
3. **Item details:** Screenshots, source tree summary, running instructions, condition report, dependency list, known issues, rights and delivery terms.
4. **Repair shop:** Request estimate form (no automatic guarantee of repair).
5. **Admin intake:** Private listing drafts, ownership evidence, inspection checklist, approve/reject/publish.

### Minimum behaviors

- Search/filter catalog without displaying fake inventory as live products.
- Show the complete applicable license and rights before purchase.
- Provide secure buyer access to a verified package after payment; never expose private direct-download URLs publicly.
- Attach a package checksum and version to every sold artifact.
- Record sales, authorization, fulfillment, and refund events without retaining payment card data.
- Require human approval before publishing or fulfilling any AI-generated listing.

## Phase 2 — Real transaction pilot

- Integrate a reputable hosted payment checkout, relying on its native checkout and compliance capabilities.
- Secure private digital download delivery, expiring access, and abuse protections.
- Manual service fulfillment and basic order support.
- Test refunds, takedowns, disputes, and license documentation end to end.

## Phase 3 — Seller marketplace

- Seller verification, proof of ownership, payouts, fraud detection, listing agreements, and dispute workflows.
- Consignment commissions and optional paid inspections.
- Moderation and abuse reporting; repeat infringement controls.

## Acceptance criteria for first production pilot

- Every public listing has documented rights, an inspection timestamp, grade explanation, supported environment, known issues, and clear delivery contents.
- No package contains confirmed secrets, undisclosed personal data, or detected malicious content.
- Files are stored privately and downloadable only by authorized buyers.
- The full test order lifecycle, including refunds and revocations where applicable, is exercised.
- At least one independent buyer can follow the listed setup instructions on a fresh environment.

## Backlog seeds

- AJ-001: Brand landing page and static searchable catalog.
- AJ-002: Define canonical inventory and provenance data model.
- AJ-003: Create inspector report and quarantine pipeline.
- AJ-004: Build private admin review queue.
- AJ-005: Design hosted checkout and secure fulfillment.
- AJ-006: Publish license/disclosure and dispute policy drafts for legal review.
- AJ-007: Add repair quote requests and service workflows.

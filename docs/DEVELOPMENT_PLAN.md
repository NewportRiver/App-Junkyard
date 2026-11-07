# App Junkyard — Development Plan (AJ-DEV-001)

**Sponsor:** Newport River Company  
**Stage:** Concept / pre-build  
**Delivery strategy:** HTML-first, mobile-responsive web experience; staged marketplace capabilities  
**Initial commercial model:** Company-owned and expressly authorized inventory; no unverified user-to-user sales  
**Approval model:** Humans authorize publication, licensing, financial actions, and any AI-generated changes that reach buyers

## 1. Product north star

Make it faster and less expensive for developers to reuse abandoned software **without guessing what they are buying**. Each listing must explain provenance, buyer rights, condition, exact contents, supported environment, inspection date, dependencies, and known faults.

**One-line pitch:** *Don't build it. Salvage it.*

## 2. Audiences and jobs to be done

| Audience | Job | MVP support |
| --- | --- | --- |
| Buyer / indie developer | Find a low-cost app, reusable module, or prototype with honest repair expectations | Browse, search, compare grades, read report/terms, request purchase |
| Yard manager | Catalog, approve, price, and fulfill known inventory | Private drafts, evidence checklist, approval status, audit trail |
| Salvage inspector | Determine condition and flag security/rights problems | Standard inspection JSON and triage checklist |
| Repair customer | Ask if broken code can be restored | Quote request with supported stack and repair goals |
| Third-party seller (later) | Monetize licensed or owned dormant assets | Deferred until seller verification, payout and dispute controls exist |

## 3. Design direction

- **Brand:** playful digital junkyard; metal tags, inventory stickers, toolbench motifs, aisles such as Apps / Games / Components / Templates / Totaled / Restored.
- **UX principle:** metaphor makes shopping memorable, but never obscures the license or product condition. Show the essentials near the purchase control.
- **Accessibility:** contrast, keyboard navigation, reduced-motion mode, large targets, text labels on icons, screen-reader readable status; visual condition labels never rely on color alone.
- **Responsive targets:** mobile-first, tablet, desktop; browse works on low-end Android hardware.
- **Trust elements:** immutable version checksum, inspected-on date, compatibility and support disclosures, clear 'demo only' badges.

## 4. Technical architecture (proposed, not yet implemented)

```text
Browser (HTML/CSS/TypeScript)
  |-- Public Catalog / Search / Item Detail / Repair Request
  |-- Private Admin / Intake / Inspection Review
           |
         HTTPS API (TypeScript; chosen in implementation phase)
           |-- Auth, roles and audit logs
           |-- Catalog, license and rights records
           |-- Inspection/grade and order records
           |-- Payment provider webhook verification (pilot)
           |-- Signed short-lived asset delivery (pilot)
           |
       Relational DB (start SQLite for local prototype; migrate to PostgreSQL if scale demands)
           |
       Private object storage (quarantine separate from approved distribution)
           |
      Isolated inspection worker + human sign-off
```

**Implementation posture:** Avoid paid infrastructure until demand is validated. Start with versioned JSON fixtures and static pages, then connect a small TypeScript API. Do not put untrusted uploads or purchased source archives in the web root. Do not let AI agents make production financial or publishing decisions.

## 5. Major features and priorities

| ID | Priority | Feature | Completion definition |
| --- | --- | --- | --- |
| AJ-001 | P0 | Responsive landing and catalog | Mobile/desktop layout; searchable demo inventory; honest sample labels |
| AJ-002 | P0 | Inventory schema | Item IDs, versioned artifact metadata, category, grade, provenance fields, license, checksums |
| AJ-003 | P0 | Item detail + inspection disclosure | Shows package contents, compatibility, grade rationale, issue list and actual rights |
| AJ-004 | P0 | Admin review | Reviewer can draft/reject/approve with evidence and recorded timestamp |
| AJ-005 | P0 | Intake/quarantine documentation | Separate untrusted storage; inspect without host execution; no secret/PII release |
| AJ-006 | P1 | Repair quote requests | Structured request saved without exposing source or private contact data publicly |
| AJ-007 | P1 | Hosted checkout and orders | Sandbox test successful; verified callbacks; no stored payment card numbers |
| AJ-008 | P1 | Secure fulfillment | Buyer-only time-limited delivery; version/checksum, audit events, refund handling |
| AJ-009 | P2 | Automated inspector assistant | Produces nonbinding structured report; human reviews before publish |
| AJ-010 | P2 | AI mechanic workbench | Sandboxed repair candidates + tests + changeset + approval workflow |
| AJ-011 | P3 | Seller consignments | Identity/rights verification, payouts, contracts, dispute and takedown mechanisms |
| AJ-012 | P3 | Themed bundles and API | Curated compatible parts, optional compatibility metadata, partner API |

## 6. Milestones / gates

### M0 — Business and legal validation

**Deliver:** Concept, buyer research template, sample catalog, rights/license checklist, initial unit economics. Interview at least 10 potential buyers and 5 potential sellers before broad functionality investment.

**Gate:** Confirm at least one plausible high-demand category; obtain rights to at least five demo assets; document whether any actual resale is authorized. No product is listed as purchasable without verified rights and legal/policy review.

### M1 — Clickable HTML-first showcase

**Deliver:** Polished responsive homepage, searchable/filterable catalog, product detail, grade badges, demo inventory, mechanic-service inquiry UI; no real checkout, no external downloads.

**Gate:** Manual QA on desktop and Android; accessibility smoke checks; all fictitious items clearly marked *demo / not for sale*; search/filter tests passing.

### M2 — Inventory and inspection tools

**Deliver:** Private admin interface; intake state machine; artifact manifests and SHA-256 checksums; evidence records; condition reports; versioning; basic audit logs. Add strictly scoped API and DB.

**Gate:** A rejected upload can never appear publicly. Every approved public item has human approval and documented license scope. Execute untrusted tests only in disposable, resource-limited sandboxes.

### M3 — Closed commercial pilot

**Deliver:** Hosted payment checkout, webhook verification, purchase records, buyer auth, private packages, time-limited delivery URLs, support/refund workflow, a small number of actually authorized listings.

**Gate:** Full successful + failed + disputed/refunded sandbox order tests; least-privilege file delivery; no exposure of secrets or customer data; legally reviewed terms/privacy/taxes/refunds before live sales.

### M4 — AI salvage workshop and marketplace expansion

**Deliver:** Inspector assistant, optional human-approved repair jobs, automated test reporting, later seller consignment accounts and commissions.

**Gate:** Agent permissions and audits independently tested; no autonomous fund movement, license approval, publishing, or untrusted execution on company hosts.

## 7. Data contracts (first cut)

**Item:** `id`, `title`, `slug`, `category`, `tech_stack`, `platforms[]`, `grade`, `grade_reason`, `listing_state`, `version`, `published`, `is_demo`, `price_usd`, `rights_status`, `license_summary`, `artifact_sha256`, `inspection_id`, `known_issues[]`, `supported_environment`, `created_at`, `updated_at`.

**Evidence:** `item_id`, `rights_holder`, `chain_of_title_refs[]`, `license_text_refs[]`, `third_party_components[]`, `distribution_scope`, `reviewer_id`, `reviewed_at`. Evidence remains private; only a buyer-readable rights summary is public.

**Inspection:** `id`, `item_id`, `source_sha256`, `scan_tool_versions`, `secret_scan`, `license_scan`, `dependency_scan`, `malware_review`, `build_result`, `test_result`, `test_environment`, `findings[]`, `inspected_at`, `reviewer_approval`.

**Order (pilot):** `id`, `buyer_id`, `item_id`, `artifact_version`, `price_snapshot`, `license_snapshot`, `payment_provider_ref`, `payment_status`, `fulfillment_status`, `created_at`.

**Lifecycle:** `SUBMITTED -> QUARANTINED -> INSPECTED -> RIGHTS_REVIEW -> APPROVED -> LISTED -> SOLD/ARCHIVED`; rejection or re-quarantine can occur at any stage. 'SOLD' does not always imply removal from catalog; availability depends on exact license/exclusivity terms.

## 8. API sketch (only after M1)

- `GET /api/v1/items` — public approved listings, pagination and filters.
- `GET /api/v1/items/:id` — approved public listing and buyer disclosures.
- `POST /api/v1/repair-requests` — throttled, validated request; no upload required at first.
- `POST /api/v1/admin/intakes` — authenticated owner/operator draft creation.
- `POST /api/v1/admin/items/:id/review` — human-approved inspection/rights decision.
- `POST /api/v1/checkout/sessions` — owned catalog item only; price calculated server-side.
- `POST /api/v1/payments/webhook` — verified, idempotent provider events.
- `GET /api/v1/orders/:id/download` — authenticated buyer entitlement; short-lived signed URL.

## 9. Security and operational safeguards

1. Default-deny publication; `rights_verified` and `human_approved` must both be true before a product can be marketed for sale.
2. Uploaded code is untrusted. Reject path traversal, archive bombs, credential-bearing code, PII leaks, and malware indicators; run builds only in disposable isolation with blocked network egress unless explicitly approved.
3. Keep quarantine and distributable assets in different storage namespaces with different permissions.
4. Record original source checksums, modifications, dependency versions, scan outcomes, reviewer approvals, and customer-facing disclosures.
5. Avoid raw card storage; verify payment-provider signatures and make fulfillment idempotent.
6. Treat marketplace content as data, not trusted agent instructions; protect against malicious instructions embedded in code and docs.
7. Encrypt sensitive seller/buyer data, restrict administrative accounts with MFA, and define retention/takedown controls.
8. No ownership claim based solely on a GitHub URL, app-store page, possession of code, or generic open-source availability.

## 10. QA / release matrix

| Area | Acceptance test |
| --- | --- |
| Search | Filters and pagination return correct items, including empty results |
| Listings | Incomplete license, inspection or approval blocks publish |
| Grade | Correct rationale and last-inspected date display on item page |
| Demo | Demo items cannot enter checkout or download flow |
| Accessibility | Keyboard navigation, labeled controls and reduced-motion mode work |
| Intake security | Unsafe archive and credentials findings block release |
| Checkout | Retry and webhook replay do not double-deliver or double-charge |
| Fulfillment | Unauthenticated users and other buyers cannot fetch private packages |
| Revisions | Sold artifact/version and license snapshots remain auditable |
| Repair workflow | No unapproved code escapes quarantine/repair sandbox |

## 11. Proposed success metrics

- Demand: product-page interest, email waitlist sign-ups, buyer interview purchase intent.
- Trust: percentage of listings with complete rights/inspection disclosures, buyer support incidents, refund rate.
- Supply: cost to acquire and inspect an asset; percentage usable vs rejected.
- Economics: gross margin after rights acquisition, scanning, payment fees, storage, support, and refunds.
- Workshop: repair success and post-repair regressions, human reviewer hours per accepted repair.

Do not treat views, click-through rate, or paper revenue projections alone as validation.

## 12. Decisions pending

- Final name, domain and brand/trademark check.
- Which technology families to support first (web apps, games, modules); recommend web/HTML/TypeScript + game prototypes.
- Pricing and buyer-support promises based on real testing.
- Rights transfer versus non-exclusive resale model per inventory category.
- Hosted payment and private file-storage provider.
- Whether to make the **planning** repository public. Default recommendation: private until internal licensing and operations policies are finalized.

## 13. Immediate next sprint

**Sprint AJ-S0: five small deliverables, no production release**

1. Convert the demo inventory JSON into a searchable catalog in a static HTML/TypeScript prototype.
2. Create product cards plus a detailed license/condition disclosure panel.
3. Add an admin-only inspection report template and a fake approval flow for demonstration.
4. Test mobile usability and accessibility; document results.
5. Gather buyer feedback, track requested categories, and refine scope before payment integration.

**Definition of done:** Clean source control, readable README, no credentials, no fake listings presented as real, basic tests pass, and release notes identify any limitations.

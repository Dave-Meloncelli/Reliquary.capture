# Reliquary Ingest: requirements and gate matrix

**Review draft 0.2 | Baseline v1.0-RC | 19 October 2026**

Q1–Q33 and Q25A/Q26A are now sourced. See S1–S7 and precedence
in DESIGN_SPECIFICATION.md. S6 is the original signed-in
conversation; S7 includes the approved final consolidated baseline
and the complete reconstructed register/classification table.
Earlier summary-only gaps are closed, not reclassified as Later.

Each requirement below has an ID, source/evidence, class/gate,
implementation dependency and named acceptance contract. Source
and dependency lines apply to every requirement in their Q section.
Acceptance tests specify both observable good and bad outcomes.
No test is represented as executed.

Evidence: “approved/direct” means attributed to the available
original owner decisions and recorded registers, not independent
technical verification. S7's reconstructed table is used alongside
its approved final baseline and S6 original records.
Numerical budgets, technologies and unselected mechanisms remain
implementation proposals; they do not inherit design approval.

Gate allocation follows the recovered consolidated scope:
Gate 1 is a small technical proof, Gate 2 completes production
safeguards, Later retains deferred capabilities. Safeguards apply
before any path needing them is enabled. A Gate 2 feature can stay
disabled in Gate 1; it cannot run there with weaker safety.

Gate 1 requirements continue into Gate 2.
No accepted major capability is wholly DROPPED.

## Q1: Conditional collector identity

Source/evidence: S6 original Q1; S7 final baseline and register; approved/direct.
Dependency: Claims, Evidence.

**R01-1 | MVP / Gate 1**
Disclose uncertainty; reject unsupported collector claims and sibling-inherited identity. Preserve copy evidence; conflicts require review.
Acceptance: AT-01, AT-02, AT-08.

## Q2: Human reference promotion

Source/evidence: S6 original Q2; S7 final baseline and register; approved/direct.
Dependency: Catalogue, Claims, authorisation.

**R02-1 | MVP / Gate 2**
Keep provisional and verified references separate; authorised human promotion needs evidence/audit; version verified changes. Inventory approval is a different permission; references cannot silently overwrite contrary copy evidence.
Acceptance: AT-03, AT-13, AT-21.

## Q3: Exception-driven condition

Source/evidence: S6 original Q3; S7 final baseline and register; approved/direct.
Dependency: Capture, templates, Evidence.

**R03-1 | MVP / Gate 1 basic; Gate 2 full**
Assess grade, defects, completeness and photos at capture. Routine consistent cases avoid a second inspection; material concerns block bulk approval. AI flags but cannot override; audit corrections. Keep bibliographic, collector and physical-condition confidence distinct.
Acceptance: AT-04, AT-12.

## Q4: Shopify inventory authority

Source/evidence: S6 original Q4; S7 final baseline and register; approved/direct.
Dependency: Commerce, event reconciliation.

**R04-1 | MVP / Gate 1**
Provision only the approved initial copy state; Shopify owns availability thereafter. Metadata sync never resets quantity; duplicate/delayed/missed events reconcile. Sold stock cannot resurrect; returns need inspection. Discrepancies create exceptions.
Acceptance: AT-06, AT-07, AT-14, AT-29.

## Q5: Hybrid iOS capture durability

Source/evidence: S6 original Q5; S7 final baseline and register; approved/direct.
Dependency: Capture, persistent client storage.

**R05-1 | MVP / Gate 2; simpler Gate 1 capture allowed**
Native camera/storage/recovery with shared web logic/contracts. Persist photos and condition before Locally Saved; show actual Uploading/Server Verified/Attention Required. Capture continues during sync; unsynced is not backed up; iOS background completion is not guaranteed. Framework TBD.
Acceptance: AT-05, AT-15, AT-43.

## Q6: Physical location and fulfilment

Source/evidence: S6 original Q6; S7 final baseline and register; approved/direct.
Dependency: Capture, Commerce, location history.

**R06-1 | MVP / Gate 2**
Permanent copy SKU; select/scan location, carry forward until changed, hierarchical shelf/bin locations, audited movement. Staging is allowed; final location required before publication. Fulfilment identifies copy/location; physical and Shopify locations stay distinct.
Acceptance: AT-01, AT-16.

## Q7: Versioned product templates

Source/evidence: S6 original Q7; S7 final baseline and register; approved/direct.
Dependency: Catalogue, Capture, condition policy.

**R07-1 | MVP / Gate 1 basic; Gate 2 full**
Books, boxed sets and simple accessories use one pipeline and versioned type-specific evidence/metadata/completeness policies. Box/contents grading and component manifest; sealed items stay closed with unverified internals disclosed.
Acceptance: AT-04, AT-17.

**R07-2 | LATER / after Gate 2**
TCG, LEGO and specialist grading remain extension scope.
Acceptance: AT-17.

## Q8: Adaptive evidence capture

Source/evidence: S6 original Q8; S7 final baseline and register; approved/direct.
Dependency: Capture, local identification.

**R08-1 | MVP / Gate 2**
Minimum template photos, rapid local checks, explained in-hand extra-image requests and deferral as visible desktop exceptions. Distinguish missing/inconclusive/contradictory evidence, retain copy/SKU links and never block capture on slow enrichment or network.
Acceptance: AT-05, AT-18.

## Q9: Policy-qualified bulk approval

Source/evidence: S6 original Q9; S7 final baseline and register; approved/direct.
Dependency: Claims policy, review, approval ledger.

**R09-1 | MVP / Gate 2**
Explicit human batch authority; show eligible/excluded records and exceptions. Revalidate each current item on server. Preserve operator/time/listing revision/evidence/policy version; material changes invalidate approval. AI confidence is not authority. Q31 limits resulting automation to draft preparation.
Acceptance: AT-12, AT-13, AT-29, AT-42.

## Q10: Tiered processing and spending controls

Source/evidence: S6 original Q10; S7 final baseline and register; approved/direct.
Dependency: Worker, provider adapters, cost ledger.

**R10-1 | MVP / Gate 2; controls required whenever enrichment is enabled**
Barcode/OCR/internal matching before AI; reuse verified knowledge, deduplicate identical requests, capture asynchronously and recover from outage. Track per-item/batch/operation/provider cost; enforce caps/escalation and authorise expensive over-budget reruns. Q27 local-first boundary prevails.
Acceptance: AT-09, AT-21, AT-31.

## Q11: Existing-stock reconciliation

Source/evidence: S6 original Q11; S7 final baseline and register; approved/direct.
Dependency: Commerce, stable copy identifiers.

**R11-1 | MVP / Gate 1 collision safety; Gate 2 full safeguards**
Check existing matches before creation; bibliography is not physical identity. Explicit confirmation for linking; preserve content, IDs, quantity and sales history. SKU conflicts/uncertain copy matches create exceptions; linking decisions are audited and safely reversible.
Acceptance: AT-01, AT-06, AT-32.

**R11-2 | LATER / after Gate 2**
Complete historical catalogue migration; it is not a launch prerequisite.
Acceptance: AT-32, AT-40.

## Q12: Separate authenticity hold

Source/evidence: S6 original Q12; S7 final baseline and register; approved/direct.
Dependency: Claims, reviewer authorisation.

**R12-1 | MVP / Gate 2; Gate 1 never asserts unsupported claims**
Printing uncertainty is not counterfeit evidence. Credible misrepresentation/unauthorised-copy concern holds approval/publication. Specialist disposition records evidence/actor/time/outcome; AI cannot declare counterfeit or release hold. New contrary evidence reopens verification; C-06 governs live protection.
Acceptance: AT-02, AT-12, AT-19, AT-33.

## Q13: Independent catalogue and managed infrastructure

Source/evidence: S6 original Q13; S7 final baseline and register; approved/direct.
Dependency: Catalogue, Evidence, managed hosting.

**R13-1 | MVP / Gate 1 foundation**
Own persistent catalogue/media/history independently of Shopify. Separate commerce adapter; select providers on cost/security/accessibility/portability/maintenance, with measurable BOM costs. No adaptation to the pre-existing implementation.
Acceptance: AT-23, AT-34.

## Q14: Portable exports and rehearsed restore

Source/evidence: S6 original Q14; S7 final baseline and register; approved/direct.
Dependency: Database, object store, manifests.

**R14-1 | MVP / Gate 2**
Versioned export of canonical records/relationships/media/provenance; stable internal IDs separate from external IDs. Checksums/manifests verify exports. Scheduled backups, documented dependencies/manual steps and at least one end-to-end restore before production.
Acceptance: AT-22, AT-34.

**R14-2 | LATER / after Gate 2**
Full multi-cloud deployment automation is not required by the MVP.
Acceptance: AT-34.

## Q15: Commercial product groups and copy variants

Source/evidence: S6 original Q15; S7 final baseline and register; approved/direct.
Dependency: Catalogue, Commerce.

**R15-1 | MVP / Gate 1**
C-01 supersedes production-group splitting. One title + content edition + release product; each copy its own variant/SKU/price/media/condition/quantity. Printings and PoD can coexist; different releases split. Product membership never proves copy identity.
Acceptance: AT-01, AT-02, AT-07, AT-29.

## Q16: Dynamic selected-copy presentation

Source/evidence: S6 original Q16; S7 final baseline and register; approved/direct.
Dependency: Theme, Commerce, channel inventory.

**R16-1 | MVP / Gate 2**
Selected photos/grade/defects/completeness/production identity/price/SKU/availability remain correct through product, cart, checkout and fulfilment. Shared bibliography only at product level. Accessible keyboard/screen-reader use; missing copy data prevents ambiguous purchase. Verify theme and variant capacity; per-variant feeds/condition.
Acceptance: AT-08, AT-25, AT-29, AT-35.

## Q17: Historical inventory and commercial events

Source/evidence: S6 original Q17; S7 final baseline and register; approved/direct.
Dependency: Evidence, Commerce restricted schemas.

**R17-1 | MVP / Gate 2 foundation**
Retain copy/evidence and acquisition/listing/sale/return/retirement history, variant/order links and known costs/prices/discounts/fees/freight without rewriting events. Personal records restricted. C-07 keeps sold variants unavailable, hidden and out of feeds.
Acceptance: AT-07, AT-21, AT-25, AT-36, AT-41.

**R17-2 | LATER / after Gate 2**
Advanced profitability/ageing/demand intelligence, valuation, forecasting and purchasing recommendations.
Acceptance: AT-36, AT-37.

## Q18: Customer demand and supply register

Source/evidence: S6 original Q18; S7 final baseline and register; approved/direct.
Dependency: Deferred Demand module, consent.

**R18-1 | LATER / after Gate 2**
Customer wanted items and acceptable substitutes; staff purchasing/trade-in/collection leads; distinguish demand, potential supply and completed transactions. Explicit requests outrank passive signals. Catalogue linkage independent of live products; consent/preferences before notifications, no stock/price/procurement promise. Passive tracking/predictive scoring outside MVP.
Acceptance: AT-37.

## Q19: Isolated versioned data providers

Source/evidence: S6 original Q19; S7 final baseline and register; approved/direct.
Dependency: Claims, provider register, adapters.

**R19-1 | MVP / Gate 2**
Versioned replaceable Data Provider Interface; attributed candidates with version/time/usage restrictions, never direct canonical mutation. Human reference promotion; optional-provider outage preserves local/manual operation.
Acceptance: AT-03, AT-09, AT-31, AT-38.

**R19-2 | LATER / separately authorised independent comparison**
Support independent/provider-assisted/comparative evaluation against identical inputs and independent truth. Preserve design/tests before access to the existing dataset; agreement alone is not correctness.
Acceptance: AT-31, AT-38.

## Q20: Central claims and independent corroboration

Source/evidence: S6 original Q20; S7 final baseline and register; approved/direct.
Dependency: Claims, Evidence, all output adapters.

**R20-1 | MVP / Gate 1 safety; Gate 2 full**
Material claim value/scope/source/evidence/confidence/status; preserve conflicts and common upstream/derived-source dependencies. No circular or dependent-source corroboration. One versioned policy asserts/attributes/qualifies/withholds/escalates across every output, including back-cover summaries. Human overrides audited; no unclassified bypass.
Acceptance: AT-02, AT-08, AT-13, AT-38.

## Q21: Continuous evidence-policy impact

Source/evidence: S6 original Q21; S7 final baseline and register; approved/direct.
Dependency: Claims, Commerce, exception centre.

**R21-1 | MVP / Gate 2 limited safety**
Evidence/policy changes identify affected copies and customer surfaces; preserve historical representations. New material assertions/live content corrections need humans. C-06 alone permits automatic one-copy emergency suspension. Handle stale caches and failed updates as unresolved exposure with critical alert.
Acceptance: AT-19, AT-21, AT-39.

## Q22: Controlled regrouping and migration

Source/evidence: S6 original Q22; S7 final baseline and register; approved/direct.
Dependency: Commerce, claims holds, order state.

**R22-1 | MVP / Gate 2 manual safety**
Hold affected copy and route identity conflicts/manual resolution. Permanent identity/history and transactions preserved; orders/reservations require resolution; at most one sellable representation. Printing/PoD-only change does not move product under C-01.
Acceptance: AT-19, AT-32, AT-40.

**R22-2 | LATER / after Gate 2**
Full migration with authorised destination/reason, recoverable multi-step actions, reconciliation and safe compensation/rollback without rewriting completed transactions.
Acceptance: AT-40.

## Q23: Post-sale accountability

Source/evidence: S6 original Q23; S7 final baseline and register; approved/direct.
Dependency: Immutable sale snapshots, Commerce.

**R23-1 | MVP / Gate 2 foundation**
Preserve exact represented title/edition/printing/status/condition/photos/text/price and order links. Later corrections never rewrite sale evidence; allow affected-sale identification and manual escalation.
Acceptance: AT-21, AT-36, AT-41.

**R23-2 | LATER / after Gate 2**
Full prioritised customer-impact case workflow, contact history and human-authorised refund/return/replacement/compensation with access/retention and applicable obligations assessed.
Acceptance: AT-41.

## Q24: Optional acquisition cost and lot allocation

Source/evidence: S6 original Q24; S7 final baseline and register; approved/direct.
Dependency: Restricted commercial model.

**R24-1 | MVP / Gate 2 nullable foundation**
Unknown cost is not zero; separate known/allocated/estimated/unknown and permit capture/pricing/approval without full cost. Preserve extensible cost provenance and adjustment hooks.
Acceptance: AT-36.

**R24-2 | LATER / after Gate 2**
Detailed acquisition-lot costs/expenses, retrospective item allocation, adjustment audit, no double counting and methodology-preserving financial analytics.
Acceptance: AT-36.

## Q25: Durable Shopify outage queue

Source/evidence: S6 original Q25; S7 final baseline and register; approved/direct.
Dependency: Capture, Commerce, database jobs.

**R25-1 | MVP / Gate 1**
Capture/enrichment/review/pricing/approval continue during Shopify outage. Durable retries survive outage/auth/rate limits. Resume only after current evidence/claims/condition/price/approval/inventory revalidation. Actual states distinguish approved, awaiting, draft work, confirmed and attention. Q31 forbids resumed jobs publishing live; no success before remote confirmation.
Acceptance: AT-05, AT-06, AT-13, AT-42.

## Q26: Central operational exceptions

Source/evidence: S3/S4 original Q26; S7 consolidated baseline; approved/direct.
Dependency: Commerce, web/worker notifications.

**R26-1 | MVP / Gate 2 minimal centre**
Material failures create prioritised cases with severity/copies/customer-financial exposure/owner/cause/attempts/state. Critical alerts and escalation; routine queue, safe retries/audit/history. Delivery, acknowledgement, confirmed protection and resolution are separate.
Acceptance: AT-19, AT-23, AT-39, AT-42.

## Q27: Local-first purpose-limited privacy

Source/evidence: S3/S4 original Q27; S7 consolidated baseline; approved/direct.
Dependency: Restricted roles, disclosure gateway.

**R27-1 | MVP / Gate 1 privacy; Gate 2 full**
Four data classes; local/internal/OCR/matching first. Task allowlists, sanitised/cropped derivatives and no original access. Commercial/personal schemas structurally denied to provider execution. Provider register records terms/region/retention/no-training; audit field list/payload hash/outcome. Untrusted returns/OCR; stop rather than weaken. Explicit exceptions audited.
Acceptance: AT-08, AT-09, AT-10, AT-11, AT-28.

## Q28: Location-free immutable image evidence

Source/evidence: S3/S4 original Q28; S7 consolidated baseline; approved/direct.
Dependency: Capture boundary, object store.

**R28-1 | MVP / Gate 1**
No GPS capture; strip imports before persistence while preserving pixels, then hash canonical file. Restricted/audited originals, retake supersession and derivative lineage. Ordinary retention indefinite; personal-content restrictions and C-05 authorised tombstones/deletion apply across restored/public derivatives.
Acceptance: AT-10, AT-20, AT-21, AT-22.

## Q29: Versioned consequential processing

Source/evidence: S3/S4 original Q29; S7 consolidated baseline; approved/direct.
Dependency: Evidence, processing-run ledger.

**R29-1 | MVP / Gate 2; preserve enabled Gate 1 provenance**
Immutable run ID/input hashes/references/time/model/version/config/output/claims/review; reruns append, old approvals retain exact evidence. Disagreements reconcile; human corrections audited. Temporary cache expiry allowed; provenance is not guaranteed identical AI results.
Acceptance: AT-03, AT-13, AT-21.

## Q30: Four-component modular monolith

Source/evidence: S3/S4 original Q30; S7 consolidated baseline; approved/direct.
Dependency: All modules, database queue.

**R30-1 | MVP / Gate 1 foundation; Gate 2 operations**
Web, one worker, database, object store; no broker. Owned tables/interfaces and enforced import/tests. Restricted schema roles; provider worker cannot acquire elevated credentials. Managed backups, single-command/screen operations, rehearsed recovery and proactive daily health. One-book vertical slice first.
Acceptance: AT-11, AT-22, AT-23.

## Q31: Two release gates and owner publication

Source/evidence: S3/S4 original Q31; S7 consolidated baseline; approved/direct.
Dependency: Fixture manifests, gate validator.

**R31-1 | Delivery governance / both gates**
Original five-book dev-store proof and retry/sale tests; Gate 2 50-book/timing/fault/restore/privacy/evidence/channel/writer proof. Owner alone publishes, including under live parents. Every criterion has nonempty named known-good/known-bad evidence; no vacuous pass.
Acceptance: AT-01, AT-06, AT-07, AT-08, AT-11, AT-22, AT-25, AT-26, AT-29, AT-30.

## Q32: Fixed dual budget and stop/reset rules

Source/evidence: S3/S4 original Q32; S7 consolidated baseline; approved/direct.
Dependency: PLAN.md, owner decision ledger.

**R32-1 | Delivery governance / before Gate 1 and continuing**
Effort and attention estimates/confidence; one 50% checkpoint; ordered owner-approved cuts; never-cut invariants; one owner reset, second miss full re-plan; evidence of estimate error. Reduced gate has own name and exact omissions.
Acceptance: AT-27, AT-28.

## Q33: Design closure

Source/evidence: S3/S4 original Q33; S7 consolidated baseline; approved/direct.
Dependency: Source register, reviewed baseline.

**R33-1 | Design governance / completed before planning**
Classify requirements/gates and reconcile contradictions before owner baseline approval. Approval recorded; this reconciliation preserves it and distinguishes new implementation/estimate proposals.
Acceptance: AT-30.

## Amendments, audit resolutions and derived safety constraint

### Q25A: Dual first-class capture

Source/evidence: S6 capture amendment; S7 approved baseline; approved/direct.
Dependency: Capture, iOS client, desktop import/device adapter.
Class/gate: MVP / Gate 2; simpler Gate 1 input permitted.
Requirement: Equal mobile/desktop paths share canonical copy/evidence contracts and can hand off without duplicate creation. Device/time/slot provenance, accessible keyboard/spoken feedback and continuous capture. Existing CZUR Lens with import fallback; direct-driver support must be tested; no required new camera purchase.
Acceptance: AT-05, AT-15, AT-43.

### Q26A: Controlled Shopify CLI

Source/evidence: S3/S6 Q26A; S7 approved baseline; approved/direct.
Dependency: Isolated dev store, scoped identities, configuration history.
Class/gate: MVP tooling / Gate 1; deployment controls at Gate 2.
Requirement: Official CLI supports development/theme/API diagnostics; runtime uses supported APIs, not CLI jobs. Version app/theme config, separate production credentials, keep secrets out of GitHub, require explicit production-change approval, validation and rollback.
Acceptance: AT-24.

### C-01: Commercial grouping and independent copy evidence

Source/evidence: S4 owner resolution; S7 approved baseline; approved/direct.
Dependency: Catalogue, Commerce, copy claims.
Class/gate: MVP / Gate 1.
Requirement: Title + edition + release groups; originals/reprints/PoD/unverified printings can share a product. Different releases split. Copy evidence never inherited from group/sibling; supersedes Q15 production grouping.
Acceptance: AT-01, AT-02, AT-40.

### C-02: Variant outputs and structured data

Source/evidence: S4 owner resolution; S7 approved baseline; approved/direct.
Dependency: Theme, feed/structured-data adapters.
Class/gate: MVP / Gate 2.
Requirement: Correct variant condition/price/photos/production; product text/data only shared facts. No one-copy condition generalised to product.
Acceptance: AT-08, AT-25, AT-35.

### C-03: All Shopify writers assessed

Source/evidence: S4 owner resolution; S7 approved baseline; approved/direct.
Dependency: Writer access inventory, field ownership/conflict assessment.
Class/gate: MVP / Gate 2.
Requirement: Include every product/variant writer, including book-metafield apps; any unassessed writer blocks deployment. Assessment follows preservation of independent design and appropriate access authority.
Acceptance: AT-26.

### C-04: Fail-closed privacy

Source/evidence: S4 owner resolution; S7 approved baseline; approved/direct.
Dependency: Database credentials, provider execution boundary.
Class/gate: MVP / Gate 1 and continuing.
Requirement: Stop for reassessment if four components cannot demonstrate commercial/personal denial. No indirect access, inherited credential or waived security assertion.
Acceptance: AT-09, AT-11, AT-28.

### C-05: Authorised deletion and tombstone

Source/evidence: S4 owner resolution; S7 approved baseline; approved/direct.
Dependency: Evidence storage, restrictions and restore.
Class/gate: MVP / Gate 2 completion; before earlier privacy-exception use.
Requirement: Immutability forbids silent rewrite, not authorised removal/restriction. Tombstone contains only hash/reason/authoriser/time, never sensitive content.
Acceptance: AT-20, AT-22.

### C-06: One-copy emergency suspension

Source/evidence: S4 explicit owner selection; S7 approved baseline; approved/direct.
Dependency: Variant/location identity, concurrency, reconciliation, critical cases.
Class/gate: MVP / Gate 2 before live exposure.
Requirement: Verify correct copy/variant and Shopify inventory location/current state; concurrency protection and final state confirmation. Only availability to zero; no content/price/publication/sibling change. Critical attempted/failed/confirmed states; no automatic restoration, owner approval required.
Acceptance: AT-19, AT-39.

### C-07: Retain sold variants

Source/evidence: S4 owner resolution; S7 approved baseline; approved/direct.
Dependency: Commerce, theme and feed filtering.
Class/gate: MVP / Gate 1 stock history; Gate 2 picker/feeds.
Requirement: Keep unavailable variant/history; hide in active picker and exclude from sellable feeds. Automatic retirement remains Later.
Acceptance: AT-07, AT-25, AT-36.

### C-08: Named reduced gates

Source/evidence: S4 owner resolution; S7 approved baseline; approved/direct.
Dependency: Budget/approval/evidence register.
Class/gate: Delivery governance / Gate 1 and continuing.
Requirement: Each approved reduction has distinct gate name/version, exact omission and actual test outcomes. No relabelled original pass.
Acceptance: AT-27, AT-28.

### SAFETY-LIVE-PARENT: Unapproved copy under a live title

Source/evidence: Q31 owner policy; S5 clarification; S7; derived enforcement of approved authority.
Dependency: Copy staging mechanism, full channel inventory.
Class/gate: MVP / Gate 1 mandatory negative; Gate 2 every channel.
Requirement: An unapproved new copy remains unavailable on every enabled storefront/channel/feed/direct-cart path despite its live parent. Mechanism is proposed/TBD until proven; no guessed API flag counts as evidence.
Acceptance: AT-29.

## Coverage and review result

33 numbered decisions, Q25A, Q26A and all eight audit resolutions
are represented. No source-absent or unallocated placeholders remain.
The live-parent safeguard is traced separately.
All requirement groups name dependencies and acceptance tests.

Earlier Q15 production splits and Q21 autonomous content changes are
superseded, not alternative implementation choices.
Later scope is explicit: full migration, demand/notifications,
trade-in/collection workflow, advanced analytics, full case workflow,
detailed cost allocation, sold-variant retirement and new categories.
Foundational history, identity, nullable commercial records and
manual safety holds remain allocated to Gate 2 where specified.

Remaining review: numerical budgets/attention, timing aggregation,
provider/framework choices and proof of technical feasibility.
Source recovery is not implementation approval or a gate pass.

# Reliquary Ingest: preserved baseline source

**Source extract | Baseline v1.0-RC | Preserved 19 October 2026**

Purpose: keep the approved consolidated design and its decision
register independently readable for Dave, Josh and future agents.
This is selected design source material, not a complete chat export.

Origin: the owner-supplied updated fullchat.md (S7).
Original file SHA-256:
704bc76d0c24cb5818d53cd9a6dce984510cc8582dffaf1357b908b0f8a257dd.

Section A preserves the consolidated baseline followed by the
owner's explicit approval as supplied. Section B preserves the
originating agent's reconstructed decision register and classification
table. Section B is labelled reconstruction; it does not become a
verbatim Q1–Q33 transcript merely by being saved here.

The signed-in original App Capture Concept decision records were
also checked directly (S6), as described in DESIGN_SPECIFICATION.md.
Its original Q1–Q25 records supply detail beyond the reconstruction.
The preserved approved final baseline takes precedence over earlier
question wording. C-01, Q31, C-06 and C-05 supersessions are explicit
in the specification and matrix.

Historical permission/status statements within the extract describe
the source conversation. They do not override the owner's subsequent
authority to upload the review package and place it on main.
Reading this source is not implementation or deployment approval.

No credentials, sign-in screens, unrelated chat navigation, existing
implementation or proprietary dataset are included.

## A. Consolidated baseline and explicit owner approval

~~~text
Grill Me final audit C-06: I choose NARROW PROTECTIVE ACTION: emergency suspension of one copy's availability with critical alert and owner-controlled restoration. Record C-06, then prepare the final consolidated design summary for my approval before PLAN.md and BOM.md.
C-06 accepted — Grill Me audit closed
Reliquary Ingest
Final Consolidated Design Baseline · Version 1.0-RC · 19 October 2026

We've completed the Grill Me question loop and resolved all eight findings from the contradiction audit.

The design is ready for your approval. This is a design baseline, not an implementation approval or a claim that the system has been built.

1. Final audit decision: C-06
Decision: NARROW PROTECTIVE ACTION

Reliquary Ingest may suspend the availability of one specific physical copy when a defined critical risk is detected.

This is a narrowly authorised exception to our owner-controlled Shopify publishing policy.

The application:

May set the affected Shopify variant's available quantity to zero following a qualifying emergency trigger.

Must verify the correct variant, Shopify inventory location and current inventory state before acting.

Must use appropriate concurrency protections and reconcile the final Shopify state.

Must not change sibling variants, product descriptions, prices or publication status.

Must immediately raise a critical operational exception identifying the affected copy, cause and attempted action.

Must distinguish a confirmed suspension from an attempted or failed suspension.

Must not restore stock automatically. Only you may approve restoration.

Must preserve the evidence and audit trail supporting the intervention.

If Shopify is unavailable or the suspension cannot be confirmed, the incident remains critical and unresolved.

A queued protective action cannot be treated as successful merely because the worker accepted it.

2. Approved-direction architecture
Hybrid iOS

Native camera and resilient local capture

Desktop / CZUR

Document-camera capture and import fallback

Reliquary modular application

Capture · Catalogue · Claims · Evidence · Commerce · Demand

Desktop pricing · Condition review · Bulk approval · Operational exceptions

Managed database

Canonical records · Restricted schemas · Durable jobs

Object storage

Immutable evidence · Sanitised derivatives

One background worker

Local-first enrichment · Database queue · Provider gateway

Shopify

Shared products · Individual-copy variants · Draft-only creation · Owner publishing

The backend deployment ceiling remains four components: one web application, one worker, one database and one object store.

The iOS client and desktop capture hardware are clients of this architecture, not additional backend services.

3. Canonical product and inventory model
This is the most important revision from the original design.

A Shopify product represents a title, content edition and release. A Shopify variant represents one physical copy.

Shopify product

Player's Handbook — Standard Release

Shared bibliographic description

Copy 001

Original · First printing

Own SKU · Price · Images · Condition

Copy 002

Original · Later printing

Own SKU · Price · Images · Condition

Copy 003

PoD reproduction

Own SKU · Price · Images · Condition

Copy 004

Printing unverified

Own SKU · Price · Images · Condition

Different printings, including PoD copies, can belong to the same Shopify product when they represent the same edition and release.

Different releases, such as limited editions or materially different cover-art releases, receive separate products.

Product membership is never evidence of production identity.

Each physical copy retains independent evidence for printing, production status, condition, completeness, provenance and authenticity.

Customer-facing variant selection must update the correct copy's details. Shopping feeds must carry copy-specific condition and price information, and product-level structured data cannot assert a condition belonging to only one copy.

Sold variants remain historically linked but unavailable, hidden from the active copy picker and excluded from saleable feeds.

4. Operational workflow
1

Capture

iPhone or desktop CZUR workflow. Photograph the item, record condition and completeness, assign storage location and preserve immutable location-free evidence.

2

Identify and enrich

Internal catalogue, OCR and local matching first. External providers only when needed, through purpose-limited disclosure controls.

3

Evaluate evidence

Preserve competing claims, source dependencies and uncertainty. Central publication policy determines permissible assertions.

4

Price and review

Desktop pricing, exception-driven verification and policy-qualified bulk approval. Collector-sensitive exceptions receive individual review.

5

Create Shopify draft

Create or update the appropriate product group and physical-copy variant. Validate photos, pricing, identity and inventory without making the listing live.

6

Owner publication and lifecycle

You publish through an authorised workflow. Shopify owns inventory availability. Reliquary retains the physical-copy, evidence and commercial history.

5. Safety and authority boundaries
Operation

Authority

AI proposes book identification

Automated

AI proposes production classification

Automated candidate only

Promote a verified reference

Authorised human

Condition assessment

Capture operator, with exception verification

Selling price

Human reviewer

Bulk approve qualifying drafts

Authorised reviewer

Create Shopify draft

Automated after approval

Publish to live storefront

Owner

Suspend one copy in defined emergency

Automated, narrowly authorised

Restore suspended copy

Owner

Change material published claim

Human-approved correction

Resolve commercial or customer remediation

Authorised human

The emergency suspension policy does not grant general inventory-management authority to the application.

Only the identified physical-copy variant may be made unavailable, with verified Shopify state and a critical alert. A failure to verify suspension remains an unresolved critical incident.

6. Evidence, privacy and provider independence
The design retains these non-negotiable principles:

Original evidence: Location metadata removed at acquisition; original pixels retained, hashed and protected against silent alteration.

Processing history: Consequential OCR and AI runs versioned with their inputs, tools, configurations and outcomes.

Claims: Source provenance, genuinely independent corroboration and recorded human verification.

Public output: Central policy enforcement for product descriptions, metafields, structured data, feeds and other enabled publishing surfaces.

External processing: Local-first, allowlisted disclosure, sanitised media and auditable provider access.

Sensitive information: Commercial and personal records isolated through restricted database credentials.

Privacy deletion: Authorised removal or restriction leaves a non-sensitive audit tombstone.

Existing system independence: External datasets operate through isolated adapters and cannot directly modify the canonical catalogue.

No inspection or adoption of the existing Reliquary implementation is part of this approved-direction design.

7. Release gates
Gate 1 — Technical proof
Development store
Five deliberately challenging books: modern ISBN, pre-ISBN TSR stock code, boxed set, PoD and second physical copy.

Every item must reach an accurate Shopify draft. Forced retries must not create duplicates, and a simulated sale must affect only the correct copy.

A fixed effort budget and owner-attention budget are established before implementation. One 50% checkpoint and the approved scope-cut ladder govern recovery if the estimate proves inadequate.

Gate 2 — Production MVP
Release qualification
Fifty books processed end to end, measured desktop review effort against the two-minute target, fault injection with zero duplicate sellable copies, successful backup restoration, verified privacy isolation and complete publication-policy tests.

Every mandatory gate test must pass with known-good data and demonstrably fail with known-bad data.

Shopify app-write permissions and customer-facing output integrations must be inventoried and assessed before production deployment.

Neither gate authorises autonomous live publication.

8. Delivery constraints
The implementation plan must incorporate the following commitments.

Vertical slice first: One real book traverses the entire system before individual modules are expanded.

Fixed infrastructure ceiling: Four backend components; deviations require recorded justification.

Database-backed jobs: No separate message broker for the MVP.

Minimal operator workload: Routine operation must not require infrastructure administration.

Two budgets: Build effort and your own attention, both estimated with confidence.

One checkpoint: At 50% of the Gate 1 budget.

One authorised reset: A second miss requires full replanning.

Scope-cut ladder: Enrichment, boxed-set test, adaptive capture, then review-interface sophistication, subject to your approval.

Non-negotiable safeguards: Draft-only publication, copy identity, duplicate prevention, honest claims, privacy isolation and valid positive/negative gate tests.

No technology purchase or deployment commitment is implied by design approval.

9. Deferred capabilities
We preserve the architecture for these capabilities without making their complete implementation part of the first production release:

Full historical Shopify catalogue migration.

Customer demand registration and automated wanted-item notifications.

Trade-in processing and collection-acquisition workflows.

Advanced business intelligence and valuation.

Automated purchasing recommendations.

Full customer-impact case management.

Automatic retirement of historical sold variants.

Expansion to TCG, LEGO and other collectible categories.

The necessary permanent identities, evidence records, transaction history and extension contracts will be established in the foundational architecture.

10. Final approval request
Design baseline approval
All eight audit findings have proposed resolutions, including your revised Shopify grouping policy and narrowly authorised emergency suspension.


Approve independent design baseline

Close Grill Me as design-approved. Authorise preparation of the canonical specification, requirement matrix, release-gate tests, PLAN.md and BOM.md for review.


Request a targeted correction

Keep the design in review and address a specific remaining issue before planning.

Grill Me exit

Decision: needs-more-grilling — final baseline awaiting explicit approval.

Next: plan-ready after approval.

Repository: 
Dave-Meloncelli/Reliquary.capture

Commit status: No design files have been committed yet.

Your approval will close the independent design phase. It will not authorise deployment, spending or changes to the production Shopify store.

I approve Reliquary Ingest Design Baseline v1.0-RC, including Q1–Q33, the capture and Shopify CLI amendments, my eight audit resolutions, and the Q32 delivery governance. Mark Grill Me design-approved and prepare the canonical specification, requirements matrix, acceptance test plan, PLAN.md and BOM.md in Reliquary.capture for my review before committing. Maintain independence from my existing implementation.
~~~

## B. Reconstructed register and recorded release classification

~~~text
RELIQUARY INGEST — RECOVERED DESIGN DECISION REGISTER
Document purpose: Restore design context missing from the Work conversation.

Project: Reliquary Ingest
Repository: Dave-Meloncelli/Reliquary.capture
Baseline: v1.0-RC
Design status: APPROVED
Planning status: AUTHORISED FOR DRAFT PREPARATION
GitHub commits: NOT AUTHORISED WITHOUT REVIEW

Source integrity
This register reconstructs the decisions recorded across the original Grill Me discussion.

It is a decision summary, not a verbatim transcript. Do not invent additional design requirements or treat missing implementation details as settled decisions.

The owner's later amendments and the eight final audit resolutions supersede conflicting earlier interpretations.

Maintain an independent architectural baseline. Do not inspect or adapt to the owner's pre-existing implementation or proprietary dataset before the independent design deliverables have been completed and preserved.

PART A — ORIGINAL GRILL ME DECISIONS
Q1 — Conditional collector identity
Allow approval of items whose exact printing or production method cannot yet be established, provided their uncertainty is clearly recorded and disclosed.

Never assert first printing, original production, rarity or other collector-sensitive claims without supporting evidence.

Credible authenticity conflicts require review.

Q2 — Reference record promotion
OCR, AI and reference datasets can propose provisional bibliographic and production records.

Only authorised humans can promote candidate records into trusted catalogue references.

Promotions require evidence, versioning and audit history.

Inventory listing approval is separate from authority over the reference catalogue.

Q3 — Exception-driven condition assessment
Capture operators record structured condition grades, defects, completeness and evidence photographs.

Routine consistent assessments proceed without unnecessary review.

Material defects, inconsistencies and missing evidence generate exceptions.

Policies vary by item type.

AI cannot silently override human condition assessments.

Q4 — Shopify inventory ownership
Reliquary creates and maintains its independent physical-copy records.

Shopify owns sellable inventory availability once the item is provisioned.

Sales, reservations, refunds and inventory adjustments require Shopify-aware reconciliation.

Metadata synchronisation must never accidentally reset sold inventory to quantity one.

Returned stock requires physical inspection before being made sellable again.

Q5 — Hybrid mobile capture
Use a hybrid iOS approach with shared web business logic and native access where required.

Support durable local image capture, upload recovery, offline continuity and truthful synchronisation status.

A desktop browser application shares the canonical workflow.

The precise mobile framework was not selected during Grill Me.

Q6 — Physical location at capture
Every physical copy receives a permanent internal identity and SKU.

A shelf, bin, box or equivalent physical location is recorded during capture.

Staging locations may be used temporarily, but a final location is required before publication.

Location changes must be auditable.

Physical storage locations are distinct from Shopify inventory locations.

Q7 — Item-type templates
Use one extensible ingestion pipeline with configurable templates for:

Individual books.

Boxed sets.

Simple accessories.

Templates define evidence, grading and completeness requirements.

Sealed items must be handled without requiring them to be opened.

The architecture should eventually accommodate TCG and LEGO without making those categories part of the initial release.

Q8 — Adaptive evidence capture
Require a minimum evidence set and use available identification signals to request additional photographs while the physical item is in hand.

Examples include copyright pages, stock codes, printing identifiers and condition defects.

Slow AI calls must not block continuous capture.

Operators may defer additional evidence and resolve it later.

The fixed-photo-checklist fallback remains permitted by the Q32 cut ladder.

Q9 — Policy-qualified bulk approval
Allow bulk approval for records that satisfy all applicable evidence, condition, pricing and collector-identity policies.

Exception cases and collector-sensitive conflicts require individual review.

Bulk approval must use the current record revision and policy version.

Approval records the responsible human, applicable checks and decision timestamp.

Approval of a listing does not confer authority to publish it live.

Q10 — Tiered AI and cost control
Use the least expensive sufficient identification method.

Prefer local/internal catalogue matching, ISBN and stock-code lookups, OCR and cached evidence before expensive external AI.

External processing is conditional and subject to budgets and provider policies.

Provider outages must not destroy capture progress.

Retain processing costs and provenance where relevant.

Q27 strengthens this decision: local processing is the default; external services are exceptions.

Q11 — Existing Shopify record reconciliation
Identify potential existing Shopify records before creating new commercial inventory.

A matching title does not establish that two records represent the same physical copy.

Linking to an existing copy or product requires deliberate reconciliation.

Do not silently overwrite existing records or modify stock quantities.

Final scope classification: Collision detection and SKU safety are MVP safeguards. The complete historical Shopify catalogue migration workflow is LATER.

Q12 — Authenticity gate
Separate ordinary printing uncertainty from credible evidence of misrepresentation or counterfeit goods.

An honestly labelled unknown printing may proceed.

Credible evidence of misrepresentation or unauthorised reproduction triggers a hold and authorised review.

Ordinary PoD production is not inherently suspicious.

Affected live listings may require protective inventory action, subject to the final C-06 decision.

Q13 — Independent catalogue and infrastructure
Reliquary owns its canonical catalogue, media, evidence and identity records.

Shopify is the commerce platform, not the sole catalogue authority.

Use managed infrastructure where appropriate, prioritising reliability, affordability and portability.

The pre-existing implementation must not influence the independent design exercise.

Q14 — Portability and restoration
Maintain versioned exports covering canonical records, identifiers, relationships, evidence and media.

Preserve integrity checks and restoration instructions.

Implement reliable backups and rehearse restoration before production release.

Avoid unnecessary multi-cloud infrastructure.

Q15 — Shopify product grouping
Original decision superseded by final audit resolution C-01.

The FINAL rule is:

One Shopify product represents a title, content edition and release.

One Shopify variant represents one physical copy.

Different printings of the same release may coexist as variants.

Original, reprint, PoD and printing-unverified copies may coexist under one product.

Different releases, including limited editions and materially different cover-art releases, receive separate products.

Production identity remains specific to each copy.

Product membership never establishes or corroborates printing identity.

Do not implement the earlier production-group-per-product interpretation.

Q16 — Dynamic copy-specific presentation
Selecting a Shopify variant must expose that specific copy's:

Photographs.

Condition grade.

Defects.

Completeness.

Production identity.

Price.

SKU.

Availability.

Product-level descriptions contain only shared facts.

Variant-specific information must be correct across product pages, checkout-related surfaces, structured data and supported shopping feeds.

Feeds must have copy-specific price and condition; product-level structured data must not misrepresent an individual copy.

Q17 — Historical inventory and intelligence
Preserve sold physical-copy records rather than deleting their commercial history.

Maintain stable references to variant, order, pricing, discounts and other transactional information.

Support later analysis of profitability, stock ageing, acquisition costs and demand.

Sold Shopify variants remain unavailable, are excluded from the active copy picker and are excluded from sellable feeds.

Automatic retirement of historical variants is deferred.

Scope: Historical identity and transaction foundations are MVP. Advanced intelligence is LATER.

Q18 — Demand register
The long-term architecture should support customer wanted-item requests, acceptable substitutes and staff-generated purchasing or trade-in leads.

Distinguish demand from available offers of supply.

Customer notifications require appropriate consent.

Do not promise automated procurement or fulfillment.

Scope: Full demand and trade-in workflows are LATER.

Q19 — Isolated data-provider interface
Existing proprietary datasets may later connect through versioned provider adapters.

External and internal provider outputs are candidates, not automatically trusted canonical facts.

Each candidate claim retains provenance.

Providers must not directly mutate canonical catalogue records.

The independent implementation should later be comparable to a dataset-assisted approach without adopting that implementation during the independent design phase.

Q20 — Central claims policy
Represent material bibliographic, printing, production and authenticity assertions as evidence-linked claims.

Record:

Claim value and scope.

Source and provenance.

Supporting and conflicting evidence.

Independent-source relationships.

Verification state.

Public-presentation eligibility.

Human overrides and audit history.

Duplicate references to the same underlying source do not constitute independent corroboration.

All public outputs must pass through centrally enforced claims and publication policy.

Provider output is never directly promoted to verified fact.

Q21 — Continuing published-policy enforcement
New material evidence may invalidate an existing approved claim.

The system must identify affected current listings and determine whether qualification, correction, protective inventory action or human review is needed.

Historical representations and approvals must remain auditable.

Failures to apply necessary changes generate operational exceptions.

Q31 and C-06 constrain automation: The app cannot autonomously publish or rewrite commercial claims. It may only perform the narrowly authorised one-copy emergency suspension.

Q22 — Controlled production reclassification
If evidence changes a copy's edition or release identity, migration between Shopify product groups must be controlled and auditable.

Preserve the physical-copy identifier, SKU, evidence and historical transaction links.

Avoid creating multiple sellable representations of the same copy.

Use idempotent operations with recovery or compensation.

Active orders require special handling.

Scope: Full automated migration is LATER. Gate 2 retains safe hold/manual-resolution controls.

Q23 — Post-sale customer-impact cases
Material identity or condition corrections after sale should be traceable to the historical representation shown to the purchaser.

The longer-term system should support customer-impact case management, prioritisation, contact records and authorised remediation.

Scope: Full case workflow is LATER. Historical order/listing evidence is retained in the MVP.

Q24 — Acquisition costs
Support lot-level acquisition costs, associated expenses and later allocation to individual copies.

Distinguish known, allocated, estimated and unknown costs.

Unknown cost must not silently become zero cost.

Cost adjustments require audit history.

Missing cost information must not unnecessarily prevent capture or listing.

Scope: Detailed allocation and financial analytics are LATER. Preserve nullable and extensible commercial data foundations.

Q25 — Queued Shopify integration
Capture, enrichment and review should continue during Shopify service failures.

Publishing operations are durable, retryable and idempotent.

After recovery, revalidate current inventory, policy, evidence revision, pricing and approval status before issuing updates.

No queued operation may claim success before Shopify confirms the intended state.

Q25A — Dual first-class capture
Both the hybrid iOS capture workflow and desktop capture using the existing CZUR Lens are first-class input methods.

Use device-independent capture records and a shared capture service.

Support moving between devices without duplicate physical-copy creation.

Record relevant device provenance.

If direct CZUR integration is unavailable, use an import-based fallback.

Do not require purchasing new camera hardware merely to begin.

Q26 — Operational exception centre
Implement a central operational exception centre for material failures, inconsistencies and recoverable incidents.

Cases record severity, impacted copies, commercial/customer exposure, responsible operator, attempts and resolution state.

Critical commercial risks generate urgent alerts.

Routine issues enter a prioritised queue.

Safe retries may be automated.

Human authorisation remains required where earlier decisions require it.

Unresolved critical cases remain visible and subject to escalation.

Q26A — Controlled Shopify CLI
The official Shopify CLI may be used for app/theme development, schema exploration and diagnostics.

Use the existing isolated Shopify development store.

Keep credentials least-privileged and outside the public repository.

Production changes require explicit approval and rollback procedures.

The runtime integrates through appropriate Shopify APIs, not by treating the CLI as a production job runner.

Q27 — Local-first, purpose-limited disclosure
Local processing is the default:

Internal catalogue and local lookup.

On-device or self-hosted OCR/image matching.

External providers only when local methods cannot answer sufficiently.

Provider access is deny-by-default and allowlisted for each specific task.

Four information classifications:

Public bibliographic data.

Copy evidence.

Commercial information.

Personal information.

Commercial and personal information must never be sent to external enrichment providers.

Sensitive classes require structural isolation and independent access permissions.

Sanitise externally disclosed images.

Maintain a provider register documenting purpose, permitted fields, retention, geographic processing, contractual controls and prohibition of training use.

Audit external calls by provider, purpose, allowed fields and payload hash.

Treat provider responses and OCR text as untrusted data, never instructions.

Exceptions require owner authorisation and audit history.

Applicable Australian privacy obligations must be assessed; the stricter internal privacy policy applies regardless of a possible legal exemption.

Q28 — Immutable location-free evidence
Retain canonical original photographs without location metadata.

For in-app photographs, generate location-free capture records.

For imports, strip GPS/location metadata before persistent storage.

Preserve image pixels, hash canonical originals with SHA-256 and prevent silent modification.

Retakes create new versions instead of overwriting the old evidence.

Generate derivatives for OCR, listings, analysis and external processing.

External providers never receive direct original-storage access.

Originals have restricted access.

Default ordinary evidence retention is indefinite, subject to privacy exceptions.

Images containing identifiable people, names, inscriptions or seller documents require additional handling.

Deletion or restriction leaves a tombstone recording hash, reason, authorisation and time without retaining sensitive content.

Q29 — Versioned consequential processing
Retain consequential OCR, AI and image-analysis processing runs.

Record processing-run identity, input hashes, tool/model version, meaningful configuration, outputs and review outcomes.

A re-run creates a new artefact rather than overwriting history.

Earlier claims and approvals retain references to their original supporting processing runs.

Temporary caches and redundant processing artefacts need not be retained indefinitely.

Versioned provenance does not guarantee bit-for-bit reproducibility of third-party AI.

Q30 — Modular monolith with fixed ceiling
Maximum MVP backend deployment shape:

One web application providing API, desktop bench and review screens.

One background worker process.

One database.

One object store.

No separate message broker; use database-backed jobs with appropriate locking, leases, retries and recovery.

Primary application modules:

Catalogue.

Claims.

Capture.

Evidence.

Commerce.

Demand.

Module boundaries must be enforced by interfaces, import rules and tests.

Commercial/personal information uses restricted schemas and roles.

External-enrichment execution must not possess credentials granting access to those sensitive records.

Use managed infrastructure and automatic backups.

Recovery should be a documented, rehearsed operator-friendly procedure.

Routine operation should be possible through one screen or simple command.

Health is delivered proactively through the exception centre and daily summary.

Build an end-to-end vertical slice before completing individual modules.

Q31 — Two release gates
Gate 1: Technical proof

Use five real shelf items in the existing isolated Shopify development store:

Modern book with ISBN.

Pre-ISBN TSR publication with stock code.

Boxed set with independent box and contents condition.

PoD copy.

Second physical copy of a previously captured title.

All must reach accurate Shopify drafts with approved condition, price and photos.

A forced retry must produce no duplicate.

A simulated sale must affect only the correct physical copy.

For the pre-ISBN item, correctly recording printing unverified is acceptable when evidence is insufficient. Guessing is not.

Gate 2: Production MVP

Fifty physical books processed end to end.

Measure desktop effort per listing against the two-minute target.

Fault injection for killed workers, failed uploads and repeated approvals.

Zero duplicate sellable copies.

Successful backup restoration.

Verified enrichment-worker isolation from personal/commercial data.

No unsupported first-printing claims.

No PoD market availability or pricing intelligence leaking into customer text, tags or feeds.

Variant-specific storefront/feed correctness.

Inventory of all installed Shopify apps with product-write permission; unassessed writers block deployment.

Publication rule: At both gates and after production release, the app only prepares drafts. The owner decides when a listing is made live.

Every gate check needs named automated positive and negative tests. Passing because the test found no applicable records is failure, not evidence of success.

Q32 — Dual-budget delivery governance
Estimate and track two budgets:

Build effort, expressed in agent sessions or human hours, with confidence estimates.

Owner attention, expressed in required decisions and approvals.

Set both before implementation.

Conduct one checkpoint at 50% of the Gate 1 build budget.

At that checkpoint report working functionality, missing functionality, actual spend and forecast completion.

If the forecast exceeds budget, propose reductions according to this ladder:

Replace automated enrichment with clearly identified manual data entry.

Reduce five test books to four, removing the boxed set first.

Replace adaptive capture with a fixed photo checklist.

Simplify desktop review to the most basic workable list.

Never cut:

Draft-only publication.

No duplicate Shopify products or variants on retry.

One distinct canonical identity per physical copy.

No unsupported claims.

Privacy isolation.

Positive/negative test requirements.

Only the owner may approve cuts or budget changes.

One reset is permitted. A second miss requires a complete replan.

Every reset records original assumptions, actual outcomes, estimate error and approval in an evidence log.

A reduced four-book Gate 1 is a separately identified, versioned gate variation; it must not be reported as passing the original five-book gate.

Q33 — Design closure
Close open-ended grilling.

Classify requirements by MVP, LATER or DROPPED and assign Gate 1, Gate 2 or later.

Resolve contradictions.

Present and obtain explicit consolidated-design approval before producing implementation plans and bills of materials.

The owner has completed this approval.

PART B — FINAL EIGHT AUDIT RESOLUTIONS
These override conflicting earlier interpretations.

C-01 — Commercial grouping, not evidential grouping
A Shopify product represents one title, edition and release.

A Shopify variant represents one physical copy.

Different printings, originals, reprints, PoD copies and printing-unverified copies may share a product when they belong to the same release.

Different releases, such as limited editions or materially different cover art, create distinct products.

Each copy establishes its own production identity from its own evidence.

Never infer a copy's production identity from its product or sibling variants.

This explicitly overrides the former production-group-per-product design.

C-02 — Variant-specific public information
Product-level text and structured data describe only shared characteristics.

Variant selection controls the copy's condition, completeness, images, price, SKU and production identity.

Shopping feeds must carry the relevant variant's own condition and price.

Do not let product-level structured data assert one copy's condition as if it applied to all copies.

C-03 — Shopify write-access inventory
Before Gate 2 production deployment, inventory all installed Shopify apps with product or variant write permissions.

At least one existing store app writes book metafields.

Any unassessed application capable of altering governed product data is a deployment blocker.

C-04 — Privacy enforcement
Commercial and personal data segregation must be enforceable through separate database permissions and credentials.

An enrichment execution path must not be able to retrieve those records, directly or indirectly.

If the four-component architecture cannot demonstrate this isolation, stop for architectural reassessment rather than weakening the security requirement.

C-05 — Evidence deletion and tombstones
Immutability means evidence is never silently rewritten.

It does not prevent authorised deletion or restriction where required.

Preserve only a non-sensitive tombstone containing the image hash, reason, authoriser and time.

Do not retain sensitive content in the tombstone.

C-06 — Narrow emergency protective action
This final decision is approved.

Reliquary may automatically set exactly one affected physical copy's available Shopify inventory to zero in a narrowly defined emergency, such as a credible authenticity concern or duplicate-sale risk.

It must:

Positively identify the correct variant and Shopify inventory location.

Apply appropriate concurrency protections.

Verify the resulting state.

Avoid editing product content, pricing, publication status or sibling variants.

Generate a critical operational exception.

Distinguish attempted, failed and confirmed suspension.

Never automatically restore the copy.

Only the owner may authorise restoration.

This is the sole approved automated protective exception to the general rule that the application does not control live publication.

C-07 — Sold variant retention
Sold variants stay historically linked in Shopify.

They remain unavailable, are hidden from active variant selection and are excluded from sellable shopping feeds.

Automatic deletion or retirement is deferred until its safety can be proven.

C-08 — Explicit reduced-gate versions
A reduced Gate 1 is not the original Gate 1.

Record the gate variation, omitted scope, owner approval and acceptance results separately.

Never relabel an unmet original gate as passed.

PART C — PREVIOUSLY AGREED REQUIREMENT CLASSIFICATION
These classifications are from the consolidated audit and should be carried into the requirements matrix, with the later audit resolutions applied.

Decision	Classification	Release allocation
Q1	MVP	Gate 1 minimum
Q2	MVP	Gate 2
Q3	MVP	Gate 1 basic; Gate 2 full
Q4	MVP	Gate 1
Q5	MVP	Gate 2; simpler Gate 1 capture permissible
Q6	MVP	Gate 2
Q7	MVP	Gate 1 basic; Gate 2 full
Q8	MVP	Gate 2
Q9	MVP	Gate 2
Q10	MVP	Gate 2
Q11	LATER full migration; MVP collision safety	Gate 1/2 safeguards; migration later
Q12	MVP	Gate 2
Q13	MVP	Gate 1 foundation
Q14	MVP	Gate 2
Q15, amended by C-01	MVP	Gate 1
Q16	MVP	Gate 2
Q17	MVP historical foundation; LATER analytics	Gate 2 foundation
Q18	LATER	After Gate 2
Q19	MVP	Gate 2
Q20	MVP	Gate 1 safety; Gate 2 full
Q21	MVP limited safety enforcement	Gate 2
Q22	LATER migration; MVP safety hold	Gate 2 manual safety
Q23	LATER cases; MVP transaction history	Gate 2 foundation
Q24	LATER allocation; MVP nullable foundation	Gate 2 foundation
Q25	MVP	Gate 1
Q25A	MVP	Gate 2 dual capture
Q26	MVP	Gate 2 minimal centre
Q26A	MVP tooling	Gate 1
Q27	MVP	Gate 1 privacy; Gate 2 full
Q28	MVP	Gate 1
Q29	MVP	Gate 2
Q30	MVP	Gate 1
Q31	Delivery governance	Both gates
Q32	Delivery governance	Before Gate 1 and throughout
Q33	Design governance	Completed before planning
No accepted major design capability was wholly DROPPED. Some are deliberately LATER or reduced to a foundational capability for Gate 2.
~~~

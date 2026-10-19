# Reliquary Ingest: canonical design specification

**Review draft 0.2 | Baseline v1.0-RC | 19 October 2026**

Target repository: Dave-Meloncelli/Reliquary.capture.
Owner: Dave Meloncelli.
Design status: APPROVED, as instructed by the owner.
Document status: DRAFT, original decision records reconciled.
Grill Me is design-approved. These documents do not reopen approval.
No implementation, commit, remote write or deployment is authorised
by the act of preparing this package.

## 1. Authority, provenance and source reconciliation

Consumer: Dave and Josh reviewing the independent design package;
then an implementer working from an explicitly reviewed revision.
The owner-approved design and an unapproved implementation proposal
are different authorities.

Evidence levels:

- Approved and directly supported: the owner's original decisions,
  recorded decision registers and final audit resolutions read in
  the source conversation.
- Approved but reconstructed: earlier handover summaries, retained
  only as historical context. Original decisions now supersede them.
- Implementation proposal: mechanisms not chosen by the owner,
  technologies, provider selections and numerical estimates introduced
  by this drafting work. Gate allocations now follow the recovered
  consolidated baseline; any new change is labelled as a proposal.

Sources:

- S1: owner instructions in this Work chat and subsequent authority
  to upload the review drafts and place them on GitHub main.
- S2: earlier recovered Q1–Q9 summary. Historical only; it was
  incomplete and is no longer the primary evidence for those Qs.
- S3: the supplied Downloads/fullchat.md excerpt: Q26A through Q31
  and the beginning of the Q32 question, 777 lines. SHA-256:
  9bfc01f6a670bbc259a0ab8c3692d92ecade4c0978769e7a9ef50dd31046feb0.
  This excerpt was not a complete transcript.
- S4: original conversation's final owner exchanges recovered by
  chat retrieval: Q32, Q33, C-01–C-08, explicit C-06 selection
  and final baseline approval.
- S5: originating-agent commentary supplied by the owner, clarifying
  traceability and the live-parent-copy publication hazard.
- S6: [App Capture Concept](https://chatgpt.com/c/6ad5c13e-59e0-83ec-bde2-0f6f57294911),
  read directly in the signed-in browser on 19 October 2026.
  Earlier messages were loaded and the recorded Q1–Q25 decisions,
  full Q9, Q25A capture amendment and related operational decisions
  were read. Q26A/Q26–Q33 are also supported by S3/S4.
  This is a source read, not an AI reconstruction.

S6 anchors are the visible “Decision Qn recorded” blocks followed
by their decision registers; the capture amendment is headed
“Capture architecture amendment recorded” and “Q25A: Capture-device
architecture”. These anchors are reproducible for an authorised
viewer of the source chat. The original conversation remains the
source; this public package does not reproduce private account
navigation, sign-in information or unrelated chats.

S7: the owner-replaced Downloads/fullchat.md, read on 19 October
2026: 1,526 lines, starting with final C-06 and the consolidated
v1.0-RC baseline, followed by explicit approval, the complete
reconstructed register and its classification table.
SHA-256:
704bc76d0c24cb5818d53cd9a6dce984510cc8582dffaf1357b908b0f8a257dd.
S7 supplies the approved consolidated deferrals and corroborating
summaries; S6 supplies the original Q1–Q25 records. S7 is not
mislabelled a verbatim original transcript. S3 is the historical
earlier excerpt; its former file path now holds S7.

All Q1–Q33 decision IDs and both Q25A/Q26A amendments are now
accounted for. The former Q9 truncation and Q10–Q25/capture source
gaps are closed. This does not certify implementation, test execution
or the owner's approval of implementation details and numerical budget estimates.

Precedence audit:

- C-01 replaces Q15's earlier production-group split with commercial
  title + edition + release grouping. Printing/PoD changes alone
  do not move a copy to a new product.
- Q31 replaces earlier automatic-publication wording, including
  Q9 and Q25. Approval and queued work prepare drafts; only the
  owner releases inventory to customers.
- C-06 narrows earlier Q21/Q22 automatic withdrawal/correction ideas
  to one copy's emergency availability suspension. Content edits,
  migrations and restoration require the appropriate human authority.
- C-05 qualifies “immutable/indefinite” evidence with authorised
  deletion/restriction and non-sensitive tombstones.
- C-07 requires retaining sold variants, overriding any suggestion
  that routine sale requires deleting or retiring the Shopify variant.

The pre-existing implementation and proprietary dataset have not
been inspected. The only repository contents read are this independent
documentation package and its README. Source recovery does not lift
the prohibition on adapting the baseline to the existing system.

## 2. Product purpose and authority

Capture physical stock, preserve evidence, establish defensible
copy-specific descriptions and prepare reviewed Shopify drafts.
Support hybrid iOS capture and the shared desktop browser workflow.
The precise mobile framework remains unselected.

The owner alone publishes. Listing approval, reference-catalogue
promotion and storefront publication are different authorities.
Neither bulk approval nor Gate 2 completion permits app publication.

The app creates drafts. It must not modify a live product merely
because a new copy belongs with that product: adding a variant to
a published product may expose that variant immediately. Such a
copy remains staged and unavailable on every enabled sales channel
until an owner-controlled publication path has been reviewed and
proven. This is a mandatory Gate 1 negative test (AT-29) and a
Gate 2 storefront/feed check, including direct cart/checkout paths. The exact Shopify staging mechanism is
TBD; production is blocked until this case is tested.

## 3. Bibliographic grouping and physical identity

A Shopify product represents **title + edition + release**.
A release distinction includes a limited edition or materially
different cover art. A printing difference alone does not create
a different product.

Each physical copy has its own permanent identity, SKU and variant.
Copies from different printings, including PoD, may share a product.
Eleven printings of one title do not imply eleven products.

Each copy carries one production status:

- original;
- reprint;
- PoD;
- printing unverified.

Establish the status from that copy's evidence. Product membership,
a sibling's evidence and a reference candidate cannot confer it.
An uncertain copy can be approved with honest disclosure.
Unsupported first-printing, original-production or rarity claims
are forbidden. Credible authenticity conflicts require review.

Keep copy condition, defects, completeness, price, photos and
availability distinct. Do not generalise one copy's condition to
the product. A copy's factual PoD status must be disclosed where
appropriate. Commercial intelligence about other PoD availability
or prices must not appear in customer text, tags or feeds.

## 3A. Logical records and state contracts

Physical schema/framework choices are still implementation work.
The following logical relationships preserve the approved behaviour:

- Work/title, content edition and release identify the commercial
  product group. Printing/production facts are evidenced per copy.
- PhysicalCopy owns permanent ID/SKU, condition/completeness,
  production/authenticity state, media links and physical location.
- OriginalMedia owns canonical hash/capture/device/slot provenance;
  Derivative links to original and transformations; retakes supersede
  rather than overwrite. Privacy tombstones do not retain content.
- ProcessingRun links immutable inputs/version/configuration to
  resulting claims. Claim retains source scope, conflicts, dependency
  relationships and human verification/presentation decisions.
- Approval links reviewer/time to the exact listing/evidence/policy
  revisions. Material change invalidates current approval while
  retaining the historical approval record.
- ShopifyMapping links internal group/copy IDs to external product,
  variant, inventory item and location references; external IDs do
  not replace canonical identity.
- Job/Attempt records durable state, ownership lease, retries,
  revalidation and confirmed remote outcome. SaleSnapshot and
  CommercialEvent retain represented purchase facts and chronology.
- OperationalException records exposure, owner, attempts and
  resolution separately from notification delivery.
- Restricted commercial/personal records are outside enrichment
  credentials. Nullable costs are distinct from zero; future lot,
  demand and case records use the reserved extension interfaces.

Capture: Locally Saved -> Uploading -> Server Verified, or Attention
Required; local acknowledgement follows persistence.
Review: evidence/condition/pricing qualified -> human-approved
revision; material change -> revalidation/exception.
Shopify work: approved -> awaiting Shopify -> preparing draft ->
draft confirmed, or attention required. Public release requires the
owner; a live parent never supplies that authority.
Availability: Shopify-owned current state; qualifying emergency ->
attempted suspension -> confirmed unavailable or unresolved critical
failure; restoration requires owner approval and reconciliation.
Image evidence: canonical -> superseded or authorised restriction/
deletion with tombstone; no silent rewrite.
Exact enum/storage implementation remains TBD; these are behavioural
contracts, not assertions that a database has been built.

## 4. Capture, condition and physical location

Capture records structured grade, defects, completeness and
evidence photographs. Item-type policy determines required evidence
and exceptions. AI cannot silently override human condition grades.

Every copy records a shelf, bin, box or equivalent location.
Staging is allowed at capture; final physical location is required
before publication. Location changes are auditable.
A storage location is not a Shopify inventory location.

Templates cover individual books, boxed sets and simple accessories.
Grade a boxed set's box and contents separately. Do not require a
sealed item to be opened. TCG and LEGO are future extensions, not
initial-release commitments.

Adaptive capture requests additional evidence while the item is
in hand: copyright pages, stock codes, printing identifiers or
defects. Slow AI must not block continued capture. Operators may
defer evidence requests. Q32 permits a fixed checklist only through
the approved scope-reduction process.

Local capture must survive network loss and app interruption.
Upload recovery and synchronisation status must be truthful.
Q25A makes mobile and desktop capture equal first-class workflows.
The existing CZUR Lens is supported through a verified device path
or desktop file import. Direct camera/SDK support must be tested,
not assumed. Neither workstation requires the other to be available.
An iPhone-started item can receive desktop images using the same
copy ID, evidence slots and processing contracts.

Desktop pricing is entered and approved at review, not required at
capture. The selected/scanned physical location can carry forward
until changed and supports a storage-area/shelf/box hierarchy.
Capture evidence requests explain what is needed and why, with
missing, inconclusive and contradictory evidence kept distinct.

Locally Saved requires durable images and condition records.
Uploading, Server Verified and Attention Required reflect actual
state. Unsynchronised data is not described as backed up.
iOS background uploading is best-effort; completion after app
termination is not assumed. Both workflows require accessible,
keyboard-operable controls and appropriate spoken feedback.
Minimum initial evidence includes front/back covers and template-
specific identification, publication, completeness and defect images.
Back-cover OCR may supply candidate content context; publication
policy still governs any customer-facing text.

## 5. References, claims and review

OCR, AI and datasets propose candidate records. Only authorised
humans can promote trusted catalogue references, with evidence,
versions and audit history. Inventory approval does not confer
reference-promotion authority.

Routine consistent condition assessments avoid unnecessary review.
Material defects, inconsistent assessments and missing evidence
create exceptions. Policy-qualified bulk approval requires identity, collector identity,
condition/completeness, pricing and publication checks. Present
eligible and excluded items and outstanding exceptions clearly.
The operator explicitly authorises the batch; routine qualified
items need not each be opened. Material concerns require individual
review; an AI confidence score cannot authorise publication.

Revalidate each item on the server immediately before approval.
Record operator, timestamp, listing revision, supporting evidence
and validation-policy version. Material changes invalidate the
relevant approval. AT-13 is now grounded in the complete Q9 source,
rather than being merely an implementation proposal.

Maintain three independent confidence dimensions: bibliographic
identity, collector identity, and physical condition/completeness.
A previously verified reference cannot silently overwrite contrary
evidence from a newly captured copy.

## 6. Evidence and processing history

Never request or record GPS for app capture. Strip location from
camera-roll imports before persistent application storage, including
local staging and upload queues. Preserve the image pixels.
Do not retain the unsanitised imported file as a second original.

For an import, the canonical original is the location-stripped file.
Hash that file with SHA-256 after sanitisation. For app capture,
create a location-free original from the outset.

Record copy ID, timestamp, necessary device provenance and image
slot. Originals are write-once: retakes create new media records
and supersede earlier ones without overwriting them.

Keep ordinary evidence indefinitely, subject to privacy exceptions.
Operator roles and evidence processes alone can read originals.
All other processing and public/external use receives sanitised
derivatives traceable to the original and transformation history.
Personal inscriptions, names and paperwork are flagged and withheld
from public/external use unless specifically authorised.

Immutability prohibits silent rewriting; it does not prohibit
authorised deletion or restriction. Preserve a non-sensitive
tombstone containing hash, reason, authoriser and time.
Propagate restrictions to derivatives and access paths. Backup
restore procedures must reapply restrictions before exposure.

Each consequential processing run has an immutable ID, input hash
and references, timestamp, engine/model version, configuration,
claims and review outcome. Reruns add evidence versions.
Approvals retain the exact evidence versions used.
Disagreements trigger reconciliation. Human corrections retain
identity, timestamp and justification. Temporary caches can expire.
Reproducible provenance does not promise identical AI output.

## 7. Local-first privacy boundary

Consult the internal catalogue and local OCR/image matching first.
External AI/data services are fallback only when the local tier
cannot answer. There is no external-provider default.

Four data classes:

- Public bibliographic: permitted task-relevant title, ISBN,
  publisher and cover material.
- Copy evidence: permitted identification evidence only.
- Commercial: acquisition cost, supplier, unpublished prices,
  pricing intelligence and trade-in negotiations.
- Personal: customer requests, sellers and personal details.

Commercial and personal data are excluded from enrichment-provider
payloads through database roles and schema isolation, not just
field filtering. Public bibliographic does not mean automatic
permission to transmit every field or image.

Each provider has a reviewed register entry specifying task,
allowlisted data, retention, processing region, contractual terms
and prohibition on training use. Strip metadata and crop
derivatives to the item. Never disclose surrounding stock,
paperwork or original-storage access.

Log provider, purpose, field list, payload hash, timestamp and
outcome, without retaining a duplicate sensitive payload.
Provider results and OCR text are untrusted data, never instructions
or automatically verified catalogue facts.

If the local tier fails and no compliant external route exists,
stop or use manual entry. Do not weaken the boundary.
Any exception requires explicit owner approval and an audit trail;
a gate cannot claim its original privacy criterion passed after
the criterion has been weakened.

The owner requests Australian privacy compliance. Applicability,
retention duties and lawful exceptions need qualified assessment;
this draft makes no legal determination. Internal controls apply
regardless of any statutory exemption.

## 8. Exactly four backend components

Q30 fixes the MVP shape:

1. One web application: API, bench application and review screens.
2. One background worker process.
3. One database.
4. One object store for originals and derivatives.

No separate broker. Use database-backed jobs with locking, leases,
retries and recovery. No extra deployable service without a
recorded justification and reviewed complexity impact.

Modules: Catalogue, Claims, Capture, Evidence, Commerce and Demand.
Each owns its tables and exposes an interface. Tests and import
rules enforce boundaries. Demand reserves the deferred request/supply interface described below;
it does not become a new deployable service or a Gate 2 full workflow.

Commercial and personal schemas use restricted roles. The worker
making provider calls must not possess sensitive-schema credentials,
including through inherited environment, connection pools, views,
privileged functions or previous jobs. Sensitive operations must
use an authorised boundary without upgrading the enrichment worker.

Use managed hosting/database and automatic backups. Routine
operations should take one command or one screen. Recovery has
one documented command, rehearsed with explicit prerequisites.
The exception centre and daily health summary report problems to
the operator. This draft creates no notification automation.

## 9. Shopify lifecycle and exceptions

Reliquary owns physical-copy records. Once provisioned, Shopify owns
sellable availability. Sales, reservations, refunds and adjustments
require reconciliation. Metadata sync must never reset sold stock
to one. Returned stock needs physical inspection before resale.

Retries must not duplicate products, variants or sellable copies.
Proposed implementation: stable copy/group keys, durable operation
ledger, bounded retries and remote-state reconciliation after an
ambiguous timeout. Do not assume exactly-once webhook delivery or
assume a failed response means a write did not occur.

Sold variants remain in place and unavailable. The theme hides them
from the copy picker; feeds exclude them. Each available variant
feed item carries its own condition and price. Product structured
data must not attribute a single copy's condition to the whole title.

Gate 2 inventories every app with product write access, including
book-metafield writers. Assess ownership and conflicts; any
unassessed writer blocks go-live. The assessment occurs after this
independent design is preserved, under appropriate authorisation.

C-06 permits one narrow automatic protective action in a defined
emergency, such as sale elsewhere or an authenticity flag:
verify the affected copy/variant, Shopify inventory location and
current stock state, apply concurrency protection, set only that
copy's available quantity to zero, reconcile the final state and
raise a critical exception. Worker acceptance or a queued request
is never confirmation of suspension. Do not edit content, unpublish a product,
change sibling stock or restore availability automatically.
Restoration requires the owner, current Shopify reconciliation
and physical inspection where a return is involved.

If suspension fails, availability may remain exposed. Keep the
critical case unresolved, alert/escalate, reconcile and retry only
within the protective boundary. Delivered alert, acknowledgement,
successful suspension and resolved case are separate states.

The central exception centre records severity, affected inventory,
customer exposure, financial risk, cause, owner and recovery status.
Routine failures queue; critical risks alert immediately and remain
visible. Corrective actions are audited.

## 10. Controlled development toolchain

Q26A makes Shopify CLI a development and diagnostic tool for app
development, API exploration, theme testing and deployment.
It is not a runtime dependency. Runtime uses supported APIs.

Separate development and production configuration and credentials.
Keep secrets out of GitHub. Version app configuration and theme
changes. Deployments require validation, rollback and audit.
Production mutations, deployments and destructive operations need
explicit authorisation. This drafting task performs none.

Use the already-existing isolated development store for Gate 1.
No live publication before Gate 2; owner publication remains the
rule after Gate 2.

## 11. Acceptance and delivery governance

Gate 1: five specified physical books through accurate drafts,
forced retry without duplication and simulated sale affecting only
the correct copy. Pre-ISBN TSR title is identified by stock code;
evidence-backed printing or “printing unverified” passes.
Guessing printing fails. Reliable production-variant detection is
Gate 2 or Later, not a prerequisite for Gate 1 honesty.

Gate 2: 50 books end to end; measured desktop effort per listing
against the two-minute target; zero duplicate sellable copies under
fault injection; rehearsed backup restore; tested privacy denial;
evidence-safe listings and no leaked PoD commercial intelligence;
complete writer assessment; owner-controlled publication.
The source does not specify the timing aggregation or acceptable
outlier rule. Ratify these before timing tests, without silently
substituting an average for the stated target.

Every criterion needs a named automated check with a known-good
case that passes and a known-bad case that fails.
Empty fixtures, skipped assertions and “nothing found” do not pass.
These documents define tests; no software acceptance test has run.

Q32 requires fixed effort and owner-attention budgets, one 50%
checkpoint, the ordered cut ladder, owner-only reductions/resets,
one reset maximum and a full re-plan after a second miss.
A reduced gate is reported under a different name.
See PLAN.md for proposed numerical estimates, not approved caps.

Q33 closes grilling after classification, gate allocation and the
contradiction audit. Design approval is preserved; incomplete source
reconciliation is recorded as documentation debt.

## 12. Recovered catalogue and operational contracts

### Tiered processing and independent providers: Q10/Q19

Use barcode recognition, conventional OCR and catalogue matching
before expensive AI, with Q27's local-first privacy taking precedence.
Reuse verified knowledge without overriding contradictory copy
evidence. Deduplicate/cache identical requests where appropriate.
Track processing costs per item, batch, operation and provider;
configure spending limits and escalation policy. Expensive reprocessing
over budget needs explicit authorisation. Provider outages leave
capture durable and processing recoverable.

Use a versioned Data Provider Interface. Results are candidates,
with source, version, timestamps and usage restrictions. Providers
cannot mutate canonical references and can be disabled/replaced
without restructuring the application. Optional-provider absence
does not stop manual/local ingestion.

Support independent, provider-assisted and comparative evaluation
modes using the same inputs and independent truth fixtures.
Comparative evaluation of the existing dataset remains deferred
until the independent design and tests are preserved and access
is separately authorised. Agreement is not independent proof.

### Existing-stock reconciliation and authenticity: Q11/Q12

Check for potential Shopify matches before creation. A title, ISBN,
edition or image match does not prove physical-copy identity.
Link an existing item only after explicit operator confirmation.
Preserve identifiers, sale history and quantities; never silently
overwrite existing content. Conflicting SKUs, duplicate physical
identities and uncertain matches become exceptions. Link/unlink
decisions are audited and reversible where safe. Full migration is
not a launch prerequisite.

Unknown printing can proceed with disclosure. Credible counterfeit,
unauthorised-reproduction or misrepresentation evidence creates an
independent authenticity hold. Held items cannot pass bulk approval
or publication. Only an authorised specialist may resolve/dispose
of a concern with evidence, identity, time and outcome.
AI can flag concerns, not declare counterfeit or release a hold.
New contrary evidence reopens an earlier verification.

### Portability and recovery: Q13/Q14

Reliquary owns catalogue, media and history independently of Shopify.
Export all canonical records, relationships, claims, evidence,
condition and provenance through a documented, versioned format.
Permanent IDs remain distinct from Shopify/cloud/provider IDs.
Export media with verifiable manifests and checksums.
Backups and at least one end-to-end restore precede production.
Record dependencies, limitations and manual prerequisites.
Full multi-cloud deployment automation is outside the MVP.
Assess cost, security, accessibility, portability and maintenance
before provider selection. Existing-resource assessment must not
become an unauthorised existing-system inspection in this design task.

### Selected-copy customer experience: Q16

Variant selection updates that copy's photos, grade, defects,
completeness, price and availability. Shared bibliography remains
consistent; a sibling's condition image is never presented as the
selected copy's evidence. Preserve the selected copy through cart,
checkout and fulfilment. Support keyboard and screen-reader use.
If copy data fails to load, prevent an ambiguous purchase instead
of showing misleading fallback details.
Verify theme/channel capability and variant capacity before go-live,
not by assuming that the current theme supports the design.

### History, demand and costing: Q17/Q18/Q24

Keep auditable acquisition, listing, sale, return and retirement
events, relevant order/variant references, evidence and commercial
history. Protect personal data and respect retention exceptions.
Preserve acquisition cost, asking price, discounts, realised sale
price, fees and freight where known.

The deferred demand register links to catalogue identity independently of an
existing Shopify product. Record explicit customer wanted items and
acceptable editions/printings/production alternatives; distinguish
collector demand from an inexpensive playable copy.
Staff can record purchasing opportunities, trade-in enquiries and
potential collection acquisitions. Distinguish customer demand,
potential supply and completed transactions. Explicit requests are
stronger intent than passive browsing. Notifications need appropriate
contact consent/preferences. Interest guarantees neither stock,
future acquisition nor price. No messages are authorised by this
documentation task.

Preserve optional/nullable item-cost foundations in Gate 2.
The deferred detailed-costing workflow records acquisition lots with total cost,
date, source, incidental costs and associated items. Later cost
allocation is allowed with adjustments, methodology and no double
counting. Distinguish known, allocated, estimated and unknown.
Unknown cost is not zero. Incomplete costing does not block reviewed
pricing or draft approval; profitability distinguishes realised,
estimated and incomplete results.

The approved final baseline defers full customer demand and wanted-
item notifications, trade-in/collection-acquisition workflows,
detailed cost allocation, full historical Shopify migration and
full customer-impact case management until after Gate 2.
Gate 2 retains history, nullable cost fields, collision/SKU safety,
and manual holds/resolution. Full automation is not smuggled into
these foundational requirements.

Advanced valuation, forecasting, predictive demand scoring,
automated buying recommendations and passive behavioural tracking
are Later proposals outside the initial release. Preserve the basic
ledger and explicit-request foundations without building those
advanced capabilities first.

### Claim dependencies, invalidation and controlled correction: Q20/Q21

Each material claim has source, evidence, confidence and verification
state. Preserve conflicts. Trace common upstream sources and derived
claims: two dependent sources do not corroborate one another.
A claim cannot independently corroborate its own origin.

One versioned, testable publication policy governs descriptions,
back-cover summaries, structured data, customer-visible metafields,
tags and storefront/feed output. Policy can assert, attribute,
qualify, withhold or escalate a claim. Unclassified paths do not
bypass the policy. Overrides need identity, time, evidence and audit.

Evidence/policy changes trigger impact assessment across affected
copies and customer surfaces, with historical sale representations
preserved. Reconcile caches, delayed updates and failed writes.
New material assertions and live content corrections need authorised
human action; agents have only C-06's narrow suspension exception.
Failure to remove customer exposure remains a critical case.
A public-cache or channel leak cannot be declared fixed merely
because an internal claim was invalidated.

### Controlled migration and post-sale accountability: Q22/Q23

Permanent copy identity, history, SKU, photos and evidence survive
a legitimate move between commercial release groups. A printing or
PoD reclassification alone only changes copy evidence/status under
C-01 and does not require regrouping.

The full migration workflow is Later. Gate 2 must safely hold and
route a genuine edition/release regrouping for manual resolution.
When the deferred migration workflow is implemented, it needs human authorisation,
availability suspension within the approved rules, current Shopify
reconciliation and a recoverable multi-step workflow. Active orders
or reservations require explicit resolution. Preserve order/refund/
return/fulfilment links and at most one sellable representation.
Failure leaves a safe recoverable state; rollback never rewrites
completed transactions. Audit reason, approver, origin, destination
and outcome.

A material post-sale correction identifies affected transactions
from retained sale evidence. Full prioritised customer-impact case
management is Later; Gate 2 retains the evidence and manual escalation. Keep exactly the title,
edition, printing/status, condition, photos, description and price
represented at sale, linked to original and corrected evidence.
Authorised humans decide communications, refunds, returns,
replacements or compensation; record contacts and outcomes.
Applicable consumer obligations require proper assessment, not a
discretionary-remedy assumption. Restrict access and retention.

### Shopify outage continuity: Q25

Capture, enrichment, assessment, review, pricing and approval can
continue when Shopify is unavailable. Store jobs durably across
authentication failures, outages and rate limits.
Resume draft-preparation jobs only after revalidating evidence,
claims, condition, price, approval revision and Shopify inventory.
Stale/conflicting approvals return to exceptions; no duplicate
product, variant or sellable copy is permitted.

Distinguish Approved, Awaiting Shopify, Preparing Draft,
Draft Confirmed, Attention Required and owner-controlled Published.
These labels implement Q25's state distinction under Q31's later
draft-only rule: automatic queue resumption does not publish.

## 13. Contradiction audit and circle-back receipt

Source recovery through S6 and S7 closed the missing-Q9/Q10–Q25/Q25A
handover gap and restored the approved release allocation.
The earlier excerpt genuinely contained only Q26A onward; the full
signed-in conversation supplies the earlier original records.

Conflicts resolved: C-01 over Q15 grouping; Q31 over automatic
publication in Q9/Q25; C-06 over broad automated edits in Q21/Q22;
C-05 over undeletable evidence; C-07 over routine sold-variant removal.
The live-parent-copy safeguard and worker credential proof remain
mandatory. Newly recovered requirements do not create microservices.

ENGINE: connect recovered requirements to models, gates and tests.
EXPERIENCE: dual capture, actual sync states, accessible copy choice,
consented demand and central exceptions are now explicit.
SKILL: original source was read through the supported signed-in
browser. No unrelated chats, dataset or implementation were used.
VALUE/CARRY-FORWARD: recover once, record the source anchors and
reconcile all six documents together. Budgets remain proposals.
FINAL: rights, provider contracts, operating costs, lawful retention
and recovery evidence remain explicit review obligations.

This is a documentation reconciliation, not a gate test result.
All source-backed claims are attributed/recovered; new allocations
and estimates remain unverified/introduced.

## 14. Remaining review decisions

B1 source recovery: CLOSED by S6. Original Q1–Q25 and Q25A now
replace the reconstructed/truncated handover.
B2: owner reviews the reconciled package, numerical effort proposal,
attention budgets and the two-minute timing rule. The gate allocations
follow the recovered consolidated baseline, not a new scope expansion.
B3: choose frameworks/providers and assess material spend, rights,
privacy/consumer obligations and recovery objectives.
B4: prove live-parent staging and worker execution/credential denial.
B5: implement and execute the expanded good/bad acceptance suite.

Placing this revision on main follows the owner's instruction to
share the review package there. It does not ratify these remaining
decisions or authorise a production Shopify mutation.

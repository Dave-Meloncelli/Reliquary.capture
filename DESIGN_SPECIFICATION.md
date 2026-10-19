# Reliquary Ingest: canonical design specification

**Review draft 0.1 | Baseline v1.0-RC | 19 October 2026**

Target repository: Dave-Meloncelli/Reliquary.capture.
Owner: Dave Meloncelli.
Design status: APPROVED, as instructed by the owner.
Document status: DRAFT, source reconciliation incomplete.
Grill Me is design-approved. These documents do not reopen approval.
No implementation, commit, remote write or deployment is authorised
by the act of preparing this package.

## 1. Authority, provenance and completeness

Evidence levels used in REQUIREMENTS.md:

- Approved and directly supported: explicit owner decisions and audit
  resolutions available in S1/S3/S4.
- Approved but reconstructed: S2 summaries of Q1 to Q9, pending
  original-transcript verification. Q9 is incomplete even as a summary.
- Implementation proposal: introduced mechanisms, schemas beyond
  settled Q30 boundaries, estimates, allocations and technology choices.
- Source absent: Q10 to Q25 and missing amendment text; no content
  has been reconstructed for them.

S5: the owner's supplied comments from the originating agent in
this chat. They confirm source limitations, request three evidence
levels and identify live-parent variant exposure as a necessary
clarification of owner-controlled publishing. S5 is commentary on
the design, not a replacement transcript for Q1 to Q25.

The consumer of this package is Dave, reviewing the independent
baseline before any commit. A future implementer consumes the
reviewed version, not unreviewed proposals in this draft.

Sources:

- S1: current user instructions: five Markdown drafts, independent
  design, no pre-existing-system inspection, no commits or remote writes.
- S2: owner-supplied recovered register in this chat: Q1 to Q8,
  plus the beginning of Q9. It explicitly calls itself a decision
  summary rather than a verbatim transcript.
- S3: supplied fullchat.md, read from
  C:/Users/davem/Downloads/fullchat.md. It contains 777 lines.
  Decision anchors: Q26A line 2; Q26 line 78; Q27 line 160;
  Q28 line 259; Q29 line 396; Q30 line 480; Q31 line 621.
  It ends with the Q32 question, without the owner's Q32 answer.
  Source SHA-256:
  9bfc01f6a670bbc259a0ab8c3692d92ecade4c0978769e7a9ef50dd31046feb0.
- S4: retrieved App Capture Concept chat, conversation ID
  6ad5c13e-59e0-83ec-bde2-0f6f57294911: owner's Q32 answer,
  Q33 closure, C-01 to C-08, C-06 selection and final approval.
  The retrieval supplied five exchanges and no older-page cursor.

Approved decisions recovered from these sources are **attributed /
recovered** claims. Draft allocations, estimates and implementation
mechanisms are **unverified / introduced** proposals. They do not
acquire approval merely by appearing here.

Q10 to Q25, the end of Q9, and earlier capture amendments are not
present in the available sources. Their content and allocation
must not be inferred from later references to them. This package
cannot yet be certified as the complete canonical baseline.

Later owner amendments and final audit resolutions supersede
conflicting earlier wording. In particular, “production group”
in an older Q31 assistant summary does not override C-01.

The existing implementation, proprietary datasets, GitHub contents
and live Shopify configuration have not been inspected. An existing
development store is known only from the supplied Q31 decision.

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
The exact earlier capture amendment is missing; do not assume
that this paragraph fully reconstructs it.

## 5. References, claims and review

OCR, AI and datasets propose candidate records. Only authorised
humans can promote trusted catalogue references, with evidence,
versions and audit history. Inventory approval does not confer
reference-promotion authority.

Routine consistent condition assessments avoid unnecessary review.
Material defects, inconsistent assessments and missing evidence
create exceptions. Policy-qualified bulk approval is accepted in
principle; conflicts require individual review. The supplied Q9
text ends mid-sentence, so its complete approval contract is TBD.

Proposed safeguard for implementation review: bind an approval to
the exact reviewed record and evidence versions; reject stale
approval after material edits. This is a draft mechanism, not a
claimed reconstruction of Q9's missing text.

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
rules enforce boundaries. Mentioning Demand does not recover its
missing requirements or authorise building them now.

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
set the affected copy's available quantity to zero and raise a
critical exception. Do not edit content, unpublish a product,
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

## 12. Contradiction audit and circle-back receipt

Resolved conflicts:

- Commercial grouping does not establish copy production identity.
- Honest “this copy is PoD” differs from confidential PoD-market data.
- Final owner publishing supersedes any earlier auto-publish idea.
- Narrow suspension is an explicit exception, not general live-edit power.
- Location-stripped original pixels differ from imported file bytes.
- Authorised deletion with a tombstone coexists with immutability.
- Four components coexist with credential-enforced privacy separation.
- A sold variant is retained, while picker/feed visibility is removed.
- A reduced gate cannot be reported as the original passing.
- Existing live-product association needs staging, not silent exposure.

Circle-back disposition:

- ENGINE: recovered Q26 to Q31; missing Q10 to Q25 still blocks
  complete traceability. ACTIONED to source reconciliation before
  budget ratification or implementation.
- EXPERIENCE: single-workflow operations and truthful sync preserved;
  timing target's aggregation remains a pre-test decision.
- SKILL: explicit Markdown output and no remote writes govern delivery;
  no reuse scan of an existing implementation is permitted here.
- VALUE/CARRY-FORWARD: preserve this independent draft and its source
  coverage. Resolve missing canon before spending implementation effort.
- FINAL: dependency/licensing prices and compliance assessment remain
  explicit BOM unknowns; recovery and failure tests are specified.

Consumer: Dave at document review, then the authorised implementer.
Receipt claims: source coverage is attributed/recovered; proposed
mechanisms and estimates remain unverified/introduced.

## 13. Review blockers and exact next actions

B1: Recover Q10 to Q25, the end of Q9 and earlier capture amendments.
Owner: drafting agent reconciles supplied source; Dave supplies missing
source if retrieval remains unavailable. Trigger: before this package
is marked complete or any implementation budget is ratified.

B2: Ratify numerical budgets, proposed allocations and timing rule.
Owner: Dave. Trigger: after B1, before implementation.

B3: Select framework, managed providers and compliance arrangements.
Owner: authorised implementer prepares options; Dave approves material
spend or policy changes. Trigger: before the affected build stage.

These are recorded again in PLAN.md's review queue.

# Reliquary Ingest: requirements and gate matrix

**Review draft 0.1 | Baseline v1.0-RC | 19 October 2026**

Sources S1 to S4 are defined in DESIGN_SPECIFICATION.md.
Recovered decisions are attributed/recovered.
Evidence status is stated for every question/amendment below.
“Approved but reconstructed” is not direct transcript verification.
All allocations below are introduced planning proposals for review;
they do not alter the approved design.

Classification vocabulary:

- MVP / Gate 1 minimal: required for the technical proof.
- MVP / Gate 2 required: production safeguard or completion.
- LATER / Later: retained intent outside the two release gates.
- DROPPED: requires an explicit owner decision; none invented here.
- UNALLOCATED: source missing. Not a synonym for Later or Dropped.

A Gate 1 requirement continues into Gate 2.
Deferral never permits unsafe behaviour on an earlier gate's path.
If a feature is not needed yet, disable its path; do not run it with
weaker privacy, claim or publication controls.

## Original decisions Q1 to Q9

### Q1: conditional collector identity

Source/evidence: S2; approved but reconstructed.

Class/gate: MVP, Gate 1 minimal.
Requirement: each copy's identity is evidence-based; uncertainty is
disclosed; unsupported collector claims and inherited status fail.
Gate 2: production-wide evidence checks and conflict handling.
Tests: AT-01, AT-02, AT-08.

### Q2: human promotion of reference records

Source/evidence: S2; approved but reconstructed.

Class/gate: MVP, Gate 1 minimal for provisional/manual records.
Gate 2 required for the complete authorised promotion workflow,
versioned references and audit. No automatic promotion at either gate.
Tests: AT-03, AT-13.

### Q3: exception-driven condition

Source/evidence: S2; approved but reconstructed.

Class/gate: MVP, Gate 1 minimal: grade, defects, evidence and
boxed-set box/contents grading.
Gate 2 required: configurable exception policy, routine handling and
prevention of AI override. Tests: AT-04, AT-12.

### Q4: Shopify inventory ownership

Source/evidence: S2; approved but reconstructed.

Class/gate: MVP, Gate 1 minimal: draft inventory, simulated sale,
retry and no stock resurrection.
Gate 2 required: reservation/refund/return/adjustment reconciliation
and physical inspection of returned stock.
Tests: AT-06, AT-07, AT-14.

### Q5: hybrid iOS and shared desktop workflow

Source/evidence: S2; approved but reconstructed.

Class/gate: MVP, Gate 1 minimal capture/review path with durable
local capture, offline continuity and resumable upload.
Gate 2 required: hardening across supported devices and recovery.
Framework remains TBD. Tests: AT-05, AT-15.

### Q6: permanent identity and physical location

Source/evidence: S2; approved but reconstructed.

Class/gate: MVP, Gate 1 minimal: copy ID, SKU and capture location.
Gate 2 required: final-location publication preflight and audited
moves. Physical and Shopify locations remain distinct.
Tests: AT-01, AT-16.

### Q7: templates and sealed handling

Source/evidence: S2; approved but reconstructed.

Class/gate: MVP, Gate 1 minimal for book and boxed-set fixtures.
Gate 2 required: simple accessories and configurable policies,
including sealed items without opening.
LATER / Later: TCG and LEGO extensions.
Tests: AT-04, AT-17.

### Q8: adaptive evidence capture

Source/evidence: S2; approved but reconstructed.

Class/gate: MVP, Gate 1 minimal adaptive requests and deferred
resolution without blocking capture.
Gate 2 required: robust template-driven adaptation.
A fixed checklist is an owner-approved Q32 cut, not a silent
reclassification. Tests: AT-05, AT-18.

### Q9: policy-qualified bulk approval, incomplete source

Source/evidence: S2; approved but reconstructed; truncated.

Class/gate: MVP, Gate 2 required for recovered bulk-approval intent.
Gate 1 can use individual approval; it must still check policy.
Full Q9 classification remains UNALLOCATED until the truncated
sentence and remaining conditions are recovered.
Test: AT-12. Proposed version-bound approval check: AT-13;
do not represent that proposal as the missing source text.

## Unrecovered decisions Q10 to Q25

The following sixteen entries intentionally preserve every ID.
No title, requirement or release allocation has been fabricated.

### Q10: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q11: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q12: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q13: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q14: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q15: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q16: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q17: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q18: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q19: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q20: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q21: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q22: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q23: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q24: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

### Q25: source not recovered

Source/evidence: no available source; source absent.

Class: UNALLOCATED, not DROPPED.
Gate: unresolved; no Gate 1/Gate 2/Later claim is defensible.
Source: absent from S2, S3 and the accessible S4 exchanges.
Action: recover the approved decision, split its requirements,
allocate them and add positive/negative tests before implementation.

## Recovered decisions Q26 to Q33

### Q26: central operational exception centre

Source/evidence: S3; approved and directly supported.

Class/gate: MVP.
Gate 1 minimal: visible actionable failures and audited recovery.
Gate 2 required: severity, exposure, responsible operator,
notification/acknowledgement/resolution separation, escalation and
historical case analysis. Tests: AT-12, AT-19.

### Q27: local-first, purpose-limited disclosure

Source/evidence: S3; approved and directly supported.

Class/gate: MVP, Gate 1 minimal and never cut.
Gate 1: restricted worker credentials, separated sensitive schemas,
local-first/manual path and no disallowed disclosure.
Gate 2 required: full reviewed provider register, allowlists,
sanitisation, per-call audit and tested fallback.
Any provider enabled in Gate 1 must already meet all these controls.
Tests: AT-08, AT-09, AT-10, AT-11.

### Q28: location-free immutable evidence

Source/evidence: S3; approved and directly supported.

Class/gate: MVP, Gate 1 minimal: location-free acquisition,
canonical hashes, original-pixel preservation, restricted originals,
derivatives and retake history.
Gate 2 required: privacy retention exceptions, restrictions and
backup/recovery propagation. Enabled media paths require safeguards
from their first use. Tests: AT-10, AT-20, AT-21.

### Q29: versioned consequential processing

Source/evidence: S3; approved and directly supported.

Class/gate: MVP, Gate 1 minimal when OCR/AI is enabled:
input/version/configuration ledger and preserved outcomes.
Manual provenance remains mandatory if enrichment is cut.
Gate 2 required: reconciliation across versions and historical
approvals/corrections. Tests: AT-03, AT-21.

### Q30: fixed architecture and vertical slice

Source/evidence: S3; approved and directly supported.

Class/gate: MVP, Gate 1 minimal: four components, database queue,
enforced module/credential boundaries and one-book first slice.
Gate 2 required: managed operational services, automatic backups,
rehearsed recovery command and daily health summary.
Tests: AT-11, AT-22, AT-23.
No broker or microservice addition is allocated as Later by default.

### Q31: two gates and owner publication

Source/evidence: S3; approved and directly supported.

Class/gate: MVP, Gate 1 and Gate 2 governance.
Gate 1: five named book roles, correct drafts, retry and sale.
Gate 2: 50 books, desktop timing, fault injection, restore,
privacy and evidence-safe outputs.
Named good/bad tests and non-empty evidence apply to both.
Tests: AT-01 to AT-11, AT-22 to AT-26, AT-29.

### Q32: fixed budgets, checkpoint and cuts

Source/evidence: S4; approved and directly supported.

Class/gate: MVP, before Gate 1 begins and throughout delivery.
Effort and owner-attention budgets; one 50% checkpoint; ordered
cuts; owner-only reduction/reset; one reset maximum; second miss
requires full re-plan. Tests: AT-27, AT-28.
Numerical caps in PLAN.md are estimates for ratification.

### Q33: closure

Source/evidence: S4; approved and directly supported.

Class/gate: MVP, documentation/governance before implementation.
Close grilling after classification, release allocation and
contradiction audit. Owner design approval is recorded.
Complete source reconciliation is still required to certify this
matrix. Test: AT-30.

## Amendments and audit resolutions

### A-CAPTURE: earlier capture amendments

Source/evidence: source absent; recovered related provisions are S2 reconstructed and S3 direct.

Class/gate: UNALLOCATED beyond recovered Q5/Q8/Q28 provisions.
Exact amendment text missing. Recover before source-complete status.
Do not pretend the recovered hybrid/offline provisions exhaust it.
Tests pending reconciliation; existing coverage AT-05, AT-10, AT-18.

### A-CLI / Q26A: controlled Shopify CLI

Source/evidence: S3 Q26A; approved and directly supported.

Class/gate: MVP, Gate 1 minimal: isolated development store,
separate configuration, scoped identities and no committed secrets.
Gate 2 required: production-change approval, versioned config/theme,
validation and rollback. CLI is never a runtime dependency.
Test: AT-24.

### C-01: product grouping and copy production identity

Source/evidence: S4; approved and directly supported.

Class/gate: MVP, Gate 1 minimal.
Title + edition + release product; individual copies as variants;
printing differences, including PoD, do not split products;
no sibling-derived production identity. Test: AT-01, AT-02.

### C-02: variant feeds and structured data

Source/evidence: S4; approved and directly supported.

Class/gate: MVP, Gate 2 required.
Variant-specific condition and price; no single copy condition
asserted at product level. Test: AT-25.
Gate 1 model must preserve these distinctions.

### C-03: all product writers assessed

Source/evidence: S4; approved and directly supported.

Class/gate: MVP, Gate 2 required.
Inventory all apps with product-write access, including metafield
writers. Any unassessed writer blocks deployment.
Test: AT-26. No inspection is performed during independent drafting.

### C-04: stop rather than weaken Q27

Source/evidence: S4; approved and directly supported.

Class/gate: MVP, Gate 1 minimal and continuing.
A noncompliant external route is denied, not silently substituted.
Tests: AT-08, AT-09, AT-28.

### C-05: privacy deletion/restriction with tombstone

Source/evidence: S4; approved and directly supported.

Class/gate: MVP, Gate 2 required, with immutable evidence from
Gate 1. Any earlier personal-data exception requires this safeguard
before using that path.
Tombstone has hash, reason, authoriser, time; no sensitive content.
Test: AT-20.

### C-06: narrow protective action selected

Source/evidence: S4 explicit owner selection; approved and directly supported.

Class/gate: MVP, Gate 2 required before exposure to live inventory.
Only one affected copy's availability may be suspended automatically
in a defined emergency. Critical exception; owner restoration.
No content edits, unpublish, sibling change or automatic restore.
Test: AT-19.

### C-07: retain sold variants, suppress sales surfaces

Source/evidence: S4; approved and directly supported.

Class/gate: MVP, Gate 1 minimal: retain sold copy unavailable.
Gate 2 required: hide sold variants in picker and exclude from feeds.
Tests: AT-07, AT-25.

### C-08: reduced gates have separate names

Source/evidence: S4; approved and directly supported.

Class/gate: MVP, Gate 1 delivery governance and continuing.
No agent may relabel a reduced or failed gate as the original pass.
Tests: AT-27, AT-28.

### SAFETY-LIVE-PARENT: unapproved new copy of a live title

Source/evidence: Q31/S4 owner policy plus S5 originating-agent
clarification; derived enforcement of approved publication authority.
Class/gate: MVP, Gate 1 mandatory negative proof and Gate 2 required.
Requirement: no unapproved copy becomes purchasable on any enabled
channel through association with a live parent.
The staging mechanism is an implementation proposal, TBD.
Test: AT-29, with storefront, feed and direct checkout cases.

## Review result

33 original question IDs are represented; sixteen have no source
allocation, and Q9 is only partially recovered.
Q26A and the capture amendment are separately tracked.
All eight audit resolutions are individually represented.
No requirement has been designated DROPPED without authority.

Full classification is blocked, not passed. On source recovery,
split each compound Q into testable requirements and reconcile
specification, tests, budgets and BOM together before implementation.

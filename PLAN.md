# Reliquary Ingest — delivery plan

**Review draft 0.2 · v1.0-RC · 19 October 2026**

Target: Dave-Meloncelli/Reliquary.capture.
Design approval is recorded. Document review, budget ratification,
implementation, commits and deployment are separate decisions.
This document authorises none of those actions.

## Authority and source boundary

Use the canonical specification and requirements matrix in this
package. Later owner amendments and C-01–C-08 override conflicting
earlier interpretations. Original Q1–Q25 records and Q25A have now been read in the signed-in
source chat; the updated local transcript supplies the approved
consolidated baseline and full recovered register (S6/S7).

Prepare and preserve the independent design before inspecting any
pre-existing implementation or proprietary dataset. This package
was prepared without inspecting either. Do not use the existing
system to fill missing requirements.

## Two release gates

**Gate 1 — bounded end-to-end proof.**
Demonstrate capture through reviewed Shopify draft creation with
known-good and known-bad fixtures. Prove copy identity, disclosed
uncertainty, privacy isolation and duplicate-free retries.
The five-book roster is: modern ISBN book; pre-ISBN TSR stock-code
book; boxed set graded box/contents separately; PoD copy; and a
second copy of an already captured title. Use the existing isolated
development store.
The pre-ISBN TSR case must identify title by stock code and either
establish printing from evidence or say “printing unverified”.
Guessing printing fails. No live publication is part of Gate 1.

**Gate 2 — production readiness.**
Process 50 books end to end; measure desktop effort per listing
against the two-minute target. Prove operational recovery,
authorisation, reconciliation,
copy-specific storefront and feeds, app-write conflict handling,
owner-controlled publication and narrow emergency suspension.
Inventory every app with product write access, including apps
writing book metafields. An unassessed writer blocks go-live.
Gate 1 passing never implies Gate 2 passing. Passing Gate 2 never
authorises autonomous publication. A new copy under a published
parent must remain unpurchasable across all enabled channels until
the owner-controlled release. AT-29 is mandatory at both gates.

**Later** scope is explicit in the approved consolidated baseline:
full historical Shopify migration; demand/notifications; trade-in and
collection workflows; advanced intelligence; full customer-impact
cases; detailed cost allocation; sold-variant retirement; and new
collectible categories. Preserve Gate 2 identity/history/nullable
cost foundations and manual holds without implementing those full
workflows.

The recovered allocation permits a simpler Gate 1 capture path.
Full hybrid/dual capture, adaptive evidence, location workflow,
reference promotion and qualified bulk approval are Gate 2 work.
This allocation is distinct from an owner-approved Q32 scope cut.
 No essential safety invariant
can be moved to Later merely to improve the apparent result.

## Fixed budget proposal

The numerical estimates below are introduced planning estimates,
not recovered owner-approved numbers. Ratify them before building.

A work session is one bounded agent work interval with an evidence
receipt, at most two elapsed hours. It is an estimating unit,
not a guarantee of continuous execution or billable human time.

Gate 1 cap: **16 agent sessions**.
Confidence: low until device/runtime choices and representative
implementation throughput are validated.
Breakdown:

- Source verification and executable fixture contracts: 2.
- Copy model, evidence provenance and local persistence: 3.
- Minimal durable capture input and desktop review path: 3.
- Draft provisioning and idempotent retry/reconciliation: 3.
- Positive and negative fixture execution and repair: 3.
- Evidence packaging and gate review: 2.

Gate 2 cap, revised proposal: **24 additional agent sessions**.
Confidence: low; subject to Gate 1 evidence and owner ratification.

- Hybrid iOS, dual desktop/CZUR fallback, templates/adaptive capture: 4.
- Roles, reference promotion, claims and operational policy: 3.
- Shopify lifecycle, concurrency and historical foundations: 5.
- Theme, structured data and variant feed verification: 4.
- Privacy, portable export, restore and recovery: 3.
- Product-writer assessment, exception centre and emergency controls: 3.
- Full acceptance execution and deployment review: 2.

The earlier 20-session Gate 2 proposal omitted an explicit allowance
for the full hybrid/dual-capture work. This source-reconciliation
revision proposes four additional sessions before any budget has
been ratified. It is not an owner-approved increase or an authorised
Q32 reset. The owner may accept or reject the revised estimate.

No unpriced human implementation effort is assumed. If humans are
needed, record named tasks and estimated hours separately and seek
a revised budget before consuming them.

**Owner attention cap, proposed:** five Gate 1 decision events:

1. Review and ratify this five-file package, allocation and budget.
2. Confirm the fixture roster and initial capture/condition policy.
3. Resolve one batched set of policy exceptions.
4. Decide at the single 50% checkpoint.
5. Accept or reject the Gate 1 evidence.

Gate 2 attention cap, proposed: four decision events covering
production policy, writer/conflict assessment, acceptance evidence,
and go-live. These are separate from Gate 1.

Count actual decisions, not merely meetings. A batch containing
three independent approvals consumes three decisions. Unexpected
decisions are reported against the cap; agents cannot silently
exclude them from the count.

## The one checkpoint

Q32 defines one checkpoint at 50% of the Gate 1 build cap:
**after session 8 of 16**. Do not add recurring renegotiation
checkpoints. Gate 2 has a fixed proposed cap and final acceptance;
a further midpoint checkpoint requires explicit owner agreement.

Report:

- What works end to end, with reproducible evidence.
- What does not work and what is blocking it.
- Sessions spent, remaining and forecast to finish.
- Owner decisions consumed and forecast remaining.
- Any proposed cut, its exact test impact and resulting gate name.

If the forecast exceeds the cap, propose the cut ladder at that
checkpoint. Only the owner may approve reduced scope or a new cap.
A forecast does not itself confer approval.

## Cut ladder, in this exact order

1. Replace automated enrichment, including OCR and external
   lookups, with manual entry. Flag fields as manual.
2. Reduce five books to four; drop the boxed set first.
3. Replace adaptive capture with a fixed photo checklist.
4. Replace the desktop review screen with the simplest list.

Retain prior cuts when applying the next one. Record cuts proposed,
approved, rejected and applied. If the owner has not approved a
needed reduction and the cap cannot support the gate, stop at the
cap and report the unfinished work.

A reduced gate has a different name, for example
“Gate 1-R1: four-book manual-entry proof”. Record exact deviations.
Never report it as the original gate having passed.

## Never cut

Draft-only creation; duplicate-free retries; each copy as its own
record; evidence-based claims and explicit printing uncertainty;
privacy isolation; known-good/known-bad testing.

The emergency suspension exception does not grant publication,
content editing, product unpublishing or automatic restoration.

## Reset and second miss

Only the owner can approve one budget reset. Log original
assumptions, actual outcomes, estimate error, cause and revised
forecast in the evidence log. A second budget miss requires a full
re-plan, not another extension. Estimates are learning evidence.

## Work order and evidence

1. Verify the reconciled S6/S7 decision and precedence manifest.
2. Ratify gate scope, budget, fixture manifest and dependency choices.
3. Build the minimum four-component path using synthetic data first.
4. Run each positive and negative Gate 1 fixture.
5. Hold the single checkpoint at the prescribed spend.
6. Finish within the ratified scope or report the named reduced gate.
7. Obtain owner acceptance of the Gate 1 evidence.
8. Execute Gate 2 and its writer inventory before go-live.
9. Present publication/deployment evidence for owner control.

Each gate receipt records requirement IDs, fixture IDs, input hashes,
expected and actual results, side effects, environment, build
identifier, failures, remaining debt and owner decision.
“Not run”, “blocked” and “failed” are distinct from “passed”.
Documentation preparation runs no acceptance tests.

## Review and commit boundary

The five documents and README are reviewed together.
The owner subsequently authorised upload and placement on main
for sharing with Josh. This source-reconciled revision preserves
review status and does not imply spending, implementation,
production Shopify access or deployment approval.
No pre-existing implementation or proprietary dataset was inspected.

## Current review queue and circle-back

HITL-B1: source recovery CLOSED. Original Q1–Q25, complete Q9 and
Q25A are supported by S6; S7 supplies the approved final baseline,
full recovered register and release-classification table.
No missing requirement has been silently dropped or moved to Later.

HITL-B2: review reconciled package, ratify numerical budgets and
owner-attention caps, and define timing acceptance.
Owner: Dave. Trigger: before implementation.
The 120-second target has no recovered aggregation/outlier rule.
The revised 24-session Gate 2 proposal is explicitly unapproved.

HITL-B3: choose framework/providers and agree material expenditure.
Owner: Dave after implementer prepares costed options.
Trigger: before the affected stage. No purchase is authorised.

TEAM-B4: prove live-parent staging across all enabled channels.
Owner: authorised implementer. Trigger: Gate 1 AT-29 and Gate 2
channel certification. No production inspection/mutation now.

TEAM-B5: demonstrate worker isolation with the real worker identity
and no elevated credentials available in the process.
Owner: authorised implementer. Trigger: Gate 1 privacy proof,
rechecked at Gate 2. Separate schemas alone do not pass.

Circle-back: source and approved deferrals are reconciled across
specification, requirements, tests, plan, BOM and README.
Q15/Q21/Q25 are interpreted under C-01/C-06/Q31, not resurrected
as production-group splitting or autonomous publication.
The suite now contains 43 named contracts, with Later portions
explicitly excluded from Gate 2 execution requirements.
No software gate test is represented as executed.

Local saved 0.1 drafts predate this GitHub reconciliation.
The reviewed remote revision is the sharing copy; refresh local
deliverables when filesystem write access is available.

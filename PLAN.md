# Reliquary Ingest — delivery plan

**Review draft · v1.0-RC · 19 October 2026**

Target: Dave-Meloncelli/Reliquary.capture.
Design approval is recorded. Document review, budget ratification,
implementation, commits and deployment are separate decisions.
This document authorises none of those actions.

## Authority and source boundary

Use the canonical specification and requirements matrix in this
package. Later owner amendments and C-01–C-08 override conflicting
earlier interpretations. Unrecovered decisions stay unresolved.

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

**Later** work is explicitly excluded from a gate only by the
reviewed requirements allocation. No essential safety invariant
can be moved to Later merely to improve the apparent result.

## Fixed budget proposal

The numerical estimates below are introduced planning estimates,
not recovered owner-approved numbers. Ratify them before building.

A work session is one bounded agent work interval with an evidence
receipt, at most two elapsed hours. It is an estimating unit,
not a guarantee of continuous execution or billable human time.

Gate 1 cap: **16 agent sessions**.
Confidence: low until missing source decisions are reconciled.
Breakdown:

- Source reconciliation and executable fixture contracts: 2.
- Copy model, evidence provenance and local persistence: 3.
- Mobile capture and desktop review path: 3.
- Draft provisioning and idempotent retry/reconciliation: 3.
- Positive and negative fixture execution and repair: 3.
- Evidence packaging and gate review: 2.

Gate 2 cap: **20 additional agent sessions**.
Confidence: low; subject to Gate 1 evidence and owner ratification.

- Permissions, roles and operational policies: 3.
- Shopify lifecycle and concurrency reconciliation: 5.
- Theme, structured data and variant feed verification: 4.
- Privacy, restoration and operational recovery: 3.
- Product-writer assessment and emergency controls: 3.
- Full acceptance execution and deployment review: 2.

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

1. Reconcile approved source and resolve all unallocated requirements.
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

These five local drafts are the complete requested output.
Review them together. No repository checkout, existing-system
inspection, remote writes, commit, purchase or deployment is part
of this drafting task.

## Current review queue and circle-back

HITL-B1: missing approved source. Recover Q10 to Q25, Q9's
truncated remainder and earlier capture amendments.
Owner: Dave supplies source if retrieval remains unavailable;
drafting agent reconciles it. Trigger: before complete canonical
status or implementation. No requirement is dropped by this gap.

HITL-B2: ratify proposed gate allocations, numerical budgets and
the timing rule. Owner: Dave. Trigger: after B1, before implementation.
The 120-second target has no recovered aggregation/outlier rule.

HITL-B3: choose framework/providers and agree material expenditure.
Owner: Dave after implementer prepares costed options.
Trigger: before the affected stage. No purchase is authorised now.

TEAM-B4: design and prove live-parent staging across enabled sales
channels. Owner: authorised implementer. Trigger: Gate 1 AT-29 and
Gate 2 channel certification. No existing live product is inspected
or modified by this documentation task.

TEAM-B5: demonstrate worker isolation with the real worker identity
and no elevated credentials available in the process.
Owner: authorised implementer. Trigger: Gate 1 privacy proof;
recheck at Gate 2. Separate schemas alone do not pass.

Circle-back result: Q26A/Q26 to Q31 were recovered from the export;
Q32/Q33 and audit decisions came from the accessible chat;
Q1 to Q9 came from an explicitly reconstructed register.
Q10 to Q25 remain absent. The five files are review drafts,
not evidence that source-complete classification or acceptance passed.

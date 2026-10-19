# Reliquary.capture

Independent design and review package for **Reliquary Ingest**,
RPG Reliquary's physical-stock capture and Shopify draft-preparation
application.

## Start here

The owner has approved **Design Baseline v1.0-RC**.
The documents in this repository are **review drafts**.
Their placement on `main` makes them available for review; it does
not approve numerical budgets, implementation or production readiness.

Suggested reading order:

1. [Design specification](DESIGN_SPECIFICATION.md):
   scope, authority, evidence, privacy, architecture and unresolved
   design details.
2. [Requirements matrix](REQUIREMENTS.md):
   Q1–Q33, amendments, audit resolutions, evidence status,
   recovered Gate 1/Gate 2/Later allocation and test references.
3. [Acceptance test plan](ACCEPTANCE_TEST_PLAN.md):
   physical-book fixtures and 43 named positive/negative test
   contracts, including fault injection and publication safeguards.
4. [Delivery plan](PLAN.md):
   two release gates, proposed effort and owner-attention budgets,
   the single 50% Gate 1 checkpoint and ordered scope-cut rules.
5. [Bill of materials](BOM.md):
   dependencies, cost drivers and explicitly TBD expenses.

## Source reconciliation and review status

The original signed-in **App Capture Concept** conversation is now
readable. Its Q1–Q25 decision records, complete Q9 and Q25A dual-
capture amendment have been checked directly. Q26A/Q26–Q33 and the
eight final audit resolutions are also accounted for.

The updated local transcript supplies the approved final consolidated
baseline, full recovered register and release-allocation table.
The earlier “Q9 truncated / Q10–Q25 unrecovered” notices are resolved.
See the specification's source register for provenance and precedence.
The [preserved baseline source](BASELINE_SOURCE.md) contains the
approved consolidated text, owner approval and a separately labelled
reconstructed register so review does not depend solely on chat access.

Recovered scope explicitly defers full historical migration,
customer demand/notifications, trade-in/collection workflows,
advanced intelligence, full customer-impact cases and detailed cost
allocation. Essential identity/history, nullable cost foundations
and manual safety controls remain in the production MVP.

The acceptance tests are specified, not implemented or executed.
Gate 1's 16-session and Gate 2's revised 24-session effort caps are
proposals awaiting owner ratification. Attention estimates are
10 distinct Gate 1 decisions and 8 Gate 2 decisions, also unratified. Unknown expenses are TBD,
not zero. Technologies and unselected mechanisms remain proposals.

## Design rules to preserve

- A product groups **title + edition + release**; each physical
  copy is its own record and Shopify variant.
- Printing and production identity come from that copy's evidence.
  Uncertainty is disclosed rather than guessed.
- The application prepares drafts; the owner controls publication.
  A new copy under an already-live product must remain unavailable
  on every enabled sales channel until owner-controlled release.
- Emergency automation is limited to suspending one affected
  copy's availability, with a critical alert and owner-controlled
  restoration.
- Mobile and desktop/CZUR capture are first-class Gate 2 workflows,
  with file-import fallback and a shared physical-copy identity.
- Processing is local-first. External enrichment receives only
  permitted task data; commercial and personal data remain isolated.
- The MVP backend has four components: web application, background
  worker, database and object store. The queue is database-backed.
- The independent baseline must remain free from adaptation to the
  owner's pre-existing implementation or proprietary dataset.

## Review focus

For Josh and other reviewers, prioritise:

- Source traceability, supersession and the recovered release scope.
- Gate 2's synthetic provider-comparison harness, kept separate from
  any later access to the existing proprietary system/dataset.
- Live-parent variant exposure across storefront, cart and feeds.
- Demonstrable worker credential isolation, beyond separate schemas.
- Positive and negative fixtures that cannot pass vacuously.
- Feasibility of the budgets and the four-component operating model.

Use the specification and requirements matrix to identify the
decision or test behind each review finding. Reviewing this package
does not authorise Shopify changes, implementation or deployment.

## Review tracking

See [Circle-back receipt](CIRCLE_BACK.md) for the latest documentation
checks and [owner review queue](HITL_QUEUE.md) for decisions required
before implementation. These do not constitute software gate results.

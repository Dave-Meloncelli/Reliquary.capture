# Reliquary.capture

Independent design and review package for **Reliquary Ingest**,
RPG Reliquary's physical-stock capture and Shopify draft-preparation
application.

## Start here

The owner has approved **Design Baseline v1.0-RC**.
The documents in this repository are **review drafts**.
Their placement on `main` makes them available for review; it does
not certify source completeness, approve the proposed budgets or
demonstrate production readiness.

Suggested reading order:

1. [Design specification](DESIGN_SPECIFICATION.md):
   scope, authority, evidence, privacy, architecture and unresolved
   design details.
2. [Requirements matrix](REQUIREMENTS.md):
   Q1–Q33, amendments, audit resolutions, evidence status,
   proposed Gate 1/Gate 2/Later allocation and test references.
3. [Acceptance test plan](ACCEPTANCE_TEST_PLAN.md):
   physical-book fixtures and 30 named positive/negative test
   contracts, including fault injection and publication safeguards.
4. [Delivery plan](PLAN.md):
   two release gates, proposed effort and owner-attention budgets,
   the single 50% Gate 1 checkpoint and ordered scope-cut rules.
5. [Bill of materials](BOM.md):
   dependencies, cost drivers and explicitly TBD expenses.

## Important review limits

The available sources directly support Q26A and Q26–Q33,
together with the eight final audit resolutions.
Q1–Q9 are represented by a reconstructed decision summary;
Q9 is truncated. Q10–Q25 and earlier capture amendments remain
unrecovered and explicitly unallocated.

The requirements distinguish directly supported decisions,
reconstructed decisions and implementation proposals.
Resolve these source gaps before certifying the package as the
complete canonical baseline or starting implementation.

The acceptance tests are specified, not implemented or executed.
Numerical budgets and release allocations remain proposals for
owner review. Unknown expenses are TBD, not assumed to be zero.

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
- Processing is local-first. External enrichment receives only
  permitted task data; commercial and personal data remain isolated.
- The MVP backend has four components: web application, background
  worker, database and object store. The queue is database-backed.
- The independent baseline must remain free from adaptation to the
  owner's pre-existing implementation or proprietary dataset.

## Review focus

For Josh and other reviewers, prioritise:

- Source traceability and unresolved requirements.
- Live-parent variant exposure across storefront, cart and feeds.
- Demonstrable worker credential isolation, beyond separate schemas.
- Positive and negative fixtures that cannot pass vacuously.
- Feasibility of the budgets and the four-component operating model.

Use the specification and requirements matrix to identify the
decision or test behind each review finding. Reviewing this package
does not authorise Shopify changes, implementation or deployment.

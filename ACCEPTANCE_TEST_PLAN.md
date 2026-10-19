# Reliquary Ingest: acceptance test plan

**Review draft 0.1 | Baseline v1.0-RC | 19 October 2026**

Target: Dave-Meloncelli/Reliquary.capture.
Tests below are specifications, not executed tests.
No Shopify mutation, fixture processing or publication has run.

## Evidence contract and fixtures

Each AT identifier names an automated test contract to implement.
Manual approvals, image evidence and measurements become captured
fixture inputs checked by the named automation.

For every test run record build/configuration, environment, input
fixture IDs and SHA-256 hashes, expected and observed assertions,
record counts, side effects, output artefacts and execution time.
Use synthetic sensitive data and an isolated development store.
A disabled path is explicit, not treated as fully tested.

Execute each test twice: known-good input must PASS; deliberately
known-bad input must FAIL for the expected assertion. A negative
scenario safely rejected by the application is a passing control
test; feeding a forbidden output to the acceptance validator must
make that validator fail. Record both to avoid confusing the two.

Every validator checks expected fixture count and assertion count.
Zero fixtures, skipped checks, a missing scenario or an unexecuted
negative case fails the gate. A gate has no “pass by absence”.

Physical Gate 1 roster:

- F01: modern book with ISBN and human-confirmed identity.
- F02: pre-ISBN TSR book with photographed stock code. Printing
  evidence may establish printing or leave it unverified.
- F03: boxed set, separately graded box and contents.
- F04: PoD copy, with copy-specific evidence for that status.
- F05: second physical copy of a title already captured, same
  edition and release. It must join the product as a separate copy.

Assign each a permanent copy ID, SKU, grade, approved price,
capture/final location as applicable and required photos.
Record expected product groups before running. Where F05 duplicates
F01's title/edition/release, five copies yield four products and
five variants. F02 “printing unverified” is a valid outcome.

Additional fixtures:

- FX-LIVE: published parent with one approved sibling and a newly
  captured, unapproved copy; enumerate every enabled sales channel.
- FX-GPS: import containing GPS metadata and known pixel digest.
- FX-PRIVATE: visible personal inscription and commercial/private
  schema canary values, all synthetic.
- FX-RERUN: same original, two disagreeing consequential results.
- FX-FAULT: ambiguous write timeout, duplicate/out-of-order events,
  interrupted upload, expired lease and killed worker.
- FX-50: manifest of 50 distinct physical books with expected
  copy/group relationships and approved truth records.
- FX-WRITERS: complete declared app-writer inventory, including a
  book-metafield writer, plus an unassessed-writer mutation.

Golden truth is signed off by an authorised human and frozen before
testing. Mutant fixtures change one load-bearing property at a time.
Record mutations so a failure has an identifiable cause.

## Gate 1 tests and continuing invariants

### AT-01: copy identity, grouping and complete draft proof

Gate: 1, repeated at 2. Source: Q1/Q4/Q6/Q31, C-01.
Good: F01 to F05 reach accurate drafts with their own grade, price
and photos; F05 shares the correct product and has a unique variant.
Bad: merge F05 into another copy; duplicate the product; omit one
book or assign a sibling's photos. Validator must reject each.
Assertions: manifest count, unique copy/SKU mapping, exact grouping,
variant count, grade/price/media match and draft/publication state.

### AT-02: copy-specific production evidence

Gate: 1 and 2. Source: Q1, C-01, Q32.
Good: stock-code title match for F02; unsupported printing stays
“printing unverified”. F04's PoD status has its own evidence.
Bad: infer F02 first printing from its product or sibling; label
F04 original without evidence. Assert claim-to-copy evidence and
reject unsupported collector-sensitive output.

### AT-03: reference promotion is distinct from listing approval

Gate: 1 minimal, 2 full. Source: Q2/Q29.
Good: OCR creates candidate; authorised reference promotion records
evidence/version/actor; listing approval alone does not promote it.
Bad: candidate auto-promotes or inventory approver gains reference
authority. Assert roles, candidate state and promotion audit.

### AT-04: condition, completeness and sealed handling

Gate: 1 book/box, 2 full templates. Source: Q3/Q7.
Good: F03 box and contents have separate grades and evidence;
defects and omissions create exceptions; sealed policy uses allowed
external evidence without opening.
Bad: AI overwrites human grade, components share an unjustified
single grade or template demands opening sealed stock. Assert policy
outcome, stored human assessment and review state.

### AT-05: durable, nonblocking capture

Gate: 1 and 2. Source: Q5/Q8; earlier amendment unresolved.
Good: capture while offline, interrupt/restart app, reconnect and
resume each image once with truthful queued/uploaded states.
Slow enrichment does not block further local capture.
Bad: lose a queued image, mark failed upload synced, duplicate media
on resume or block capture waiting on AI. Assert persisted copy/media
count, content hashes, queue state and UI event sequence.

### AT-06: ambiguous retry and repeated approval

Gate: 1, expanded fault matrix at 2. Source: Q4/Q30/Q31/Q32.
Good: remote write succeeds but response is lost; retry reconciles
to the same product/variant. Repeated approval is idempotent.
Bad: retry creates a second sellable copy or treats uncertain
remote outcome as permission to create afresh.
Assert exact copy-to-remote mappings and sellable-copy counts.

### AT-07: sale, retained sold copy and no resurrection

Gate: 1 and 2. Source: Q4/Q31, C-07.
Good: simulated sale makes the selected copy unavailable; sibling
quantity is unchanged, sold variant/history remains. Metadata
refresh and duplicate sale events do not restore stock.
Bad: delete sold history, zero sibling or reset sold quantity to one.
Assert per-copy quantities, retained IDs and sync payload exclusions.

### AT-08: output evidence and commercial disclosure boundary

Gate: 1 enabled outputs, 2 every surface. Source: Q1/Q27/Q31, C-04.
Good: disclose F04's factual PoD status while withholding canary
PoD-market availability/pricing intelligence.
Bad: unsupported “first printing”, canary supplier/cost/customer data
or PoD-market intelligence in description, options, tags, metafields
exposed to customers, images, structured data or channel feeds.
Assert every declared output surface is enumerated and scanned;
an unenumerated enabled surface blocks the test.

### AT-09: local-first fallback and provider governance

Gate: 1 if enabled; 2 full. Source: Q27, C-04.
Good: local success makes zero external calls; local failure invokes
only a reviewed, compliant provider with exact task allowlist.
Audit includes provider, purpose, fields, digest, timestamp/outcome.
Bad: external-first call, unregistered provider, training-permitted
terms, missing audit or broadened payload on timeout.
Assert observed calls and serialized payload keys/hashes.
If no compliant fallback exists, the application stops or uses
manual entry. A blocked call is expected, not a waived criterion.

### AT-10: location-free originals and safe derivatives

Gate: 1 and 2. Source: Q27/Q28.
Good: FX-GPS loses all location metadata before local or remote
persistence; decoded pixel digest is unchanged; SHA-256 of the
resulting canonical file matches its evidence record.
Derivatives have no metadata and are cropped to the item.
Bad: retain import bytes with GPS in temp/queue/object storage,
alter canonical pixels, hash pre-sanitisation bytes or disclose
bench surroundings. Assert storage writes and derivative lineage.

### AT-11: actual worker credential denial

Gate: 1 minimal, 2 exhaustive. Source: Q27/Q30.
Good: run the real worker identity and attempt direct SQL, views,
functions, joins and connection reuse against synthetic sensitive
schemas. Every read fails with permission denial; allowed
bibliographic/evidence reads succeed.
Bad: grant a sensitive role, expose an inherited credential or use
an elevated connection pool. Validator must detect readable canaries.
Inspect process configuration and task boundaries: the worker must
not hold elevated secrets even if normal queries omit them.
If single-process execution cannot enforce this, fail the design
proof. Do not add a fifth component or relax isolation silently.

### AT-12: policy exceptions and qualified approval

Gate: 1 minimal, 2 bulk. Source: Q3/Q9(partial)/Q26.
Good: consistent evidence-qualified records can proceed; missing
evidence, material defects and authenticity conflicts create
individual exceptions and cannot pass bulk approval.
Bad: bulk path bypasses an unresolved exception.
Assert policy decisions, selected records and exception links.
Full Q9 acceptance remains pending source recovery.

### AT-13: approval binds reviewed versions

Gate: 1/2 proposal pending review. Source: introduced mechanism;
related Q2/Q9(partial)/Q29.
Good: unchanged reviewed revision is approved; later material edit
requires fresh approval. Historical approvals retain old references.
Bad: silently apply stale approval to changed price/grade/evidence.
Assert revision comparison and preserved historical links.

### AT-14: returns and external inventory events

Gate: 2. Source: Q4.
Good: reservation/refund/adjustment and out-of-order events reconcile
with current Shopify state. Refund does not authorise returned stock
to become sellable without physical inspection.
Bad: refund alone restores availability or delayed event overwrites
current sold state. Assert remote reconciliation and inspection link.

### AT-15: supported-device recovery

Gate: 2. Source: Q5.
Good: supported iOS and desktop versions retain capture state after
restart and interrupted upload; show consistent canonical workflow.
Bad: one supported client loses durable images or falsely reports
completion. Record device/version matrix; no empty client matrix.

### AT-16: final physical location preflight

Gate: 1 identity, 2 publication preflight. Source: Q6.
Good: capture staging location and audit move to final location.
Bad: publication readiness with staging-only location or treating a
Shopify location ID as physical shelf evidence. Assert preflight denial.

### AT-17: configurable item templates

Gate: 2. Source: Q7.
Good: book, boxed set and simple accessory apply their own minimum
evidence/completeness policy. Bad: wrong template permits missing
components or demands opening a sealed item.
Assert selected template/version and required evidence list.

### AT-18: adaptive capture and approved fallback

Gate: 1 and 2. Source: Q8/Q32.
Good: missing stock/printing evidence requests an extra slot that
may be deferred; an approved reduced gate uses the fixed checklist.
Bad: missing required evidence disappears, or checklist replaces
adaptive capture without an approved reduction record.
Assert request lifecycle, pending exceptions and gate name.

## Gate 2 operational and channel tests

### AT-19: narrow emergency suspension and alert lifecycle

Gate: 2. Source: Q26, C-06.
Good: authenticity flag or sale elsewhere suspends only the affected
copy, produces a critical case and permits restoration only after
owner approval and current-state checks.
Inject Shopify rejection: case stays unresolved and exposure visible.
Bad: content edit, product unpublish, sibling inventory change,
automatic restoration or “alert delivered” treated as resolution.
Assert exact allowed mutations and separate delivery, acknowledgement,
suspension and resolution timestamps.

### AT-20: restricted access and privacy tombstone

Gate: 2; before any earlier privacy-exception path. Source: Q28, C-05.
Good: authorised original read is audited; unauthorised read denied.
Approved deletion/restriction removes access to original and affected
derivatives; tombstone has only hash, reason, authoriser and time.
Restored backups reapply restrictions before becoming accessible.
Bad: unaudited read, silent overwrite, sensitive tombstone, lingering
public derivative or restored deleted content becoming visible.

### AT-21: supersession and consequential run provenance

Gate: 1 minimal, 2 full. Source: Q28/Q29.
Good: retake creates a new image; FX-RERUN produces a new run ID,
input hash/references, version/configuration, claims and review.
Older artefacts and approval links remain; disagreement is flagged.
Bad: overwrite a prior result, lose claim-to-run association, omit
engine/configuration or repoint an old approval to new evidence.
Assert hashes, immutable IDs, lineage and audited correction actor/time.

### AT-22: backup and recovery rehearsal

Gate: 2. Source: Q30/Q31.
Good: use the documented recovery command with stated prerequisites;
restore database/jobs, evidence objects and restrictions to a clean
authorised environment. Reconcile Shopify before resuming writes.
Bad: missing image, mismatched job/copy state, unreapplied restriction
or replay creates duplicate inventory.
Assert manifest/hash consistency and no duplicate sellable copies.
Recovery-point/time objectives are TBD until agreed; record actuals.

### AT-23: four components and enforced boundaries

Gate: 1 and 2. Source: Q30.
Good: deployment inventory is web, worker, database, object store.
Database jobs use tested locks/leases; module import/access checks pass.
Routine operations fit one command/screen; health summary is produced.
Bad: undeclared broker, privileged cross-module access, two workers
claim the same active job or expired lease repeats a sellable write.
Assert component count, boundary tests, queue recovery and summary receipt.

### AT-24: controlled CLI, environment and rollback

Gate: 1 development, 2 deployment. Source: Q26A.
Good: isolated existing dev store, separated identities, no secrets
in tracked content, versioned app/theme config, authorised deployment
with validation and rollback rehearsal; runtime works without CLI.
Bad: wrong-store target, committed secret, unauthorised production
mutation, unversioned configuration or runtime depends on CLI session.
Assert environment target and approval scope before mutations.

### AT-25: variant picker, feeds and structured data

Gate: 2. Source: C-02/C-07.
Good: two available copies with different grades/prices produce
correct individual offers/feed items. Sold variant retained but absent
from copy picker and feed. Product has no misleading copy-wide condition.
Bad: product-level grade copied from one variant, wrong variant price,
sold copy selectable or included in a feed.
Assert every enabled channel and direct variant/cart access, not only UI.

### AT-26: every product-writing app assessed

Gate: 2. Source: C-03.
Good: complete access inventory including metafield writer has
documented field ownership, conflict policy and assessment evidence.
Bad: inject an unassessed writer or omit one declared writer.
Assert inventory completeness and go-live is blocked.
A zero-writer inventory contradicting fixture truth must fail.

### AT-27: two-budget checkpoint and cut governance

Gate: before/through Gate 1. Source: Q32, C-08.
Good: ratified cap, session ledger and decision ledger trigger the
single 50% checkpoint; overrun forecast proposes ordered cuts for
owner decision with exact reduced-gate name.
Bad: skipped checkpoint, unapproved cap extension, out-of-order cuts,
hidden owner decisions or reduced gate reported as original pass.
Assert spend, decision count, checkpoint count and authority record.

### AT-28: non-negotiables and reset limit

Gate: 1 and continuing. Source: Q32, C-04/C-08.
Good: cut automation before book count, then adaptive capture, then
review complexity; preserve all never-cut controls. One authorised
reset has an estimate-error receipt; second miss triggers full re-plan.
Bad: remove privacy/retry/claim tests, guess TSR printing, quietly
extend a second time or treat missing approval as approval.

### AT-29: unapproved copy under a live parent

Gate: 1 mandatory negative proof; 2 every enabled channel.
Source: owner publication rules Q31, C-01 and supplied clarification.
Good: FX-LIVE's new copy stays unpurchasable and absent from public
copy/feed offers until owner-controlled release; approved sibling
remains unchanged. Draft creation alone is not sufficient evidence.
Bad: new variant becomes available by parent association, direct
cart/checkout, channel API or feed without owner publication.
Assert all enabled channels against an explicit inventory.
If a channel is untestable, fail readiness for that channel.
The staging mechanism is TBD; no particular API flag is presumed
to provide cross-channel isolation.

### AT-30: nonvacuous source and gate evidence

Gate: documentation closure and both release gates.
Source: Q31/Q33 and traceability clarification.
Good: every required criterion has sources, evidence status,
allocation, paired good/bad results and nonzero assertions.
Bad: missing Q10 to Q25 source, truncated Q9 presented as complete,
unexecuted test marked passed, empty fixture set or missing negative.
Assert expected requirement/test/fixture manifests. This draft
currently fails source-complete closure by design; that is recorded.

## Gate execution rules

Gate 1 requires F01 to F05 and relevant AT-01 to AT-13, AT-16,
AT-18, AT-23/24 development portions, AT-27/28 and AT-29/30.
AT-13 is a proposed safeguard pending package review.
Disabled enrichment means manual provenance and denied external
calls are still tested. It does not waive privacy isolation.

Gate 2 reruns continuing controls plus every production portion,
AT-14 to AT-26, AT-29 and AT-30, against FX-50.
All 50 must have completed end-to-end evidence; 49/50 fails.
Measure active desktop effort per listing separately from capture
and service waiting. Report all observations and distribution against
120 seconds. Timing aggregation/outlier acceptance requires owner
ratification before execution; do not invent a passing statistic.

For Gate 2 fault injection, kill a worker after remote success but
before local acknowledgement, interrupt uploads and repeat approvals.
No duplicate sellable copy is tolerated.

Fixtures, automation and gate executions remain to be implemented.
Source gaps must be resolved before this plan can be called the
complete acceptance plan for Q1 to Q33.

# Reliquary Ingest: acceptance test plan

**Review draft 0.3 | Baseline v1.0-RC | 19 October 2026**

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

Gate: 2; no automatic reference promotion permitted in Gate 1.
Source: Q2/Q29.
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

Gate: 1 minimal, 2 bulk. Source: complete Q3/Q9/Q26.
Good: consistent evidence-qualified records can proceed; missing
evidence, material defects and authenticity conflicts create
individual exceptions and cannot pass bulk approval.
Bad: bulk path bypasses an unresolved exception.
Assert policy decisions, selected records and exception links.
Assert immediately-before-approval server revalidation, explicit
batch authority, eligible/excluded summary and the operator/time/
listing-revision/evidence/policy-version approval record.

### AT-13: approval binds reviewed versions

Gate: 2 bulk workflow; Gate 1 stale-approval safety on queue/retry.
Source: complete original Q9, Q2/Q29. This is now source-backed.
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

Gate: 2 adaptive workflow; approved reduced Gate 1 scope as applicable.
Source: Q8/Q32 and final allocation in the consolidated baseline.
Good: missing stock/printing evidence requests an extra slot that
may be deferred; an approved reduced gate uses the fixed checklist.
Bad: missing required evidence disappears, or checklist replaces
adaptive capture without an approved reduction record.
Assert request lifecycle, pending exceptions and gate name.

## Gate 2 operational and channel tests

### AT-19: narrow emergency suspension and alert lifecycle

Gate: 2. Source: Q26, C-06, final consolidated baseline.
Good: authenticity flag or sale elsewhere suspends only the affected
copy, produces a critical case and permits restoration only after
owner approval and current-state checks.
Inject Shopify rejection: case stays unresolved and exposure visible.
Bad: content edit, product unpublish, sibling inventory change,
automatic restoration or “alert delivered” treated as resolution.
Assert correct copy, variant and Shopify inventory location, current
state/concurrency protection, exact allowed mutations and separate
delivery, acknowledgement, attempted/failed/confirmed suspension
and resolution timestamps. Wrong location or unconfirmed remote
state must fail, even if a worker reports success.

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
Source: Q31/Q33; S6 original decisions and S7 final baseline.
Good: all Q1–Q33 plus Q25A/Q26A, C-01–C-08 and applicable
requirements have source/evidence, dependency, allocation and paired
good/bad contracts. Executed gate receipts have nonzero assertions.
Bad: delete a source/requirement, revive superseded Q15 grouping,
claim missing or reconstructed source is verified, mark unexecuted
checks passed, use empty fixture set or omit the negative case.
Assert exact question/amendment/audit/test manifests and precedence.
Source coverage can pass document validation without software
acceptance passing. All software tests remain specified, not run.

## Additional recovered requirement tests

### AT-31: tiered processing, spend and replaceable providers

Gate: 2; enabled Gate 1 provider paths must meet privacy/spend controls.
Source: Q10/Q19/Q27.
Good: local ISBN/stock/OCR/catalogue result prevents unnecessary AI;
identical allowed requests deduplicate. Count costs per item, batch,
operation and provider; cap blocks expensive rerun until authorised.
Provider outage retains jobs; replacing/disabling an adapter leaves
manual/local operation intact. Record source/version/time/licence.
Bad: external-first disclosure, unmetered retry, budget bypass or
provider mutates trusted references. Assert call order, ledger
amount/status, cap enforcement, denied mutation and preserved inputs.
Gate 2 harness portion: run independent, provider-assisted and
comparative modes on identical synthetic inputs with independently
established truth; report accuracy, time, cost and ambiguity.
A mutant that counts copied upstream evidence as independent truth
must fail. Execution against the owner's actual proprietary dataset
is separately authorised Later work, not a reason to defer the harness.

### AT-32: existing-item collision and SKU reconciliation

Gate: 1 collision safety; 2 operator-controlled reconciliation.
Source: Q11.
Good: bibliography match to existing product creates a separate copy
only when physically distinct; verified same-copy SKU links after
operator confirmation without altering quantity/history/content.
Bad: shared ISBN merges two copies, recapture creates a duplicate,
SKU conflict is ignored or existing product silently overwritten.
Assert explicit linking decision, unchanged history/quantity and
auditable safe unlink. Full catalogue migration remains Later.

### AT-33: independent authenticity hold and specialist authority

Gate: 2; honest Gate 1 uncertainty remains covered by AT-02.
Source: Q12.
Good: uncertain printing remains disclosed; legitimate PoD is not
automatically suspect. Credible unauthorised-copy evidence creates
hold, excludes bulk/publication and is resolved only by an authorised
specialist with evidence/actor/time/outcome. New conflict reopens it.
Bad: AI releases hold, labels counterfeit as verified on its own,
or ordinary uncertainty is falsely treated as confirmed authenticity.
Assert separate printing/authenticity states and denied release.

### AT-34: portable independent catalogue

Gate: 2; stable internal identity foundation at Gate 1.
Source: Q13/Q14.
Good: export documented versioned records/relationships, originals,
claims, conditions and manifests; restore without Shopify/provider
IDs becoming canonical IDs. Verify all hashes and links.
Bad: omit a relationship/image, corrupt a checksum or require a
live Shopify account to interpret permanent identity.
Assert manifest counts, ID namespace separation and independent
restore readability. Multi-cloud automation is Later, not a hidden
production requirement.

### AT-35: selected-copy accessibility and purchase continuity

Gate: 2. Source: Q16, C-02/C-07.
Good: keyboard-select each copy and verify its own photos, production
status, grade, defects, completeness, price, SKU and availability;
screen-reader state agrees. Cart/checkout/fulfilment retain selection.
Missing copy data prevents ambiguous purchase; shared facts stay shared.
Bad: stale sibling photo/grade, wrong selected SKU, inaccessible
control or fallback allows ambiguous checkout.
Assert all fields at each boundary and supported variant capacity.

### AT-36: historical events and unknown-cost foundations

Gate: 2 foundations; detailed allocation and analytics Later.
Source: Q17/Q24.
Good: retain acquisition/listing/sale/return events and known price,
discount/fees/freight with provenance; nullable cost stays unknown.
Approval/pricing can proceed without allocation. Restricted access
and retention apply; later adjustments preserve old event evidence.
Bad: unknown silently becomes zero, missing cost blocks approval,
a correction rewrites a sale or provider can read commercial canaries.
Assert event IDs/order/links, nullable status and output isolation.
Later allocation fixtures: known/allocated/estimated/unknown, lot
expenses, reversed adjustments, no double counting and methodology-
qualified margins. Do not require full allocation to pass Gate 2.

### AT-37: deferred demand, supply and consent

Gate: Later; not a Gate 1/2 release prerequisite.
Source: Q18, final baseline deferred scope.
Good: catalogue-linked wanted title/edition/printing and acceptable
alternative are distinct from supplier offer and completed sale.
Customer consent/preferences govern notification; staff leads and
trade-ins remain separate; interest makes no stock/price promise.
Bad: send without consent, count a supply offer as confirmed demand,
infer procurement guarantee or treat browsing as explicit request.
Assert domain/state distinctions and denied unauthorised send.
Use synthetic contacts; this test plan sends no messages.
Passive tracking/predictive scoring/automatic buying remain deferred.

### AT-38: independent claim corroboration and shared policy

Gate: 1 safety; 2 full policy/dependency evaluation.
Source: Q19/Q20.
Good: truly independent evidence supports a qualified claim; common
upstream provenance remains linked and contradictory claims remain.
Descriptions, back-cover summaries, tags, feeds, metadata and
structured data invoke the same versioned policy.
Bad: mirrored datasets count as independent sources, a derived claim
corroborates its own ancestor, or one output bypasses policy.
Assert source dependency relations, states, presentation decisions
and human override actor/time/evidence. Unclassified output fails.

### AT-39: continuous impact and failed withdrawal exposure

Gate: 2. Source: Q21/Q26, C-06.
Good: material evidence/policy change identifies affected copies,
current surfaces and caches; records review, owner-approved content
correction or narrow emergency suspension, preserving sale history.
Failed/cached withdrawal remains unresolved and alerts.
Bad: automatic live content rewrite, new material assertion without
authority, stale cache ignored or internal invalidation treated as
proof customer exposure ended.
Assert full dependency/surface manifest and observed remote states.

### AT-40: safe regrouping and deferred migration

Gate: 2 manual hold/resolution; full migration Later.
Source: Q22, C-01/C-06.
Good: printing/PoD-only reclassification leaves product group intact.
Edition/release conflict safely holds copy for manual review, retains
identity/SKU/evidence/orders and prevents a second sellable copy.
Bad: automatic cross-product move, active reservation ignored,
printing change creates a duplicate product, or history is rewritten.
Assert gate-appropriate authority and at-most-one sellable mapping.
Later migration fixture requires human-approved destination, failed
step recovery and safe compensation without rewriting completed sales.

### AT-41: exact sale snapshots and deferred remedies

Gate: 2 historical foundation; full case management Later.
Source: Q23/Q17.
Good: freeze represented title/edition/printing/status/condition/
photos/text/price at sale, link order and later correction without
overwriting it; identify affected sale for manual escalation.
Bad: correction rewrites purchase evidence or loses order linkage.
Assert snapshot hashes and original/corrected evidence versions.
Later case fixtures: prioritisation/contact/outcome audit and explicit
human remedy authority; autonomous refund/contact must fail.
No customer contact or financial action is performed by this plan.

### AT-42: outage approval and mandatory resumed-job revalidation

Gate: 1; exhaustive operational recovery at 2.
Source: Q25/Q9, Q31 supersession.
Good: continue capture/review/pricing/approval while Shopify is down.
Durable jobs survive restart; after recovery check evidence, claims,
condition, price, approval revision and current Shopify availability.
Unchanged eligible job prepares the draft once; stale case enters
Attention Required. UI waits for remote confirmation.
Bad: lost queued copy, resumed job publishes live, outdated approval
runs, duplicate variant appears or worker acceptance claims success.
Assert queue/state/approval versions and Shopify-confirmed result.

### AT-43: dual first-class capture and CZUR import fallback

Gate: 2; a simpler Gate 1 input path is permitted by the final baseline.
Source: Q25A/Q5 and operational capture/pricing decisions.
Good: mobile-started copy receives desktop copyright/defect images
without a second copy record. Both paths work independently, share
evidence/condition/barcode/OCR contracts and record device/time/slot.
CZUR direct control is tested if used; unsupported driver uses import.
Condition is captured with the item, pricing at desktop review.
Keyboard controls and appropriate spoken status feedback work.
Bad: desktop needs phone online, device handoff duplicates copy,
unsupported SDK is assumed working, price blocks initial capture
or UI calls an unpersisted image “Locally Saved”.
Assert independent-client runs, shared IDs/hashes, actual persistence,
accessible states and import success. No new camera purchase required.

## Gate execution rules

Gate 1 uses F01–F05, the existing isolated dev store and the minimal
capture path permitted by the final baseline. Mandatory contracts
include AT-01/02/04/05/06/07/08, applicable approval/retry safety
in AT-12/13, privacy AT-09/10/11/20/21 as their paths are used,
architecture/tooling AT-23/24, governance AT-27/28, live-parent
AT-29, nonvacuous evidence AT-30, collision AT-32, claim safety
AT-38 and outage AT-42.
A disabled optional provider is tested as denied/absent; it is not
claimed to be a production-ready integration.

The final source allocation places full hybrid capture, dual
workstations, adaptive requests, reference promotion, bulk approval,
template breadth, physical-location workflow and production
safeguards in Gate 2. Building those features early does not replace
the five-book end-to-end proof or expand a ratified Gate 1 budget.

Gate 2 repeats Gate 1 invariants and all Gate 2 portions of AT-01
through AT-43, excluding explicitly Later portions and AT-37.
Run FX-50: all 50 physical books have completed evidence; 49/50 fails.
Measure active desktop effort per listing separately from capture
and service waiting. Report every observation/distribution against
120 seconds. Owner ratifies aggregation/outlier interpretation
before execution; no silently chosen passing average.

Inject worker termination after remote success but before local
acknowledgement, upload interruption, repeated approval and duplicate/
out-of-order events. Zero duplicate sellable copies is mandatory.
All enabled sales channels, direct-cart paths and feed outputs are
enumerated for AT-29 and AT-25.

Later tests retain future requirements and are not represented as
passed or counted as mandatory Gate 2 execution. Gate evidence
reports required, deferred, disabled, blocked, failed and passed
separately, with fixture/assertion counts.

Source recovery and test contracts are now reconciled against S6/S7.
Automation, fixture instantiation and software gate execution remain
future implementation work; no acceptance test has run.

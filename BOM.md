# Reliquary Ingest: bill of materials

**Review draft 0.2 | Baseline v1.0-RC | 19 October 2026**

Repository target: Dave-Meloncelli/Reliquary.capture.
Currency: AUD unless a future supplier quote states otherwise.
No purchase, new account, subscription or deployment is authorised.
No current vendor price has been looked up or asserted.
TBD means unknown, not zero. Existing resources are not assumed free.

## Fixed backend inventory

**1. Managed web application hosting**
Purpose: API, bench capture and review.
Dependencies: runtime/framework selection, authentication,
TLS, environment separation and supported deployment/rollback.
Setup cost: TBD. Monthly charge: TBD.
Sizing inputs: request volume, image upload path and operator count.
Gate: 1 minimal; production operations at Gate 2.

**2. One managed background worker process**
Purpose: image derivatives, optional local enrichment, database jobs
and Shopify synchronisation.
Dependencies: CPU/memory requirements, local OCR licences,
lease/retry design and provable least-privilege execution.
Setup cost: TBD. Monthly compute cost: TBD.
No elevated commercial/personal credentials in this process.
Gate: 1 minimal; recovery/operational hardening at Gate 2.

**3. One managed database**
Purpose: module-owned tables, jobs, reference/claim/run ledgers,
copy records, restricted commercial/personal schemas and audit.
Dependencies: roles/schema privileges, transactional queue locking,
automatic backup, restore/export and retention controls.
Setup cost: TBD. Monthly cost including backup retention: TBD.
Technology: TBD; must prove the agreed locking/permission semantics.
Gate: 1; backup rehearsal required at Gate 2.

**4. One object store**
Purpose: canonical location-free originals and derivatives.
Dependencies: write-once semantics with authorised privacy exceptions,
restricted access, audit, lifecycle and recoverable manifests.
Setup cost: TBD. Storage, request, egress and backup cost: TBD.
Gate: 1; retention/privacy recovery completion at Gate 2.

No fifth backend service, separate broker, vector database or
microservice has been budgeted. A new infrastructure component
requires documented justification and review.

## Capture and review toolchain

Hybrid iOS shell/native camera access:
framework TBD; shared web business logic required.
Licence cost: TBD. Apple development/distribution requirements and
account fees: TBD, depending on chosen delivery route.
No App Store distribution decision is implied.

Desktop browser review:
supported browser/device versions TBD; keyboard-efficient workflow
and co-located errors/actions required.
Incremental licence/hosting cost: TBD, included in web line where
applicable rather than counted twice.

Capture devices and accessories:
an existing CZUR Lens desktop document camera is confirmed by the
owner's original Q25A discussion. Reuse it; no new camera purchase
is required to begin. Direct video/SDK/driver compatibility, exact
model, licensing and image quality must be verified.
Desktop file import is the approved fallback. Both desktop and iOS
capture are first-class Gate 2 workflows sharing canonical identity;
a simpler Gate 1 input is permitted.
Tripod, lighting, labels/scanner and label-printer needs/costs: TBD.

Local persistence:
durable location-free image queue, recovery and upload status.
Implementation/library/licence cost TBD; this is client storage,
not a fifth backend deployment.

## Shopify and development

Shopify CLI:
required controlled development/diagnostic tool; not runtime.
Tool licence/acquisition cost: TBD pending official verification.
Associated developer effort and operational costs: TBD.

Shopify development store:
already exists according to the owner-approved Q31 source.
Use that isolated store; no additional store provisioning planned.
Account terms, limits and incremental costs: TBD, not inspected here.

Shopify production:
existing account/plan not inspected. Incremental plan/API/app,
theme, feed/channel or paid-extension costs: TBD.
Selected API/version, scopes, auth strategy and credentials: TBD.
Runtime must use supported APIs with rate-limit/retry handling.

Production app-writer assessment:
required before Gate 2 go-live, including book-metafield writers.
Effort, third-party app fees and conflict remediation costs: TBD.
No access inventory is performed before preserving this independent
design package.

App/theme configuration:
version control, validation, audit and rollback tooling required.
CI/runtime cost and repository plan implications: TBD.
Secrets must remain outside repository content.

## Enrichment, providers and rights

Internal catalogue/local OCR/image matching:
first tier. Libraries, model files, licences, hardware fit and
reference dataset rights: TBD.
Optional automation can be cut under Q32; manual provenance cannot.

External providers:
fallback only; provider selection and per-call/token/image charges TBD.
No assumed subscription. Provider register must document purpose,
allowlist, region, retention, no-training terms and contractual rights.
Disallowed providers are unavailable dependencies, not budget savings.

Bibliographic/media rights:
dataset reuse, retained evidence and public derivative rights need
assessment for selected sources. Licence fees: TBD.
No permission to reuse the owner's proprietary dataset is assumed.

Notifications and health:
critical alerts and daily health summary required for production.
Channel/provider, delivery cost and escalation policy: TBD.
Use the web/worker architecture; no additional backend component or
scheduled automation is created by this draft.

Privacy/compliance assessment:
legal applicability, retention exceptions and provider contracts.
Qualified-review cost and human hours: TBD.
Internal privacy rules apply regardless of statutory thresholds.

## Acceptance and operational dependencies

Five physical Gate 1 books and owner-approved truth manifest:
roster is defined in ACCEPTANCE_TEST_PLAN.md.
Incremental acquisition cost: TBD; books are described as from
the owner's shelf, not as a new purchasing requirement.

Fifty-book Gate 2 manifest, test automation, fault injection,
restore environment, channel/feed checks and developer time:
cost TBD; no paid test platform is presumed.

Backups, recovery and restriction replay:
included in database/object-store quotes where possible.
Restore compute, storage and egress costs remain TBD.

Domain, DNS and certificates:
whether existing resources suffice is TBD. Acquisition/renewal
costs TBD. Managed TLS availability is not assumed.

## Effort and spend model

PLAN.md proposes Gate 1: 16 agent sessions; Gate 2: 24 additional
sessions. Confidence low pending runtime/device and throughput validation.
The 24-session Gate 2 proposal supersedes the earlier unratified
20-session estimate by explicitly allowing four sessions for full
hybrid/dual capture. No budget increase or reset has been approved.
These are introduced estimates, not ratified spend authority.
Human work: task breakdown/hours/rates TBD if needed.
Agent subscription/usage charges: TBD; no assumed marginal cost.

Total one-off AUD:
setup + hardware + licences/accounts + approved human effort
+ fixture acquisition + compliance review. All components TBD.

Total monthly AUD:
web + worker + database/backups + object storage/requests/egress
+ notifications + selected external calls + incremental Shopify/CI
charges. All components TBD.

Storage estimate inputs:
copies per month × photographs per copy × canonical image MB,
plus derivative volume, retention, restore copies and growth.
Do not extrapolate an indefinite-retention bill from a single month.

External-call estimate inputs:
local-tier miss rate × permitted calls per copy × quoted unit price,
plus retry limits. Local-first operation should be measured,
not treated as a guaranteed discount.

## Dependency decisions before expenditure

Owner reviews options with AUD totals, tax/FX assumptions, contract
terms, cancellation/export path, licence restrictions and confidence.
Implementer demonstrates compatibility with four components, worker
isolation, draft-only owner release and known-good/known-bad tests.

Q1–Q33 and amendments have now been source-reconciled. Framework
choice, managed-provider choice, distribution route, timing acceptance
and recovery objectives remain explicit.
The final BOM total is TBD. This document does not present an
unverified low estimate as a funded operating plan.

## Recovered requirements affecting dependency choices

Tiered processing needs cost metering per item/batch/operation/provider,
deduplication, capped escalation and versioned replaceable adapters.
Library, local-model and provider licence/usage costs remain TBD.

Claims need provenance and dependent-source relationships; these
are logical data within the existing database, not a new graph
database or backend service.

Gate 2 needs portable manifests/exports and historical transaction
snapshots, nullable cost records and safe manual holds.
Their implementation effort is included in the revised plan;
commercial hosting/retention charges remain TBD.

Full demand/notification workflows, trade-ins/collection acquisition,
advanced intelligence, full historical migration, complete customer-
impact case management and detailed acquisition allocation are Later.
Do not charge their full implementation to the production MVP or
buy additional infrastructure for them without review.

Source recovery adds no new hardware purchase or infrastructure
component. Final scope follows the approved consolidated baseline.

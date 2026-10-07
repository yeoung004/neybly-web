# Roadmap, decisions, and current state

Updated: October 7, 2026

## 1. Implementation inventory

Verified against the repository before this documentation change:

| Area | State |
| --- | --- |
| README | Previously title-only; expanded by this documentation change |
| Ignore rules | Present; includes Next.js/Node-related patterns |
| Application code | Absent |
| Package manifest / lockfile | Absent |
| Backend / data model | Not implemented |
| Authentication / locality enforcement | Not implemented |
| Map / listing / reservation / chat | Not implemented |
| Review / QR / AI description | Not implemented |
| Tests / CI | Not present |
| Verified deployment | None established from this repository |

Re-inspect current files before using this historical snapshot to make a development claim.

## 2. Proposed delivery sequence

The founder's feature ideas are confirmed direction. The sequencing below is a recommendation, not an approved schedule or delivery promise.

### Foundation: resolve the operating contract

Define launch area, participation rules, location disclosure, reservation mode, and scope. Select the smallest suitable stack and record the reasons. Establish the entity model, access policy, and core acceptance scenarios.

Exit evidence: approved key decisions, a runnable skeleton with verified commands, and a clear definition of what the first pilot will test.

### V1: complete the neighborhood exchange loop

Candidate scope:
- Account and chosen locality policy.
- Sale creation and item inventory.
- Map and list discovery.
- Honest availability and item detail.
- Reservation creation, cancellation, deadline enforcement, and automatic release.
- Contextual buyer-seller communication.
- Pickup outcome and private exchange history.
- Basic report/block and operational moderation capability appropriate to the pilot.

Exit evidence: a seller can publish, an eligible buyer can discover and reserve, parties can coordinate, availability stays consistent, and an exchange can be recorded. Critical access and reservation-race tests pass. Real dependencies and operating costs are known.

Do not call a static frontend with sample listings a completed V1.

### V2: improve repeat use and accountability

Candidate scope:
- Two-sided reviews under an approved eligibility policy.
- Reputation presentation after there is credible input data.
- QR item pages and printable labels if needed.
- Better seller inventory management and reminders.
- Reporting and dispute workflow improvements based on pilot evidence.

Exit evidence: signals are explainable, abuse cases are handled, QR codes preserve access rules, and the additions measurably help actual coordination.

### V3: assist listing and richer discovery

Candidate scope:
- Optional AI photo-description drafts.
- Seller-authored photo hotspots.
- Improvements informed by validated neighborhood demand.
- Evaluation of local versus cloud inference against cost, quality, latency, and privacy requirements.

Exit evidence: inference has representative evaluations, manual fallback works, uncertain observations remain uncertain, and the product does not depend on free infrastructure continuing forever.

## 3. Open decision register

| ID | Decision | Why it matters | Recommended next step |
| --- | --- | --- | --- |
| D01 | Initial launch region and neighborhood definition | Determines useful density and eligibility | Choose a small pilot area |
| D02 | Browsing versus transaction locality requirements | Shapes onboarding and access checks | Define an action-by-role policy |
| D03 | Verification method and exceptions | Affects friction, privacy, and abuse | Compare methods before implementation |
| D04 | Exact address visibility | Balances event discovery and household privacy | Approve disclosure states |
| D05 | Instant reservations or seller approval | Changes the state machine | Select one V1 mode |
| D06 | Hold duration, pickup window, extension, grace | Determines expiry and conflict behavior | Specify examples and boundary cases |
| D07 | Payment and negotiation expectations | Prevents accidental checkout or bargaining scope | Confirm offline-payment scope and price options |
| D08 | Single-item sales without an event | Changes the core domain model | Validate the use case |
| D09 | Completion and review eligibility | Determines trustworthy history | Define evidence and disputes |
| D10 | Reputation formula and appeals | Can materially affect participation | Defer scoring until policy and data exist |
| D11 | Framework, storage, auth, map, hosting | Affects cost and maintenance | Record architecture decisions |
| D12 | Moderation, prohibited listings, retention | Needed for real-user operations | Prepare operating policies before launch |
| D13 | AI provider, consent, retention, budget | Affects cost and data exposure | Evaluate only for the optional AI phase |
| D14 | Monetization | Can distort early priorities | Validate usefulness before selecting a model |
| D15 | Brand pronunciation and visual system | Makes identity consistent | Confirm after initial brand exploration |
| D16 | US/Canada launch order and cross-border rules | Affects currency, locality, and operations | Separate target market from launch scope |

These entries are unresolved. Recommendations are not approvals.

## 4. Confirmed product decision ledger

| ID | Decision | Basis |
| --- | --- | --- |
| C01 | Use the name Neybly | Founder selected the name |
| C02 | English is the default product/repository language | Founder explicitly requested it |
| C03 | Focus on neighborhood participants | Founder emphasized nearby buyers and trust through locality |
| C04 | Target the United States and Canada | Founder-provided market direction |
| C05 | Discover sales by map and show items by location | Founder-provided core features |
| C06 | Include reservation expiry/release and chat | Founder-provided coordination features |
| C07 | Explore two-sided history, reviews, and reputation | Founder-provided trust direction |
| C08 | Include QR item information and optional photo assistance in the vision | Founder-provided future capabilities |

Source basis: founder context supplied for this documentation task. No prior code implementation or completed release is implied.

## 5. Architecture guidance

No framework or provider is approved by these documents. React/TypeScript familiarity may inform a proposal, but familiarity alone is not a repository decision.

Prefer one coherent deployable system for an early pilot unless a concrete requirement justifies separation. Enforce authorization at the data boundary, transactional inventory rules at the authoritative service, and explicit public/private response projections.

Evaluate map cost, geocoding limits, storage, authentication, notification delivery, and background expiry handling before choosing services. Do not claim a provider's current pricing without verification.

## 6. Definition of done

A feature is done when its user outcome works, relevant permissions and invalid states are verified, recovery paths are understandable, and documentation describes the observed behavior. Distinguish a mocked integration from a working real integration.

A documentation task is done when files are readable, internal links resolve, confirmed and proposed content are distinguishable, terminology is consistent, and changes are persisted in the intended repository.

## 7. Recording future decisions

Use: decision ID, date, status, context, selected option, alternatives considered, consequences, affected files, and evidence of founder approval where needed.

Allowed statuses: proposed, accepted, superseded, rejected. Link a replacement when superseding. Update the canonical specification alongside the record to avoid conflicting sources.

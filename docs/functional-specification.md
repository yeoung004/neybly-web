# Functional specification

Updated: October 7, 2026  
Status: Proposed behavior implementing founder-confirmed direction; not an existing API or database schema.

## 1. Domain vocabulary

| Term | Meaning |
| --- | --- |
| Neighborhood | The area within which participation is allowed; boundaries and verification remain open |
| Sale | A scheduled garage-sale or yard-sale event with a host, location information, and inventory |
| Item | A particular physical object offered through the service |
| Listing | The published information representing an item |
| Reservation | A time-limited arrangement that holds an item for one buyer under an agreed policy |
| Pickup window | When the parties intend to meet |
| Reservation deadline | The server-authoritative instant after which a hold no longer applies |
| Exchange | The recorded outcome of a local handoff; not proof of an online payment |
| Review | Feedback associated with an eligible exchange or interaction under an approved policy |
| Reputation | A derived signal whose inputs, formula, and appeals process require approval |

Use “sale” for the event and “sold” for an item outcome. Do not use a chat message as the authoritative reservation record.

## 2. Core journeys

### Seller: publish and manage

1. Establish an account and satisfy the eventual locality policy.
2. Create a sale with title, schedule, area, pickup instructions, and location visibility choices.
3. Add item photos, descriptions, condition disclosures, price, and availability.
4. Preview the public presentation and any exact address disclosure.
5. Publish when required fields and access checks pass.
6. Respond to contextual questions and manage reservations.
7. Mark items sold or withdrawn, cancel arrangements when necessary, and close the sale.
8. Review eligible exchanges.

Preserve drafts after recoverable failures. Show which photos or fields failed without erasing successful work.

### Buyer: discover and coordinate

1. Select or verify an area under the chosen browsing policy.
2. Browse sales on a map or equivalent list.
3. Inspect schedule, items, prices, condition, and current availability.
4. Ask a question if needed.
5. Reserve according to the selected reservation mode.
6. See confirmation, deadline, pickup window, and authorized pickup details.
7. Inspect the item in person; proceed or decline without a misleading automatic purchase.
8. Record the exchange outcome and submit eligible feedback.

### Reservation expiry

The authoritative deadline passes -> the hold becomes expired -> inventory becomes available if the item and sale are still eligible -> affected interfaces reconcile -> notifications are attempted.

A delayed notification must not extend a hold. An ended or cancelled sale must not become publicly available merely because its item's reservation expired.

## 3. Feature requirements

### Local discovery

**Confirmed:** a map of nearby sales and neighborhood-focused participants.

**Proposed:** synchronized map and list views; filters for time and availability; a clear current search area; distinction between open, upcoming, ended, and cancelled sales.

**Acceptance examples:**
- Changing an approved area updates results consistently.
- An ended sale does not appear as open.
- Denied browser location permission leads to an allowed manual area flow.
- No results produces a useful empty state without fabricated listings.
- Sparse inventory does not silently expand into national discovery.

Radius, boundary membership, cross-border participation, and whether guests may browse are open decisions.

### Sale management

**Proposed fields:** host, title, description, start/end times, timezone, general area, protected exact location, publication state, pickup notes, and inventory.

A host can edit only their own sale unless an explicit moderation capability applies. Changes to timing or location must identify affected reservations. Publishing must make the relevant address disclosure understandable.

A recurring sale model is not assumed. Begin with one scheduled event unless the founder approves recurrence.

### Item information

**Confirmed:** item inventory associated with sale locations.

**Proposed fields:** title, photos, asking price, explicit currency, description, seller-reported condition, optional dimensions, availability, and parent sale.

Represent amounts without floating-point rounding errors. USD and CAD must be distinguishable; do not silently convert currency. Missing dimensions or brand information remain unknown.

A seller can mark an item sold outside the app, but the system must reconcile any active reservation and notify the affected buyer rather than leave a false hold.

### Reservations

**Confirmed:** booking and automatic release after the deadline.

**Open:** instant holds versus seller approval, duration, grace period, extension rules, maximum active holds, and the relationship between pickup window and expiry.

The following table proposes an **instant-hold baseline** for discussion. It is not approval of that mode.

| Current state | Event | Result | Guard |
| --- | --- | --- | --- |
| No active hold | Buyer reserves | Active reservation | Eligible buyer, available item, valid sale, valid deadline |
| Active | Buyer cancels | Cancelled; release item | Reservation participant authorized |
| Active | Seller cancels | Cancelled; release or withdraw item | Owner authorized; reason recorded |
| Active | Deadline passes | Expired; release if still eligible | Server time is at or after deadline |
| Active | Valid handoff recorded | Completed; item sold | Authorized outcome and active hold |
| Active | Item becomes unavailable | Cancelled; item unavailable | Owner action or approved moderation action |
| Terminal state | Duplicate same operation | Stable result | Idempotent handling |

If seller approval is chosen, introduce a separately defined request state with request expiry and rules about whether requests hold inventory. Never let a pending request accidentally act like a confirmed hold.

**Required invariants for any implementation:**
- At most one active reservation per single-quantity item.
- Creation, expiry, cancellation, and sale completion are authoritative backend operations.
- Concurrent attempts cannot both acquire the item.
- Retried requests do not create duplicate holds or duplicate completion records.
- At the exact deadline, an expired hold cannot be completed as if still active.
- Cancellation and expiry release only their own reservation, never a newer hold.
- A stale client countdown does not authorize a transaction.
- Extensions, if approved, are visible to both parties and atomically validated.
- Reservations cannot outlive the allowed sale/pickup policy.
- Self-reservation is rejected unless a specific legitimate use case is approved.
- No automatic financial penalty or negative review follows expiry without an approved policy.

Test interleavings between reserve, cancel, expire, and mark-sold. A background job alone is insufficient: mutations must re-check whether a hold is still valid.

### Chat

**Confirmed:** buyer-seller communication.

**Proposed:** threads refer to a sale or item and expose the relevant reservation summary. Only authorized participants and narrowly authorized support roles can read messages. Messages are content, not executable instructions.

Support failed-send recovery, duplicate-send protection, report/block actions, and clear availability context. A promise in chat must not silently modify reservation state. Define how blocking affects active arrangements before implementation.

### Exchange history and reviews

**Confirmed:** buyer and seller history, feedback in both directions, a manners/reputation concept.

**Proposed:** distinguish private detailed history from public aggregate signals. Restrict reviews to eligible recorded interactions. Prevent self-reviews and duplicate reviews for the same side of one exchange.

Open decisions include eligibility, publication timing, edit windows, dispute handling, score weighting, aging, and how little-history accounts appear. “No reviews yet” must not be treated as proof of unreliability. Do not invent a temperature formula.

### Item QR codes

**Confirmed:** an item QR code opens item information.

**Proposed:** use a canonical item URL with a non-sensitive identifier. Re-check authorization when the page loads. Scanning never reserves or purchases automatically.

A sold, withdrawn, or deleted item's QR code should yield an informative state. QR payloads must not embed private addresses, access tokens, or internal credentials.

### Optional photo-assisted descriptions

**Confirmed:** interest in generating descriptions and visible-condition observations.

**Proposed:** seller opts in -> photos are processed under a disclosed provider policy -> a draft appears -> seller edits and confirms -> publication follows the normal listing flow.

AI must not infer working condition, authenticity, exact dimensions, ownership, cleanliness, or hidden defects from an image alone. Describe observable appearance cautiously. Preserve manual entry when inference fails, times out, or exceeds the allowed cost.

Provider, model, data retention, local-device support, output schema, and budget are unresolved. “Free” infrastructure is not a durable assumption.

### Photo hotspots

**Confirmed inspiration:** tappable item markers on a shared photo.

**Proposed later feature:** seller-controlled markers link to real item records; keyboard and list alternatives expose the same information. Do not automatically identify or publish objects from a household photo without confirmation.

## 4. Conceptual entities

These names explain relationships; they do not prescribe tables or a framework.

| Entity | Responsibilities and relationships |
| --- | --- |
| User | Identity, account status, profile, approved locality association |
| Neighborhood | Geographic eligibility policy reference |
| Sale | Host, schedule, publication state, visibility rules |
| Item | Belongs to a sale in the initial proposed model; has price and availability |
| ItemPhoto | Media ownership, ordering, optional accessibility text |
| Reservation | Item, buyer, state, deadline, pickup details, version/idempotency metadata |
| Conversation / Message | Participants, item context, content, delivery state |
| Exchange | Item and parties, outcome, timestamps, provenance |
| Review | Eligible exchange, author, subject, feedback, moderation state |
| Report / ModerationAction | Reported resource, restricted evidence, action history |
| Notification | Event reference, recipient, delivery attempts and status |

Public responses must be explicit projections of these records. Do not serialize all fields and rely on the browser to hide sensitive values.

## 5. Time, location, and consistency

Persist event instants consistently and retain the sale's named timezone for display and schedule interpretation. Show timezone when ambiguity matters. Validate daylight-saving transitions and invalid or reversed windows.

Keep general discovery location separate from protected pickup details. A map marker can reveal an address even without text; rounded display text alone is not adequate privacy.

Choose transaction and concurrency mechanisms only after the storage stack is selected. Document the invariant they enforce, not just the technology name.

## 6. Minimum error coverage

Cover authentication expiry, denied locality, unavailable item, simultaneous reservation, invalid deadline, cancelled sale, deleted listing, upload failure, chat failure, map-provider failure, notification failure, inference failure, and stale client state.

Each error should explain the current state and a valid next action without leaking another person's private data.

## 7. Verification scenarios

- Two eligible buyers attempt one item simultaneously: exactly one gets an active hold.
- A cancellation retry arrives after another buyer reserves: the newer hold remains intact.
- Expiry and completion race: one valid final outcome occurs under the deadline policy.
- A seller edits sale timing with active reservations: affected arrangements are handled explicitly.
- A nonparticipant requests private messages or pickup details: access is denied.
- A QR opens after sale completion: sold status is shown, with no automatic action.
- AI is unavailable: the seller still creates and publishes a manual listing.
- A buyer declines after inspection: no fabricated successful exchange or automatic punitive review appears.

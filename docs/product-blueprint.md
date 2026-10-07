# Product blueprint

Updated: October 7, 2026  
Status: Founder direction plus explicitly marked product proposals.

## 1. Purpose

Neybly exists to make neighborhood yard sales easier to find, understand, and coordinate. A successful interaction is a useful nearby exchange with clear expectations and limited wasted effort.

The product should preserve what makes a yard sale appealing: proximity, browsing real objects, direct inspection, casual local interaction, and giving usable belongings another life. Digital coordination should reduce friction around that experience.

## 2. Intended audience and jobs

| Person | Situation | Job to be done | Desired outcome |
| --- | --- | --- | --- |
| Household seller | Clearing several belongings during a scheduled sale | Publish the sale and its items with minimal repetition | Interested neighbors arrive with realistic expectations |
| Occasional seller | Has one or a few items to offer | Make a local pickup easy to coordinate | Less messaging and less uncertain waiting |
| Nearby buyer | Has limited time to visit sales | Understand location, timing, inventory, and availability | A worthwhile local trip |
| Browsing neighbor | Wants to explore the area | Find sales happening nearby | Convenient discovery without a shipping catalog |

Single-item selling is a plausible extension of the core experience; whether it requires a sale event is unresolved. Do not weaken the sale-centered model without recording that decision.

## 3. Seller pain points

### Uncertain attendance

A vague message is not a pickup arrangement. Show the item, agreed window, reservation deadline, and current state together. Avoid implying that every interested buyer is committed.

### Repeated questions

The sale and item pages should answer common questions about price, condition, dimensions, timing, availability, and pickup expectations. Chat handles the exceptions; it should not be required to discover basic facts.

### Negotiation overhead

Make asking price and any approved negotiation policy legible. Do not require bargaining or automatically encourage lower offers. A future firm-price option is a proposal, not an implemented policy.

### Manual availability tracking

A seller may sell an item in person while others are browsing online. Make marking items sold straightforward, reconcile active reservations, and communicate changes honestly.

## 4. Buyer pain points

### Fragmented discovery

A buyer needs a sale location, a time window, and enough item information to judge relevance. A map without time and inventory context is incomplete.

### Wasted travel

An item may already be sold, a sale may be closed, or the actual condition may differ from the photograph. Improve availability signals and disclosure. Do not claim to eliminate all wasted trips.

### Shipping and inspection

The intended experience is local pickup and in-person inspection. Do not insert shipping estimates, delivery options, escrow, or checkout as assumed requirements.

### Unclear commitment

Distinguish asking a question, requesting a reservation, holding an item, arriving, and completing an exchange. Buyers must understand the deadline and what happens when it passes.

## 5. Product goals

| ID | Goal | Design consequence | Candidate evidence |
| --- | --- | --- | --- |
| G1 | Make nearby opportunities understandable | Map and list expose sale timing and inventory | Buyers locate a relevant open or upcoming sale |
| G2 | Reduce seller coordination effort | Structured details and visible arrangements | Fewer repetitive messages per completed exchange |
| G3 | Reduce uncertainty before travel | Current item status, truthful photos, reservation details | Fewer reported unavailable-item trips |
| G4 | Make commitments understandable | Deadlines and cancellation states are explicit | Higher reservation-to-pickup completion |
| G5 | Build earned local trust | Relevant history and two-sided feedback | Repeat local exchanges and resolved reports |
| G6 | Keep participation accessible | Mobile-friendly flows and manual alternatives | Completion despite location denial or AI failure |
| G7 | Keep operation sustainable | Simple architecture and measured provider usage | Acceptable operating cost per completed exchange |

Metrics are proposed evaluation tools. There are no real baselines, targets, or results yet.

## 6. Positioning and identity

Neybly is a neighborhood service centered on physical local exchanges and sale discovery. Its strongest differentiator should be the relationship between nearby sales, visible inventory, and clear coordination.

The name is confirmed. A pronunciation aid such as “NAY-blee” is a branding proposal to validate, not an established pronunciation policy. A short introductory explanation may be useful; repeated pronunciation instructions should not distract from finding sales.

Friendly does not mean childish. Trustworthy does not mean making safety guarantees. Local does not mean publishing someone's private address everywhere.

## 7. Explicit anti-goals

| Avoid | Why it harms the intended experience | Preferred direction |
| --- | --- | --- |
| Nationwide shipping marketplace | Removes the neighborhood and inspection focus | Nearby pickup |
| Auctions and bidding wars | Adds pressure and seller negotiation work | Clear price and pickup expectations |
| Generic social feed | Competes with completing useful exchanges | Sale and item discovery |
| Endless engagement loops | Rewards time spent rather than a useful outcome | Efficient discovery and coordination |
| Payment infrastructure by default | Adds obligations and complexity before validating demand | Treat payment integration as a separate decision |
| Mandatory AI generation | Makes a simple listing depend on inference | Fully usable manual creation |
| Automatic AI condition certification | Photos cannot prove function, authenticity, or hidden damage | Editable suggestions with uncertainty |
| Fake reviews or trust badges | Misleads people about real evidence | Honest empty states and verified signals |
| Unexplained reputation penalties | Can unfairly punish legitimate behavior | Transparent, contestable policies |
| Hidden address exposure | Turns local discovery into unnecessary personal disclosure | Purpose-specific location visibility |
| Forced account creation for every screen | Can add friction before users see value | Decide access by action and privacy needs |
| Copying another product's visual identity | Confuses the brand and creates unnecessary dependence | Original design informed by useful patterns |
| Premature microservices | Increases operational burden without proven need | A small coherent system |
| Feature parity as a goal | Inflates scope without validating local demand | Problem-driven prioritization |

## 8. Prioritization rule

A feature should name the user's problem, explain its place in the discovery-to-pickup journey, identify the smallest complete solution, and define observable acceptance criteria.

Prefer work that improves reliability of an existing core flow before adding a new surface. A QR code that opens stale availability is less useful than a reliable item page. A reputation score without trustworthy exchange records is not a shortcut to trust.

## 9. Success and measurement proposal

The leading candidate outcome is **completed local exchanges per active neighborhood per week**, interpreted alongside coordination effort and reported problems. The definition of “completed” must be settled before instrumentation.

Supporting measures may include sale publishing completion, discovery-to-detail visits, reservation conversion, pickup completion, cancellations, expirations, repeat participation, reports, and seller-reported effort.

Do not optimize completion counts by pressuring people to buy after inspection. Do not collect precise location history merely to measure engagement. Establish a baseline in a small launch area before setting numeric growth targets.

## 10. Decision filter

Before adding a feature, ask:

1. Does it help a nearby seller or buyer accomplish a real exchange?
2. Does it make information or expectations clearer?
3. Does it reduce effort without hiding important choices?
4. Can it work with truthful, limited data?
5. Can the team operate and support it?
6. Does it preserve the neighborhood focus?
7. Is the benefit large enough to justify the added complexity?

An unresolved answer is a reason to narrow or investigate the feature, not to invent product certainty.

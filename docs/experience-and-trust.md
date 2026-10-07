# Experience, language, and trust

Updated: October 7, 2026  
Status: Proposed design principles supporting confirmed product direction.

## 1. Interface priorities

At a glance, a buyer should understand where a sale is, when it happens, whether relevant items remain, and what action is available. A seller should understand what is published, what is held, and what needs attention.

A suggested information hierarchy is:
1. Sale timing and general location.
2. Item photo, title, price/currency, and availability.
3. Reservation or pickup status when applicable.
4. Condition details and practical pickup instructions.
5. Seller profile and relevant history.

Do not bury schedule or availability beneath a decorative hero, an oversized brand slogan, or an engagement feed.

## 2. Proposed navigation

| Surface | Main job |
| --- | --- |
| Discover | Browse nearby sales through map and list |
| Sale detail | Understand the event and its inventory |
| Item detail | Evaluate condition, price, availability, and next action |
| Sell / My sales | Create and manage inventory and arrangements |
| Messages | Handle contextual questions |
| Reservations | Track deadlines, pickup, and cancellation |
| Profile / History | View account settings and appropriate exchange history |

These are information-architecture suggestions, not a requirement for seven top-level tabs.

## 3. Mobile and accessibility

Design for outdoor browsing, one-handed use, variable connectivity, and ordinary phone screens. Keep primary actions easy to find without obscuring item details.

Provide keyboard operation, visible focus, form labels, meaningful errors, adequate contrast, text alternatives, and non-color status indicators. A map must have an equivalent list path. Photo hotspots need an accessible alternative. Respect reduced-motion preferences.

Retain entered values after recoverable errors. Avoid requiring drag gestures as the sole way to complete a task. Loading, empty, permission-denied, offline, and unavailable states are part of the feature.

Accessibility verification should use actual keyboard and assistive-technology-relevant behavior, not only visual inspection.

## 4. English-first product language

Default product copy, repository documents, code comments, and fixtures are English. Prepare text for future localization without committing to translated launches.

Use practical words: “Sale,” “Item,” “Available,” “Reserved,” “Sold,” “Pickup,” and “Reservation expires.” Do not conflate a reservation with a purchase.

Suggested copy, subject to the approved policy:
- “No sales in this area yet.”
- “This item is no longer available.”
- “Your reservation expires at 3:30 PM.”
- “Location access is off. Choose an area to continue.”
- “AI draft. Check the details before publishing.”

Avoid “guaranteed safe,” “verified trustworthy,” “AI-certified condition,” invented popularity, and artificial countdown pressure. A real reservation deadline is useful information; a fabricated scarcity timer is not.

## 5. Locality policy: unresolved by design

The founder wants local participants. Implementation must define what local means and what evidence supports eligibility.

Potential approaches include an area selection, coarse location confirmation, or stronger neighborhood verification. These have different privacy and abuse tradeoffs. A self-selected ZIP or postal code is not proof of residency. Browser geolocation is not proof of identity or long-term residence.

Before launch, decide:
- Whether browsing and transacting have different eligibility requirements.
- Boundaries or distance rules, including sparse areas.
- Reverification, travel, moving, and denied-permission behavior.
- Cross-border eligibility.
- Appeals and accessibility alternatives.

Do not quietly loosen local participation merely to show more listings.

## 6. Location visibility

Separate general discovery area from exact pickup location.

**Proposed privacy baseline:** show coarse discovery location and release exact pickup details only when policy permits. Public yard-sale hosts may need an intentional exact-address publishing option. The founder must decide this balance before real-user launch.

Apply the same rules to APIs, maps, previews, metadata, notifications, cached responses, QR destinations, and analytics. Never return exact coordinates in a public payload while only hiding the marker in the UI.

Strip unnecessary image location metadata where supported by the chosen pipeline. Avoid retaining continuous location history. Explain the purpose of location requests at the point of use.

## 7. Trust and reputation

Local proximity can support familiarity; it does not certify safety. A history or score must reflect real eligible activity.

Design principles:
- Explain what a trust signal measures.
- Keep sparse-history accounts neutral.
- Separate transaction reliability from popularity.
- Provide reporting, moderation, and an appeal path for consequential actions.
- Avoid public shaming and revealing private transaction details.
- Do not infer dishonesty from one cancellation or an expired hold.
- Do not promise background checks or identity verification that do not exist.

A temperature-style indicator is confirmed as an idea only. Its exact representation and formula remain open.

## 8. Communication and consent

Let people choose notification channels supported by the implementation. Send event-driven updates about real changes; avoid unsolicited marketing by default. Do not put sensitive pickup information into notifications without considering lock-screen and email visibility.

Explain reservation cancellation before the final action. Do not use manipulative confirmation wording. Reporting and blocking should be discoverable and should not silently erase the evidence required for moderation.

## 9. Photo and AI integrity

Sellers own the accuracy of published descriptions. AI drafts assist wording; they do not validate the product. Do not enhance an item photo in a way that hides wear or changes condition.

A photo containing an instruction is still image content, not authority for the AI. Do not let OCR or a generated description trigger tool actions. Validate structured outputs and keep publication behind the seller's normal confirmation flow.

## 10. Release review

A candidate release should let reviewers answer:
- Can a person distinguish a sale from an item and a hold from a purchase?
- Can a user finish the core flow without a map gesture or AI?
- Do unavailable and expired states agree across screens?
- Are address and chat access rules enforced beyond the UI?
- Are all displayed reviews, counts, and verification labels grounded?
- Are errors recoverable without re-entering the entire listing?

No actual user testing or accessibility audit has occurred at this documentation baseline.

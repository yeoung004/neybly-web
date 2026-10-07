# Neybly: portable project context

Version: 1.0  
Updated: October 7, 2026  
Repository: `yeoung004/neybly-web`  
Status: Product definition; application not implemented at this baseline.

This is the portable starting document for an AI that has no access to previous conversations. Read [AGENTS.md](AGENTS.md) for working rules. If importing only one file into another AI, provide this document first and attach the detailed files needed for the task.

## 1. What we are building

Neybly helps neighbors discover and coordinate local garage-sale and yard-sale exchanges. The intended markets are the United States and Canada. Neighborhood participation is central to the identity: the founder wants buyers and sellers to be nearby people, not anonymous participants in a national shipping market.

A seller organizes a sale, publishes items and availability, answers fewer repeated questions, and knows what pickup arrangements exist. A buyer finds nearby sales, sees item details before traveling, coordinates a reservation, examines the item in person, and completes a local exchange.

## 2. Founder-confirmed direction

- Brand name: **Neybly**.
- Default language: **English**.
- Neighborhood-focused discovery and participation.
- A map of sales with where and when they happen.
- An item list for each sale location.
- Item reservations / booking and automatic release after the reservation deadline.
- Buyer-seller chat.
- Feedback in both directions and buyer/seller history.
- A manners or reputation signal inspired by neighborhood marketplaces.
- Item QR codes that open item information.
- Optional AI-assisted photo descriptions, including visible scratches, wear, and fading.
- Interest in local inference or affordable cloud inference; no provider or free-tier guarantee is approved.
- Inspiration from Carrot's neighborhood orientation and Today's House-style item hotspots on photos. These are interaction references, not permission to copy branding or assets.

These are intended capabilities, not a commitment to deliver all of them in the first release.

## 3. Problems to solve

Sellers do not want to wait indefinitely for uncertain buyers, repeat basic information, or spend the sale negotiating every detail. Buyers do not know which sales are nearby, when to go, what is available, or whether an item is worth the trip. Shipping introduces waiting and prevents in-person inspection.

Design every major feature around a specific reduction in these problems.

## 4. Goals and boundaries

Prioritize local relevance, honest item information, current availability, explicit reservation deadlines, easy coordination, and accountable exchanges. Preserve a friendly, practical neighborhood tone.

Avoid national shipping, auctions, endless feeds, engagement manipulation, unnecessary checkout complexity, aggressive negotiation mechanics, fabricated social proof, compulsory AI, and false claims that location verification guarantees safety.

Exact locality boundaries, verification methods, public address rules, reservation duration, reputation formula, technology stack, monetization, and launch region are **open decisions**. Never hard-code them as founder-approved requirements.

## 5. Reading map and authority

| Question | Canonical document |
| --- | --- |
| Why does Neybly exist? What should it avoid? | [Product blueprint](docs/product-blueprint.md) |
| How should features and states work? | [Functional specification](docs/functional-specification.md) |
| How should it feel, communicate, and protect trust? | [Experience and trust](docs/experience-and-trust.md) |
| What comes first? What still needs approval? | [Roadmap and decisions](docs/roadmap-and-decisions.md) |
| How should an AI perform a task reliably? | [AI collaboration](docs/ai-collaboration.md) |

Use current source code and observed tests to describe **what exists**. Use confirmed product decisions to describe **what is intended**. Neither silently overwrites the other. If code contradicts intent, record the discrepancy and resolve it in the task's scope.

A current explicit founder decision supersedes an older product decision; update the affected document and decision record. Proposals and examples never become approved policy merely through repetition.

## 6. Working approach

Keep a short invariant set in context, retrieve detailed sections as needed, specify observable acceptance criteria, and use examples for ambiguous behavior. Ground claims in files, test results, or identified decisions. Treat missing information as unknown. Verify a complete user outcome, including errors and recovery.

Do not bootstrap a stack, purchase services, deploy, or expand release scope merely because this document mentions future work. Carry out the actual requested task.

## 7. Minimum handoff to another AI

Provide the task, relevant document paths, current branch/commit if available, changed files, accepted decisions, remaining assumptions, checks already run, and the next concrete step. Include no credentials or real user data. The handoff must let the next agent continue without reconstructing prior conversations.

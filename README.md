# Neybly

**Neighborhood yard sales, easier to discover and easier to coordinate.**

Neybly is a neighborhood-focused service for the United States and Canada. It connects nearby people around garage sales and yard sales: discover sales on a map, inspect item information before visiting, arrange a reservation and pickup, and build a history of reliable local exchanges.

The central promise is **local participation and clearer expectations**. Proximity is not a guarantee of safety, and a reservation is not a completed purchase.

## Project status

As of October 7, 2026, this repository is in the **product-definition stage**. Before this documentation update, it contained only a title-only README and a Next.js-oriented `.gitignore`. There is no application, dependency manifest, backend, test suite, or verified deployment in this repository. Ignore-file entries do not establish an approved technology stack.

All features described below are planned unless future implementation evidence says otherwise.

## Start here

| Reader / task | Read |
| --- | --- |
| Any coding or product AI | [AGENTS.md](AGENTS.md), then [instruction.md](instruction.md) |
| Product strategy and positioning | [Product blueprint](docs/product-blueprint.md) |
| Features, workflows, entities, and edge cases | [Functional specification](docs/functional-specification.md) |
| Interface, language, location privacy, and trust | [Experience and trust](docs/experience-and-trust.md) |
| Release scope, decisions, and delivery gates | [Roadmap and decisions](docs/roadmap-and-decisions.md) |
| Reusable AI task prompts and evaluation | [AI collaboration playbook](docs/ai-collaboration.md) |

## Product direction

- Help neighbors find **where a sale is, when it is happening, and what is available**.
- Reduce sellers' uncertain waiting, repetitive questions, and negotiation overhead.
- Let buyers inspect items locally without shipping delays.
- Make availability, reservations, pickup expectations, and cancellation understandable.
- Support accountability through completed exchange history and two-sided feedback.
- Keep English as the default language for the product and repository.

Do not expand this into a nationwide shipping marketplace, auction platform, or generic social feed.

## Development

There are no install, development, build, or test commands yet. Do not invent them. After a stack is approved and implemented, replace this section with commands verified against the actual dependency manifest and environment.

## Documentation conventions

**Confirmed direction** means the founder expressed the intent; it does not mean a feature exists. **Proposed** means a recommended design awaiting approval. **Open** means a decision is unresolved. **Implemented** requires code and verification evidence.

The detailed files are the canonical product context. Keep this README short and update the relevant source document when behavior changes.

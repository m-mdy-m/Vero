# ADR 

**Date:** 2025-10-04
**Status:** Accepted

## Summary

To ensure consistent logic behavior across all clients (core CLI, SDKs, and future clients such as web/mobile), we have accepted keeping the business logic in a separate, protocol-agnostic layer on the server side. The core will be authored in **TypeScript** and will rely on **pure SQL** for persistent storage access. The core is intended to expose well-defined, language-level contracts and lightweight adapters while avoiding heavy framework or platform lock-in. This ADR records the intent, scope, expected trade-offs, and general guidelines for implementing that core in a technology-neutral manner.

## Context

* The product is a multi-client system (CLI clients, SDKs, potential web/mobile clients). Consistent behaviour across clients is a priority.
* Business rules include domain-sensitive calculations, auditability, moderation policies, reputation scoring and other logic that must remain consistent and reviewable.
* Team has chosen TypeScript as the primary implementation language for the business logic layer.
* The project emphasizes minimal external dependencies, explicit SQL (no heavy ORM), testability, and long-term maintainability.
* The architecture should allow multiple transport adapters (e.g., CLI transport, HTTP, RPC, peer sync) to coexist without embedding domain rules in transports or clients.
* Product goal: A consistent and authentic experience for users across all clients (current CLI, Go/JS SDKs, future web/mobile clients).

### Complex logic requirements:

* Reputation score calculation based on posts, comments, reasons for giving/depriving credit, and interactions — including complex and extensible rules.
* Badge issuance and reputation changes in a calculated, auditable, and traceable manner.
* Moderation flows (rules, reasons, temporary/permanent penalties).
* Sync / offline support: Users may post offline and sync later.
• Scalability and performance demands: Growth patterns (hypothetical example: 200k users with high concurrent publish loads) and need for fast response times for reading/viewing posts and reputation calculations.
## Decision

1. **Single Logical Core:** All domain and business rules are implemented in a single logical core (the “Business Core”) rather than distributed across client implementations.
2. **Implementation Language:** The Business Core will be implemented in **TypeScript**. TypeScript is the canonical language for all domain code in this core.
3. **Persistence Approach:** Data access will use **pure SQL** (hand-written, explicit queries) as the primary persistence mechanism. Use of micro-ORMs, heavy data-mapping frameworks, or auto-generated SQL layers is discouraged unless justified.
4. **Minimal Runtime Dependencies:** The core should avoid heavy framework dependencies; only small, explicit, well-maintained libraries are acceptable. Utility libraries should be evaluated for long-term maintenance and footprint.
5. **Protocol-Agnostic Interface:** The core will expose a stable, well-documented API surface (language contracts and data contracts). Transport adapters (HTTP, CLI, SDK wrappers, peer sync) are thin adapters that translate transport concerns to core API calls; they must not contain business rules.
6. **Event-Ready Design:** The core should be designed to publish and consume domain events (semantic, versioned), but the ADR does not lock the project to any particular message broker or queue technology.
7. **Observability & Audit:** The core must provide hooks for observability (metrics, tracing) and maintain audit trails for sensitive domain actions.
8. **Testing & Validation:** Business rules must be fully covered by unit and integration tests; tests must validate logic independent of transport adapters.


---

## Alternatives Considered

1. **Distribute logic to clients (client-heavy):** Lowers server complexity but leads to divergence, security risks, and inconsistent behaviour. Rejected.
2. **Monolithic server with mixed domain/transport code:** Simpler initially but couples transport and domain, making multi-client support and protocol changes more difficult. Rejected.
3. **Adopt a heavy ORM / low-code persistence layer:** Faster to implement but hides SQL semantics, increases risk of inefficient queries, and complicates complex domain queries. Rejected in favor of pure SQL.
4. **Choose a different canonical language (e.g., Go):** Valid option, but the team has chosen TypeScript for domain code consistency; language choice may be revisited by separate ADR if needed.

---

## Related ADRs

• ADR: API versioning strategy (future).
• ADR: Event schema versioning & migration (future).
• ADR: Offline sync conflict resolution strategy (future).

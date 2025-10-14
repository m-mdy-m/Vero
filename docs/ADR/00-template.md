# ADR-<NNN>: <Short, descriptive title>

**Status:** Proposed ⬢ Accepted ⬡ Superseded ⚠ Deprecated  
**Date:** YYYY-MM-DD 
**Authors:** Name <email>, Name <email>
**Reviewers:** Name <email> (optional)
**Tags:** [category], [component], [risk-level]
**Related SRS IDs / Requirement IDs:** REQ-XXXX (optional)
**Impact Area:** (e.g., Backend, API, Infra, Security, Mobile, Embedded)

---

## Summary
One-paragraph summary of the decision and the recommended choice. Keep it short and explicit: *what* is being decided and *what* is being recommended.

## Context and Problem Statement
Explain the background and the concrete problem(s) this ADR is addressing. Include:
- Why this decision is needed now (triggers, pain points, constraints).
- Relevant constraints (budget, timelines, regulatory, legacy systems).
- Stakeholders affected.
- Any assumptions made.

## Goals and Non-Goals
**Goals:** short list of what this decision aims to achieve (measurable when possible).  
**Non-Goals:** what is explicitly out of scope for this ADR.

## Decision
State the decision clearly and directly. If there are multiple parts, enumerate them. Example:
1. Selected component / technology / pattern: X
2. Configuration / mode: Y
3. Where it will be used: Z

## Rationale
Explain why this decision was chosen. Provide supporting arguments, evaluation criteria, trade-offs, and why alternatives were rejected. Include:
- How the decision satisfies the Goals.
- Important trade-offs (e.g., cost vs. latency, consistency vs. availability).
- Dependencies introduced by this decision.

## Alternatives Considered
For each meaningful alternative, include:
- Name of alternative.
- Short description.
- Pros and cons.
- Why it was rejected or deferred.

(If many alternatives exist, summarize and reference separate comparison notes.)

## Consequences
List expected consequences (positive and negative), immediate and long-term:
- Technical consequences (performance, scalability, maintainability).
- Operational consequences (on-call, runbooks, ops burden).
- Business consequences (cost, time-to-market, contractual).
- Security/privacy consequences.

## Implementation Plan
High-level steps required to implement the decision. For each step include:
- Owner (team or role).
- Rough estimate of effort (S/M/L).
- Required artifacts (configs, infra changes, migration scripts).
- Risk mitigation actions for each step.

## Migration / Compatibility Strategy
If the decision replaces or changes existing behavior, describe:
- Backward compatibility considerations.
- Migration steps and data migrations (if any).
- Coexistence strategies (feature flags, dual-run).
- Expected downtime and how to minimize it.

## Rollout, Monitoring and Validation
- Rollout strategy (canary, blue/green, feature-flag phased rollout).
- Key metrics & acceptance criteria (SLIs/SLOs) to validate success.
- Monitoring & alerting requirements (dashboards, alerts).
- Success/failure conditions and corrective actions.

## Testing & QA
- Unit/Integration/E2E tests required.
- Load/performance test plan and thresholds.
- Security testing (pen-testing, code scanning).
- Contract testing (if applicable).

## Operational Considerations
- Required runbooks and playbooks.
- On-call impacts and escalation flow.
- Backup & restore & rollback playbook summary.
- Required SLOs/SLIs and error budgets.

## Security & Privacy Considerations
- Data exposure, encryption, key management needs.
- Compliance/regulatory impacts (GDPR, export controls, radio regs).
- Threats introduced or mitigated by the decision.
- Required audits or third-party reviews.

## Cost & Licensing
- Estimated cost impact (infra, licensing, engineering hours).
- Licensing risks (open-source license compatibility, vendor lock-in).

## Risks and Mitigations
List principal risks (technical, operational, business) and planned mitigations. For each risk include likelihood and impact (High/Medium/Low).

## Rollback / Deprecation Plan
- How to revert the change if rollout fails.
- The deprecation plan for the replaced technology (timelines, migration windows).
- Who owns the deprecation and final removal.

## Related ADRs / Documents
- Links to related ADR files.
- Links to SRS requirements, design docs, RFCs, tickets, benchmarks.

## References
- Links to vendor docs, standards, benchmarks, benchmarks used in analysis, blogs, RFCs, and any other sources consulted.

---

### Status History
- YYYY-MM-DD — Proposed by X
- YYYY-MM-DD — Reviewed by Y
- YYYY-MM-DD — Accepted by Z
- YYYY-MM-DD — Superseded by ADR-XXX (if applicable)

---

## Appendix (optional)
- Raw comparison data (tables, benchmark results)
- Notes from meetings or interviews (link or short excerpt)
- Example config snippets or minimal code examples


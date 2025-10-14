# ADRs

This document describes the **Architecture Decision Records (ADRs)** process, conventions, and workflow used by this repository.
It explains how to create, review, accept, amend, link, deprecate, and reference ADRs so the whole team has a consistent, auditable trail of architecture and process decisions.

---

## 1. Purpose

ADRs are short, focused documents that record an important architectural or process decision for the project. Each ADR captures:

* the **context** and problem it addresses,
* the **decision** made,
* why that decision was made (rationale),
* alternatives considered,
* consequences and implementation notes.

ADRs are **living project artifacts**: they document *why* things were chosen (not only *what*), and provide a discoverable history for future engineers, reviewers, auditors and maintainers.

---

## 2. ADR Location & File Naming

Store ADRs in a single directory in the repository:

```
docs/adr/
```

Filename convention (mandatory):

```
ADR-<NNN>_<short-slug>.md
```

* `<NNN>` is a zero-padded sequence number (e.g. 000, 001, 002, …). Use 3 digits initially, expand if needed.
* `<short-slug>` is a short dash-separated identifier (e.g. `choose-database`, `auth-design`, `ci-cd-stack`).
* Example: `ADR-001_choose-database.md`

Why numbering? Numbering keeps ADRs ordered by creation and makes cross-references stable (`ADR-001` is the canonical id).

---

## 3. ADR Template & Front-matter (use this as canonical)

Copy the canonical template for every ADR. Put the template file at:

```
docs/adr/template.md
```

Each ADR SHOULD start with a short front-matter block. Minimal required front-matter fields:

```md
# ADR-<NNN>: <Short title>

**Status:** Proposed | Accepted | Superseded | Deprecated | Rejected  
**Date:** YYYY-MM-DD  
**Authors:** Name <email>, Name <email>  
**Reviewers:** Name <email> (optional)  
**Tags:** [backend], [infra], [security], [mobile]  # free-form tags, use kebab-case
**Related SRS IDs / REQ IDs:** REQ-XXXX (optional)
**Impact Area:** Backend | API | Infra | Security | Mobile | Embedded
```

(See `docs/adr/template.md` for a full text-ready template.)

---

## 4. ADR Statuses and Lifecycle

We use explicit statuses to make ADR lifecycle and intent clear:

* **Proposed** — Drafted and ready for review. Not yet accepted.
* **Accepted** — Decision accepted after review and merged into main. Represents the project’s current position.
* **Superseded** — This ADR is replaced by a later ADR. The file remains for history, but is no longer active.
* **Deprecated** — Decision is deprecated (discouraged) but kept for record; usually followed by a superseding ADR.
* **Rejected** — The proposed decision was considered and rejected. Kept as historical record.
* **Amended** (optional) — Minor editorial or clarifying changes after acceptance. Prefer to create a new ADR that supersedes instead of editing accepted ADRs; see policy below.

**Status History:** Each ADR MUST include a small chronological status history (date, action, actor).

---

## 5. Immutable Accepted ADRs — Edit Policy

* Once an ADR reaches **Accepted**, it should be treated as **immutable**. Do **not** edit the accepted ADR to change the substance of the decision.
* If the decision needs to change, create a **new ADR** that *supersedes* the old one. In the new ADR:

  * Explain why change is required.
  * Add `Supersedes: ADR-XXX` in the Related ADRs section.
  * Set the old ADR’s status to `Superseded` via a PR referencing the new ADR.
* Minor editorial fixes (typos, formatting) may be applied to Accepted ADRs only if:

  * The PR clearly documents the change,
  * The change does not alter meaning,
  * The status history is updated with the edit entry.
  * Preferably, annotate the ADR by adding an Appendix note rather than rewriting accepted text.

This immutability preserves auditability—history should be traceable.

---

## 6. Creating a New ADR — Workflow

1. **Create ADR file**

   * Copy `docs/adr/template.md` → `docs/adr/ADR-XYZ_short-slug.md` (choose next sequence number).
   * Fill front-matter and all required sections.

2. **Open PR**

   * Push the ADR file on a topic branch named like `adr/NNN-short-slug`.
   * Open a Pull Request titled: `ADR NNN: short title — Proposed`.

3. **Assign Reviewers**

   * Assign at least one architecture reviewer and the team lead (or designated approver).
   * Link relevant issues, SRS items or design docs in the PR description.

4. **Review Process**

   * Reviewers comment; discussion should remain within PR.
   * If an ADR requires prototypes, tests, or spike reports, attach results or link to them.
   * Review cycle ends by merging when reviewers accept the ADR.

5. **Acceptance**

   * Change **Status** to `Accepted`, add the acceptance line in Status History, and merge the PR.
   * If consensus is not reached, the ADR can remain `Proposed` while alternatives are explored.

6. **Implementation**

   * Link implementation work (tasks, issues) in the ADR under Implementation Plan.
   * For any breaking changes, create migration tickets and link them.

---

## 7. PR Checklist for ADR Acceptance

When submitting an ADR PR, ensure the PR description contains:

* [ ] ADR file added at `docs/adr/ADR-<NNN>_<slug>.md`
* [ ] Front-matter populated (status = Proposed initially)
* [ ] Sufficient context, clear decision and rationale
* [ ] Alternatives considered and why rejected
* [ ] Consequences and implementation notes
* [ ] Migration / rollback plan if applicable
* [ ] At least one reviewer assigned
* [ ] Related SRS/requirements/tickets linked
* [ ] (Optional) Proof-of-concept notes, benchmarks, or prototype results
* [ ] Tests or test-plan referenced (if relevant)
* [ ] Tag(s) added for indexing/search

Mergers should set **Status** to `Accepted` and append a status history entry.

---

## 8. Superseding / Deprecating an ADR

To change a previously accepted decision:

1. Create a **new ADR** that documents the new decision; include `Supersedes: ADR-XXX` in the Related ADRs section.
2. In the old ADR, update the **Status** to `Superseded` and add a status history line referencing the supplanting ADR (this update is editorial and allowed to preserve history).
3. Link the change PRs and migration tickets.

Reason: keeping history in separate ADRs retains audit trail and clearly shows evolution of thinking.

---

## 9. Tags, Categories & Indexing

Use the `Tags` front-matter field to aid discovery. Recommended tags:

* `backend`, `infra`, `security`, `auth`, `db`, `api`, `mobile`, `embedded`, `ci-cd`, `observability`, `cost`, `legal`

Maintain an index file `docs/adr/INDEX.md` listing all ADRs with short summaries and statuses.

---

## 10. Linking ADRs to SRS, Issues & Code

* Include `Related SRS IDs / REQ IDs` in ADR front-matter pointing to the authoritative requirement in the SRS.
* Link ADRs to GitHub/GitLab issues and implementation PRs.
* In code, add a short comment referencing the ADR when code encodes a policy from an ADR. Example:

```c
// See ADR-012_cache_strategy.md for reasoning about TTLs and eviction policy
```

---

## 11. CONTRIBUTING: Changing ADRs or Adding New Ones

If you want to propose a new ADR:

1. Create the ADR file from template.
2. Open a PR with the ADR and the PR checklist filled in.
3. Add reviewers and solicit feedback.
4. After acceptance, set `Status: Accepted` and update status history.

If you disagree with an Accepted ADR:

* **Do not** edit it to change its decision. Instead create a new ADR that supersedes or amends the old ADR. Explain the reasons and migration plan.

If you spot a factual error or typo in an Accepted ADR:

* Make a small editorial PR labeled `docs/adr: fix ADR-XXX (typo)` with a short explanation in the PR description. Add a status history entry in the ADR noting the editorial change (date, author, reason).

---

## 12. Examples of Common ADRs to Expect

* `ADR-000_choose-language`
* `ADR-001_choose-database`
* `ADR-002_architecture-style`
* `ADR-003_auth-design`
* `ADR-010_ci-cd-stack`
* `ADR-011_observability-stack`

Use the tags field to make them easy to find.

---

## 13. Contact / Questions

If you're unsure which ADR to create or how to structure your proposal, ask the repo maintainers or architecture lead. Suggested contact: `bitsgenix@gmail.com` or raise an issue `docs: guidance on ADR-XYZ`.

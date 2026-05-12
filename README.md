# CVC-5: Citizen Vibe Coder Security Model

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY%20SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

**Project type:** OWASP documentation / control standard (proposed)

## Overview

This repository develops **CVC-5**, a five-domain security control model for **Citizen Vibe Coders** — non-engineers whose use of LLMs, copilots, assistants, or agents materially shapes business outputs, decisions, or operational actions.

CVC-5 operates either as a **standalone baseline** for organizations without formal AI governance, or as a **domain-specific control profile** within an existing enterprise AI governance program. The framework is technology- and vendor-neutral, scales control strength to business impact through a risk-tiering model, and keeps human accountability explicit at every step.

The working draft of the framework is [`docs/cvc-5-security-model.md`](docs/cvc-5-security-model.md). It contains a normative control catalog ([Section 7](docs/cvc-5-security-model.md#7-cvc-5-control-catalog-normative)) with stable IDs, RFC 2119 wording, and tier-by-tier applicability, plus a self-assessment checklist ([Appendix C](docs/cvc-5-security-model.md#appendix-c-self-assessment-checklist)).

## Standard Structure

- **Part 1 — Normative core.** Sections 1–7 of the framework document: Purpose, Scope, Design Principles, Governance Positioning, Threat Model, Risk Tiering Model, and the CVC-5 Control Catalog (Section 7) with stable control IDs in the pattern `CVC-<domain>.<n>`.
- **Part 2 — Operational integration.** Sections 8–11: Minimum Starting Baseline, Roles and Decision Rights, Quick-Start Policy Language, and Metrics and Evidence. Normative where they prescribe behavior; supporting elsewhere.
- **Appendices A–C — Non-normative guidance.** Framework cross-walks, definitions, and the self-assessment checklist derived from the catalog.
- **How to use it.** Read the introduction and pick your governance path (Plug-in or Standalone). Set your Tier 1 threshold ([Section 6](docs/cvc-5-security-model.md#6-risk-tiering-model)). Adopt controls from [Section 7](docs/cvc-5-security-model.md#7-cvc-5-control-catalog-normative) at the tier(s) you operate. Self-assess against [Appendix C](docs/cvc-5-security-model.md#appendix-c-self-assessment-checklist).
- **RFC 2119 keywords.** MUST, SHOULD, and MAY in the framework document are interpreted per RFC 2119; recommendations are tier-scoped in each control's *Applicability* line.

## Project Leads

- **Project Lead:** Alton Crossley, Project Lead, @Xcaciv
- **Co-Lead / Maintainer:** *TBD*

## The five domains

1. **CVC-1** — Discovery and Registration
2. **CVC-2** — Data Boundary Protection
3. **CVC-3** — Prompt, Agent, and Action Safety
4. **CVC-4** — Output Validation and Human Accountability
5. **CVC-5** — Governance, Audit, and Incident Readiness

## Status

Draft v0.9.1, in active development. See [Roadmap](#roadmap) for the path to a stable 1.0.

## Relationship to OWASP FIASSE

[FIASSE (Framework for Integrating Application Security into Software Engineering)](https://github.com/OWASP/FIASSE) and CVC-5 address different modes of AI-assisted work and are designed to complement, not overlap.

**OWASP FIASSE is creational guidance.** It directs how software engineers build securable code, AI-assisted or not. FIASSE's core model (SSEM) gives developers a design language for building software with inherent qualities like maintainability, trustworthiness, and reliability. FIASSE concerns the artifact being produced: is the code being written with properties that make it defensible and maintainable over time? When a professional engineer uses an AI copilot to generate code, FIASSE provides the engineering principles that define what "good" looks like for that output.

**CVC-5 is operational governance and guardrails.** It governs how business users operate AI tools, agents, and workflows to produce business outcomes. CVC-5's concern is not the quality of the artifact but the safety of the process: is sensitive data being handled appropriately, are agents operating within sanctioned boundaries, are outputs being reviewed before they influence decisions? CVC-5 does not require its users to understand software engineering; it requires them to follow safe operating procedures.

## Relationship to OWASP Projects

CVC-5 borrows threat taxonomy from three active OWASP projects but is not a replacement for or extension of any of them. Its role is to translate that taxonomy into an operational control model for a persona none of the three projects directly address: the non-engineer performing material business work through AI tools they did not build.

**OWASP Citizen Development Top 10 (CD-SEC-01–10)**
The closest analogue. The Citizen Dev Top 10 covers the risk surface for business users operating AI-assisted and low-code/no-code tools, including blind trust in AI output (CD-SEC-01), data leakage (CD-SEC-04), shadow AI (CD-SEC-09), and agent identity misuse (CD-SEC-02). CVC-5 treats the Citizen Dev Top 10 as its primary threat reference for the human-behavior layer. The gap CVC-5 fills is operational: the Citizen Dev Top 10 lists risks and mitigations at the individual level but does not provide the organizational control structure, governance integration model, or risk tiering that practitioners need to implement policy.

**OWASP LLM Top 10 (LLM01–LLM10)**
Written for developers and security teams building or deploying LLM applications. CVC-5 draws on it for technical risk framing. Specifically referencing prompt injection (LLM01), sensitive data exposure (LLM02), supply chain risk (LLM03), and excessive agency (LLM06). CVC-5 recontextualizes these risks from the perspective of a business user operating within an LLM-powered tool or workflow rather than building one.

**OWASP Agentic Top 10 (ASI01–ASI10)**
Covers risks specific to autonomous agent systems: goal hijacking (ASI01), unsafe action chains (ASI02), over-permissioned tools (ASI03), and auditability gaps (ASI08). CVC-5 applies these risks to the scenario where a Citizen Vibe Coder is invoking or operating an agent — not architecting one. The control responses in CVC-3 (Prompt, Agent, and Action Safety) and CVC-5 (Governance, Audit, and Incident Readiness) operationalize the Agentic Top 10 mitigations at the business-unit level.
A full cross-walk mapping each CVC-5 domain to its corresponding OWASP reference codes is in [Appendix A](docs/cvc-5-security-model.md#appendix-a-framework-cross-walk) of the framework document.

## Contribution Model

CVC-5 is developed as an open, community-reviewed draft. Contributions are welcome from security practitioners, governance and risk specialists, AI/ML engineers, and citizen developers operating within the model's scope.

### What we accept

- **Scope refinements** — clarifying in-scope vs. out-of-scope activities, persona definitions, or boundary cases.
- **Control additions or revisions** — proposed controls, threat-model updates, or risk-tier adjustments within any of the five domains.
- **Framework cross-walks** — mappings to NIST AI RMF, ISO/IEC 42001, EU AI Act, OWASP LLM/Agentic/Citizen Dev, or other AI governance standards.
- **Implementation reports** — case studies, lessons learned, or organizational adaptation notes (anonymized as needed).
- **Editorial improvements** — clarity, consistency, terminology, and accessibility.

### How to contribute

1. For typo or wording fixes, open a direct PR against [`docs/cvc-5-security-model.md`](docs/cvc-5-security-model.md).
2. For control, scope, or structural changes, open an issue first to discuss intent and fit before sending a PR.
3. Match the existing structure, tone, and `[Standalone]` / `[Plug-in]` tagging conventions used in the framework document.
4. Keep PRs focused — one change of substance per PR makes review and provenance cleaner.

### Review and merge

- Editorial PRs are merged at maintainer discretion.
- Control-model and scope PRs require issue discussion and explicit maintainer sign-off.
- Substantive structural changes may be deferred to a numbered release cycle to keep the draft stable for reviewers.
- All contributions are accepted under the project license (CC-BY-SA-4.0); contributors retain attribution.

## Roadmap

The roadmap below tracks the working draft toward a stable 1.0 release and the enablement work that follows. Item ordering reflects priority, not commitment to specific dates.

### Toward v1.0

- Harden the [Section 7 control catalog](docs/cvc-5-security-model.md#7-cvc-5-control-catalog-normative): tighten RFC 2119 wording, close any remaining principle-or-threat gaps, and lock the control IDs.
- Finalize the risk-tiering model and the organization-defined thresholds that trigger each tier.
- Stabilize Appendix A cross-walks (NIST AI RMF, ISO/IEC 42001, EU AI Act, OWASP LLM/Agentic/Citizen Dev).
- External review of the catalog and the [Appendix C self-assessment checklist](docs/cvc-5-security-model.md#appendix-c-self-assessment-checklist) by security, governance, audit, and citizen-developer practitioners.
- Resolve open editorial inconsistencies and tighten persona examples and worked scenarios.

### Post-1.0 enablement

- Implementation guide and quick-start templates for `[Standalone]` adopters.
- Integration notes and reference artifacts for `[Plug-in]` adoption alongside existing enterprise AI governance.
- Reference policies, registration forms, and intake templates supporting CVC-1.
- Tooling-friendly machine-readable export of the control catalog and the self-assessment checklist.

### Not planned

- Tooling, scanners, or automated compliance products.
- Vendor- or product-specific configuration guides.
- Certification, attestation, or conformance schemes.

## License

Licensed under [Creative Commons Attribution-ShareAlike 4.0 International (CC-BY-SA-4.0)](licence.txt).

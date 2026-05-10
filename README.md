# CVC-5: Citizen Vibe Coder Security Framework

This repository develops **CVC-5**, a five-domain security control model for **Citizen Vibe Coders** — non-engineers whose use of LLMs, copilots, assistants, or agents materially shapes business outputs, decisions, or operational actions.

CVC-5 operates either as a **standalone baseline** for organizations without formal AI governance, or as a **domain-specific control profile** within an existing enterprise AI governance program.

## Contents

- [`docs/cvc-5-security-model.md`](docs/cvc-5-security-model.md) — the working draft of the framework.

## The five domains

1. **CVC-1** — Discovery and Registration
2. **CVC-2** — Data Boundary Protection
3. **CVC-3** — Prompt, Agent, and Action Safety
4. **CVC-4** — Output Validation and Human Accountability
5. **CVC-5** — Governance, Audit, and Incident Readiness

## Status

Draft, in active development.

## Relationship to OWASP FIASSE

[FIASSE (Framework for Integrating Application Security into Software Engineering)](docs/fiasse-rfc.md) and CVC-5 address different modes of AI-assisted work and are designed to complement, not overlap.

**OWASP FIASSE is creational guidance.** It directs how software engineers build securable code, AI-assisted or not. FIASSE's core model (SSEM) gives developers a design language for building software with inherent qualities like maintainability, trustworthiness, and reliability. FIASSE concerns the artifact being produced: is the code being written with properties that make it defensible and maintainable over time? When a professional engineer uses an AI copilot to generate code, FIASSE provides the engineering principles that define what "good" looks like for that output.

**CVC-5 is operational governance and guardrails.** It governs how business users operate AI tools, agents, and workflows to produce business outcomes. CVC-5's concern is not the quality of the artifact but the safety of the process: is sensitive data being handled appropriately, are agents operating within sanctioned boundaries, are outputs being reviewed before they influence decisions? CVC-5 does not require its users to understand software engineering; it requires them to follow safe operating procedures.

## Relationship to OWASP Projects

CVC-5 borrows threat taxonomy from three active OWASP projects but is not a replacement for or extension of any of them. Its role is to translate that taxonomy into an operational control model for a persona none of the three projects directly address: the non-engineer performing material business work through AI tools they did not build.

**OWASP Citizen Development Top 10 (CD-SEC-01–10)**
The closest analogue. The Citizen Dev Top 10 covers the risk surface for business users operating AI-assisted and low-code/no-code tools, including blind trust in AI output (CD-SEC-01), data leakage (CD-SEC-04), shadow AI (CD-SEC-09), and agent identity misuse (CD-SEC-02). CVC-5 treats the Citizen Dev Top 10 as its primary threat reference for the human-behavior layer. The gap CVC-5 fills is operational: the Citizen Dev Top 10 lists risks and mitigations at the individual level but does not provide the organizational control structure, governance integration model, or risk tiering that practitioners need to implement policy.

**OWASP LLM Top 10 (LLM01–LLM10)**
Written for developers and security teams building or deploying LLM applications. CVC-5 draws on it for technical risk framing — prompt injection (LLM01), sensitive data exposure (LLM02), supply chain risk (LLM03), and excessive agency (LLM06) — but recontextualizes these risks from the perspective of a business user operating within an LLM-powered tool or workflow rather than building one.

**OWASP Agentic Top 10 (ASI01–ASI10)**
Covers risks specific to autonomous agent systems: goal hijacking (ASI01), unsafe action chains (ASI02), over-permissioned tools (ASI03), and auditability gaps (ASI08). CVC-5 applies these risks to the scenario where a Citizen Vibe Coder is invoking or operating an agent — not architecting one. The control responses in CVC-3 (Prompt, Agent, and Action Safety) and CVC-5 (Governance, Audit, and Incident Readiness) operationalize the Agentic Top 10 mitigations at the business-unit level.
A full cross-walk mapping each CVC-5 domain to its corresponding OWASP reference codes is in [Appendix A](docs/cvc-5-security-model.md#appendix-a-framework-cross-walk) of the framework document.

## Contributing

Issues and pull requests refining scope, controls, threat model, or framework cross-walks (NIST AI RMF, ISO/IEC 42001, EU AI Act, OWASP LLM/Agentic/Citizen Dev) are welcome.

## License

Licensed under [Creative Commons Attribution-ShareAlike 4.0 International (CC-BY-SA-4.0)](licence.txt).

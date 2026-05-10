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

## Relationship to FIASSE

[FIASSE (Framework for Integrating Application Security into Software Engineering)](docs/fiasse-rfc.md) and CVC-5 address different modes of the AI-assisted work and are designed to complement, not overlap.

**FIASSE is creational guidance.** It directs how software engineers build securable code, AI-assisted or not. Its core model (SSEM) gives developers a design language for building software with inherent qualities like maintainability, trustworthiness, and reliability. FIASSE's concern is the artifact being produced: is the code being written with properties that make it defensible and maintainable over time? When a professional engineer uses an AI copilot to generate code, FIASSE provides the engineering principles that define what "good" looks like for that output.

**CVC-5 is operational governance and guardrails.** It governs how business users — who are not engineers — operate AI tools, agents, and workflows to produce business outcomes. CVC-5's concern is not the quality of the artifact but the safety of the process: is sensitive data being handled appropriately, are agents operating within sanctioned boundaries, are outputs being reviewed before they influence decisions? CVC-5 does not require its users to understand software engineering; it requires them to follow safe operating procedures.

## Contributing

Issues and pull requests refining scope, controls, threat model, or framework cross-walks (NIST AI RMF, ISO/IEC 42001, EU AI Act, OWASP LLM/Agentic/Citizen Dev) are welcome.

## License

Licensed under [Creative Commons Attribution-ShareAlike 4.0 International (CC-BY-SA-4.0)](licence.txt).
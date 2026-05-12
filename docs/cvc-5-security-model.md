# CVC-5: Citizen Vibe Coder Security Framework

**Type:** Security control standard
**Status:** Draft v0.9.1
**Date:** May 7, 2026

***

## How to Use This Document

This framework serves two audiences. Find your path before reading further.

**Path A — Your organization already has an AI governance program:**
CVC-5 is a domain-specific control profile for business-led AI use. Start at [Section 4: Governance Positioning](#4-governance-positioning) to understand how CVC-5 plugs in, then go to [Section 6: The CVC-5 Control Model](#6-the-cvc-5-control-model) for control details. Ignore "Standalone" tags.

**Path B — No formal AI governance exists yet:**
CVC-5 is your initial control structure. Start at [Section 8: Minimum Starting Baseline](#8-minimum-starting-baseline) to get oriented, then return to [Section 6: The CVC-5 Control Model](#6-the-cvc-5-control-model). Pay attention to "Standalone" tags. Commit to refactoring CVC-5 into a plug-in profile once enterprise governance is established.

> **Key terms used throughout this document:**
>
> - **Citizen Vibe Coder** — a non-engineer whose use of LLMs, copilots, assistants, or agents materially shapes business outputs, decisions, or operational actions.
> - **Material work** — work output that influences business outcomes to a degree warranting management attention if an error or harm occurs.
> - **Shadow AI** — AI tools, assistants, agents, or workflows not registered, approved, or visible to security and governance functions.
> - **Least agency** — granting an agent the minimum autonomy, tools, and action scope required for its function; broader autonomy is earned, not default.
>
> *Full definitions in [Appendix B](#appendix-b-definitions).*

***

## 1. Purpose

CVC-5 is a five-domain security control model for business users who perform material work via LLMs, AI assistants, copilots, or agentic workflows (Citizen Vibe Coders). It operates as a standalone baseline or as a domain-specific control profile within a broader enterprise AI governance program.

***

## 2. Scope

### In scope

- Drafting analyses, recommendations, summaries, decisions, or policies via AI that influence business outcomes
- Operating embedded AI assistants in enterprise SaaS to generate outputs or initiate actions
- Moving AI-produced content into tickets, emails, reports, spreadsheets, forms, or procedures
- Running LLM-driven workflows that retrieve documents, call tools/APIs, or produce downstream effects
- Producing scripts, formulas, queries, or automations as incidental artifacts of LLM-mediated processes
- Building or invoking custom agents, GPTs, retrieval pipelines, or MCP integrations under business-unit ownership

Code generation is not required for a workflow to be in scope.

### Out of scope

- Professional software development lifecycle and engineering security controls
- Low-code/no-code platform administration
- Model development, fine-tuning, dataset curation, or MLOps
- Enterprise AI strategy, ethics, vendor management, and contract review owned by other functions

***

## 3. Design Principles

1. **Standalone yet composable.** Operates as a complete minimum viable control system without enterprise AI governance; each control maps to existing enterprise capabilities.
2. **Technology and vendor neutral.** Applies regardless of AI product, vendor, deployment model, or interaction modality.
3. **Outcome focus.** Targets risk-creating outcomes, not implementation form. Code production is not the determining factor.
4. **Explicit human accountability.** A human remains accountable for inputs, configuration, outputs, and resulting actions. AI assistance does not transfer ownership.
5. **Secure enablement.** Approved patterns must be easier than shadow patterns. Prohibition must be specific, narrow, and accompanied by a sanctioned alternative.
6. **Risk proportionality.** Control strength scales with business impact via the risk tiering model.

***

## 4. Governance Positioning

> **`[Plug-in]`** — Relevant when enterprise AI governance already exists.
> **`[Standalone]`** — Relevant when CVC-5 is the first formal structure.

### `[Plug-in]` Integration with Enterprise Governance

CVC-5 is a domain-specific control profile for business-led AI use. It translates enterprise policy into operational controls; it does not form a parallel reporting chain.

| Enterprise layer | CVC-5 contribution |
|---|---|
| AI policy and acceptable use | Discoverable, machine-readable guardrails; registration and review triggers |
| Data governance and privacy | Applies data rules to prompts, uploads, retrieval, embeddings, agent memory |
| Identity and access management | Least-privilege inheritance, scoped tokens, approval boundaries |
| Vendor and third-party risk | Inventory and use-case detail for meaningful third-party AI risk evaluation |
| Security operations | Logging, alerting, and incident categories for AI-assisted actions and shadow AI |
| Internal audit and compliance | Provenance records, approvals, and traceability for material AI outputs |

| Condition | CVC-5 behavior |
|---|---|
| Existing governance is stricter | Existing requirements prevail without modification. |
| Existing governance is silent on AI prompts, agents, or business-side workflows | CVC-5 fills the control gap. |
| Exceptions and escalations | Flow through existing governance bodies. |
| Metrics | Feed upward into enterprise governance reporting; do not form a parallel chain. |

Position CVC-5 explicitly as a domain-specific control profile for citizen vibe coding under the broader enterprise AI control system.

### `[Standalone]` First-Formal-Structure Commitments

When no enterprise governance exists, CVC-5 serves as the initial control structure. Required commitments:

- Present as a security and operational control standard, not AI strategy or enterprise policy.
- Document decisions in a form inheritable by future governance bodies.
- Review annually; refactor to plug-in profile once enterprise governance is established.

### Framework Alignment

*For compliance officer reference — see [Appendix A: Framework Cross-Walk](#appendix-a-framework-cross-walk) for full mapping.*

CVC-5 contributes to NIST AI RMF 1.0 Map, Measure, and Manage functions; maps to ISO/IEC 42001:2023 Clause 4 and Annex A; and supports EU AI Act Article 26 deployer compliance evidence.

***

## 5. Threat Model

> **Guidance:** Taxonomy reference codes (OWASP LLM Top 10, Agentic Top 10, Citizen Dev Top 10) are retained in [Appendix A: Framework Cross-Walk](#appendix-a-framework-cross-walk) for specialist cross-reference.

| Risk | Description |
|---|---|
| Shadow AI | Unregistered tools, assistants, agents, or workflows |
| Prompt/context data exposure | Sensitive data in prompts, uploads, retrieval, or agent tool use |
| Prompt injection | External content directs AI to ignore rules or take unsafe actions |
| Unsafe autonomous actions | Agents send messages, modify records, or trigger processes without review |
| Output reliability / hallucination | AI-generated content is incorrect, biased, or incomplete |
| Excessive agency / over-permissioned tools | Connected tools operate with broader scope than required |
| Memory and retrieval poisoning | Persistent corruption of agent memory or knowledge bases |
| Improper output handling | Model output rendered, executed, or passed downstream without validation |
| Identity confusion / confused-deputy | Agents inherit user identity and the union of privileges across connected systems |
| Auditability gap | Inability to reconstruct prompts, context, tools, or approvals leading to a decision |
| Blind trust | Users over-trust AI output or generated actions without independent review |
| Supply-chain / component risk | Compromised models, tools, or MCP servers introduce malicious behavior |

**Key assumptions driving this framework:**

- Prompt injection cannot be reliably prevented at the model layer. The framework treats it as a containment problem, not a prevention problem.
- Business users have legitimate role-appropriate system access; AI tools extend what data is retrievable in practice even when access-control models are unchanged.
- Visibility into AI activity is incomplete by default. Controls must function under partial visibility.

***

## 6. Risk Tiering Model

CVC-5 applies three risk tiers. Every control in [Section 7: CVC-5 Control Catalog](#7-cvc-5-control-catalog-normative) names the tiers for which it is REQUIRED and the tiers for which it is RECOMMENDED. Tier classification MUST be based on the most sensitive downstream use the output could reasonably reach, not on the user's intent at time of use.

| Tier | Label | Typical use cases | Minimum control expectation |
|---|---|---|---|
| Tier 1 | **Low — Individual or Public-Data Use** | Drafting with public or low-sensitivity data; brainstorming and exploration; one-off assistance with no system action and no external sharing. | Acceptable-use rules apply; registration optional below a defined volume threshold. |
| Tier 2 | **Moderate — Team or Internal Use** | Recurring use of internal data for business analysis or decision support; outputs influence operations but do not directly trigger action; team-shared assets. | Registration required; approved tools only; output review required for material use. |
| Tier 3 | **High — Regulated or Material-Action Use** | Sensitive, regulated, or business-confidential data; external communication; tool-calling or record changes; HR, legal, financial, or compliance impact; agentic execution of business-meaningful actions. | Registration with named owner; approved enterprise environment; explicit confirmation gates for action; logging, review, and provenance mandatory. |

The Tier 1 registration threshold MUST be set by each organization, documented with its decision date, and re-evaluated at least annually.

> **Guidance — Setting the Tier 1 threshold.** Determine your threshold by answering two questions:
>
> 1. At what frequency or business impact does unregistered use create unacceptable visibility gaps? (e.g., any recurring use, any use producing outputs shared beyond the originating team)
> 2. How will edge cases between Tier 1 and Tier 2 be adjudicated, and by whom?
>
> Record the decision in the same artifact that holds the use-case inventory required by [CVC-1.2](#cvc-1-discovery-and-registration).

***

## 7. CVC-5 Control Catalog (Normative)

This section is the normative core of CVC-5. Each control has a stable identifier in the pattern `CVC-<domain>.<n>`, a normative statement using RFC 2119 keywords (MUST, SHOULD, MAY), an applicability statement by risk tier, the primary risks it addresses, and references to the cross-walks in [Appendix A](#appendix-a-framework-cross-walk).

Controls are tagged `[Plug-in]` where behavior differs when enterprise AI governance exists, and `[Standalone]` where the control must be self-contained. Where a control names another, the referenced control governs.

***

### CVC-1. Discovery and Registration

**Objective:** Convert unknown AI use into known AI use.

**CVC-1.1 — AI tool classification register**
- **Statement:** The organization MUST maintain an AI tool classification register with at least three statuses: *approved for sensitive work*, *approved for limited use*, *prohibited for corporate data*.
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** Shadow AI; Supply-chain / component risk.
- **References:** OWASP CD-SEC-09; OWASP LLM03; NIST AI RMF Map 1; ISO/IEC 42001 Clause 4; EU AI Act Art. 11.

**CVC-1.2 — Use-case registration and ownership**
- **Statement:** All recurring or material business use of LLMs, copilots, assistants, agents, custom GPTs, and MCP-connected workflows MUST be registered with a designated human owner.
- **Applicability:** Required for Tier 2 and Tier 3. Recommended for Tier 1; registration becomes required once organization-defined volume thresholds are crossed (see [Section 6](#6-risk-tiering-model)).
- **Primary risks:** Shadow AI; Auditability gap.
- **References:** OWASP CD-SEC-09; OWASP ASI04; NIST AI RMF Map 1, Map 2; ISO/IEC 42001 Clause 4 (Annex A inventory); EU AI Act Art. 11.

**CVC-1.3 — Use-case metadata schema**
- **Statement:** Each registered use case MUST record at minimum: owning team, business purpose, data classes involved, connected tools and data sources, output type, whether automated actions occur, and the level of human review applied.
- **Applicability:** Required for Tier 2 and Tier 3. Recommended for Tier 1 where registration applies.
- **Primary risks:** Shadow AI; Auditability gap; Excessive agency / over-permissioned tools.
- **References:** OWASP CD-SEC-09; OWASP ASI04, ASI08; NIST AI RMF Map 2; ISO/IEC 42001 Annex A; EU AI Act Art. 11.

**CVC-1.4 — Active discovery mechanisms**
- **Statement:** Discovery of AI use MUST combine self-attestation, network and identity telemetry, periodic business-unit reviews, and reconciliation against the sanctioned-tool register. No single mechanism is sufficient.
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** Shadow AI; Auditability gap.
- **References:** OWASP CD-SEC-09; OWASP ASI04; NIST AI RMF Map 1, Map 2.

**CVC-1.5 — AI-BOM expression**
- **Statement:** Where automated discovery is technically feasible, the resulting use-case record SHOULD be expressed as an AI-BOM (SPDX 3.0 or CycloneDX) capturing models, datasets, prompts, system prompts, embeddings, vector stores, MCP servers, and tool integrations. For Tier 3 use cases, the AI-BOM MUST be produced where the underlying tools support it.
- **Applicability:** Required for Tier 3 where supported. Recommended for Tier 2.
- **Primary risks:** Supply-chain / component risk; Shadow AI; Memory and retrieval poisoning.
- **References:** OWASP LLM03; OWASP ASI04; NIST AI RMF Map 2; ISO/IEC 42001 Annex A; EU AI Act Art. 11.

**CVC-1.6 — Inventory authority**
- **Statement:** `[Plug-in]` The use-case inventory and AI-BOM MUST feed into the enterprise AI governance register; a parallel inventory MUST NOT be maintained. `[Standalone]` The use-case inventory MUST be designated the authoritative organizational record until enterprise governance is established, with a named maintainer assigned.
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** Auditability gap; Shadow AI.
- **References:** NIST AI RMF Govern 1; ISO/IEC 42001 Clauses 4, 9; EU AI Act Art. 26(5).

***

### CVC-2. Data Boundary Protection

**Objective:** Prevent inappropriate disclosure of sensitive data into AI systems; constrain what AI systems can retrieve, expose, or carry across boundaries.

**CVC-2.1 — AI-extended data classification**
- **Statement:** Enterprise data classification MUST be extended to AI usage with explicit rules covering prompts, file uploads, retrieval content, embedded indexes, copied context, and downstream responses.
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** Prompt/context data exposure; Improper output handling.
- **References:** OWASP LLM02, LLM08; OWASP CD-SEC-04, CD-SEC-05; NIST AI RMF Manage 2; ISO/IEC 42001 Clause 8; EU AI Act Art. 26(4).

**CVC-2.2 — Prohibition of high-sensitivity data in public AI tools**
- **Statement:** Submission of high-sensitivity data to public or consumer AI tools MUST be prohibited without a documented exception granted under [CVC-5.8](#cvc-5-governance-audit-and-incident-readiness).
- **Applicability:** Required for Tier 2 and Tier 3. Recommended for Tier 1.
- **Primary risks:** Prompt/context data exposure; Shadow AI.
- **References:** OWASP LLM02; OWASP CD-SEC-04; NIST AI RMF Manage 2; ISO/IEC 42001 Clause 8; EU AI Act Art. 26(4).

**CVC-2.3 — Approved enterprise environment for sensitive use**
- **Statement:** Any use of internal sensitive, regulated, or business-confidential data MUST occur within an approved enterprise AI environment.
- **Applicability:** Required for Tier 2 and Tier 3.
- **Primary risks:** Prompt/context data exposure; Shadow AI.
- **References:** OWASP LLM02; OWASP CD-SEC-04, CD-SEC-05; ISO/IEC 42001 Clause 8; EU AI Act Art. 26(4).

**CVC-2.4 — Least-privilege connectors and short-lived credentials**
- **Statement:** Connectors, plugins, and tools accessible to AI assistants MUST operate under least privilege. Short-lived credentials MUST be used where the underlying systems support them.
- **Applicability:** Required for Tier 2 and Tier 3. Recommended for Tier 1.
- **Primary risks:** Excessive agency / over-permissioned tools; Identity confusion / confused-deputy.
- **References:** OWASP ASI06; OWASP CD-SEC-05; NIST AI RMF Manage 2; ISO/IEC 42001 Clause 8.

**CVC-2.5 — Detective controls for leakage patterns**
- **Statement:** Where technically feasible, preventive or detective controls SHOULD be deployed for obvious leakage patterns (secrets, PCI data, PHI). Absence MUST be recorded as a control gap in the use case's record under [CVC-1.3](#cvc-1-discovery-and-registration).
- **Applicability:** Required for Tier 3. Recommended for Tier 2.
- **Primary risks:** Prompt/context data exposure.
- **References:** OWASP LLM02; OWASP CD-SEC-04; NIST AI RMF Measure 2.

**CVC-2.6 — Access controls on retrieval indexes and vector stores**
- **Statement:** Vector stores and retrieval indexes MUST enforce access controls equivalent to those on the underlying source data.
- **Applicability:** Required for Tier 2 and Tier 3.
- **Primary risks:** Prompt/context data exposure; Memory and retrieval poisoning.
- **References:** OWASP LLM02, LLM08; OWASP CD-SEC-04; ISO/IEC 42001 Clause 8.

**CVC-2.7 — Category-based prohibition with governed allowlist**
- **Statement:** Prohibitions MUST be expressed by category (e.g., "public consumer AI tools," "personal AI accounts not provisioned by IT") rather than by named product. A separately governed allowlist of approved tools MUST exist with an explicitly assigned owner and a documented review cadence.
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** Shadow AI; Supply-chain / component risk.
- **References:** OWASP CD-SEC-09; OWASP LLM03; NIST AI RMF Govern 4; ISO/IEC 42001 Clause 4.

> **Guidance — Why split prohibition from allowlist.** The category-level prohibition is a stable policy artifact and changes infrequently. The allowlist is an operational artifact that turns over as the market evolves. Separating them keeps policy churn low and shortens the path to approving new tools without rewriting prohibitions.

**CVC-2.8 — Minimum data-classification scheme (Standalone prerequisite)**
- **Statement:** `[Standalone]` Where no enterprise data classification scheme exists, a minimum three-tier classification (public / internal / restricted) MUST be established as a prerequisite to applying CVC-2.1 through CVC-2.6.
- **Applicability:** Required at the organizational level when operating in Standalone mode.
- **Primary risks:** Prompt/context data exposure; Auditability gap.
- **References:** ISO/IEC 42001 Clause 8; NIST AI RMF Manage 2.

***

### CVC-3. Prompt, Agent, and Action Safety

**Objective:** Prevent AI systems from following malicious instructions, exceeding authority, or performing unsafe actions.

**CVC-3.1 — Treat external content as untrusted**
- **Statement:** External content processed by AI systems — including emails, attachments, web pages, documents, transcripts, and meeting recordings — MUST be treated as untrusted input.
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** Prompt injection; Memory and retrieval poisoning.
- **References:** OWASP LLM01; OWASP ASI01; OWASP CD-SEC-02; NIST AI RMF Manage 1; ISO/IEC 42001 Clause 8.

**CVC-3.2 — Instruction/content separation in business-critical workflows**
- **Statement:** Business-critical workflows MUST use prompt and system-instruction patterns that separate untrusted content from operating instructions and that refuse to follow embedded directives without explicit user confirmation.
- **Applicability:** Required for Tier 3. Recommended for Tier 2.
- **Primary risks:** Prompt injection; Unsafe autonomous actions.
- **References:** OWASP LLM01, LLM05; OWASP ASI01, ASI02; OWASP CD-SEC-02; NIST AI RMF Manage 1.

**CVC-3.3 — Default read-only access for AI tools and agents**
- **Statement:** AI-connected tools and agents MUST default to read-only access. Write, modify, or send capabilities MAY be granted only through a documented decision under the least-agency standard in [CVC-3.7](#cvc-3-prompt-agent-and-action-safety).
- **Applicability:** Required for Tier 2 and Tier 3.
- **Primary risks:** Unsafe autonomous actions; Excessive agency / over-permissioned tools.
- **References:** OWASP ASI02, ASI03; OWASP LLM06; OWASP CD-SEC-03, CD-SEC-07; NIST AI RMF Manage 4.

**CVC-3.4 — Out-of-band human confirmation for material actions**
- **Statement:** Any action that sends data externally, modifies records, changes entitlements, transfers funds, or produces material outcomes MUST require explicit human confirmation captured outside the AI chat surface.
- **Applicability:** Required for Tier 3. Recommended for Tier 2.
- **Primary risks:** Unsafe autonomous actions; Blind trust; Identity confusion / confused-deputy.
- **References:** OWASP ASI02, ASI07; OWASP LLM06; OWASP CD-SEC-01, CD-SEC-03; NIST AI RMF Manage 4; EU AI Act Art. 26(2).

**CVC-3.5 — Forbidden autonomous-action categories**
- **Statement:** The organization MUST define and enforce a list of forbidden autonomous-action categories, including at minimum: employment status changes, payment approvals, contract execution, access provisioning, and regulated communications.
- **Applicability:** Required at the organizational level for all tiers. Enforced for Tier 2 and Tier 3 use cases.
- **Primary risks:** Unsafe autonomous actions; Excessive agency / over-permissioned tools.
- **References:** OWASP ASI02, ASI03, ASI05; OWASP LLM06; OWASP CD-SEC-03; NIST AI RMF Manage 4; EU AI Act Art. 26(2).

**CVC-3.6 — Per-agent non-human identity with scoped credentials**
- **Statement:** Each agent MUST operate under its own non-human identity with scoped credentials and short-lived tokens. User-impersonation patterns for agent execution MUST NOT be used.
- **Applicability:** Required for Tier 2 and Tier 3.
- **Primary risks:** Identity confusion / confused-deputy; Excessive agency / over-permissioned tools.
- **References:** OWASP ASI03, ASI07; OWASP CD-SEC-02; NIST AI RMF Manage 4.

**CVC-3.7 — Least agency for capability expansion**
- **Statement:** Decisions granting an agent new tools, broader scopes, or auto-approval permissions MUST apply the least-agency standard: the expansion MUST be justified, documented, and reviewable.
- **Applicability:** Required for Tier 2 and Tier 3.
- **Primary risks:** Excessive agency / over-permissioned tools; Unsafe autonomous actions.
- **References:** OWASP ASI02, ASI03; OWASP LLM06; OWASP CD-SEC-07; NIST AI RMF Manage 4.

**CVC-3.8 — AI-gateway or compensating controls for business-critical workflows**
- **Statement:** `[Plug-in]` Where AI governance or AI-gateway capabilities are available, prompt-injection detection, output policy enforcement, rate and budget limits, and egress allowlisting MUST be applied to business-critical workflows. `[Standalone]` In the absence of an AI gateway, compensating controls MUST be applied: manual workflow checklists for Tier 3 actions, peer confirmation for high-risk outputs, and documented review records.
- **Applicability:** Required for Tier 3. Recommended for Tier 2.
- **Primary risks:** Prompt injection; Unsafe autonomous actions; Improper output handling.
- **References:** OWASP LLM01, LLM05, LLM10; OWASP ASI01, ASI02, ASI05; NIST AI RMF Manage 1, Manage 4.

**CVC-3.9 — Forbidden-action list ownership and change control**
- **Statement:** The forbidden autonomous-action categories list MUST have a single named owner with unilateral authority to add categories. Removal of a category MUST require a documented two-person review (Security plus Legal or Compliance). The full list MUST be reviewed at least quarterly. Additions take effect immediately; removals require justification recorded against the use-case inventory.
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** Unsafe autonomous actions; Auditability gap.
- **References:** OWASP ASI02, ASI08; NIST AI RMF Govern 1, Govern 4; ISO/IEC 42001 Clause 5.

> **Guidance — Why an asymmetric change-control.** In environments where new agent capabilities emerge faster than committees can convene, this asymmetry (one-person add, two-person remove) keeps the prohibition list current without creating a bottleneck on protective additions.

***

### CVC-4. Output Validation and Human Accountability

**Objective:** Prevent plausible but incorrect AI output from becoming an authoritative business artifact or decision.

**CVC-4.1 — Output classification tiers**
- **Statement:** AI outputs MUST be classified into at least three tiers: *reference-only*, *business input*, *action-enabling*. Classification MUST be visible to downstream consumers of the output.
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** Blind trust; Output reliability / hallucination; Improper output handling.
- **References:** OWASP LLM05, LLM09; OWASP ASI09, ASI10; OWASP CD-SEC-01, CD-SEC-08; NIST AI RMF Measure 2.

**CVC-4.2 — Named accountable reviewer**
- **Statement:** Any AI-assisted output that influences decisions, records, controls, legal statements, or customer-facing commitments MUST have a named accountable reviewer recorded.
- **Applicability:** Required for Tier 2 and Tier 3. Recommended for Tier 1.
- **Primary risks:** Blind trust; Output reliability / hallucination; Auditability gap.
- **References:** OWASP LLM09; OWASP ASI10; OWASP CD-SEC-01; NIST AI RMF Measure 3; ISO/IEC 42001 Clause 9; EU AI Act Art. 26(2), Art. 50.

**CVC-4.3 — Source validation for material claims**
- **Statement:** Source validation MUST be performed for quantitative claims, legal interpretations, policy language, regulatory references, and operational procedures used beyond the draft stage.
- **Applicability:** Required for Tier 3. Recommended for Tier 2.
- **Primary risks:** Output reliability / hallucination; Blind trust.
- **References:** OWASP LLM09; OWASP CD-SEC-01; NIST AI RMF Measure 2.

**CVC-4.4 — Sandbox or test validation of generated artifacts**
- **Statement:** AI-generated formulas, queries, scripts, and configurations MUST be tested or sandbox-validated before operational use.
- **Applicability:** Required for Tier 2 and Tier 3.
- **Primary risks:** Output reliability / hallucination; Improper output handling; Unsafe autonomous actions.
- **References:** OWASP LLM05; OWASP ASI09; OWASP CD-SEC-08; NIST AI RMF Measure 2.

**CVC-4.5 — Provenance labeling for material outputs**
- **Statement:** Provenance labeling MUST be preserved on materially important AI-assisted outputs in a form recognizable to downstream reviewers and auditors.
- **Applicability:** Required for Tier 2 and Tier 3.
- **Primary risks:** Auditability gap; Blind trust.
- **References:** OWASP ASI10; OWASP CD-SEC-01; NIST AI RMF Measure 3; ISO/IEC 42001 Clause 9; EU AI Act Art. 50.

**CVC-4.6 — End-to-end accountability chain for agentic workflows**
- **Statement:** Agentic workflows MUST record an end-to-end accountability chain comprising: prompts issued, retrieved context, model output, tool calls, human approvals, and final action.
- **Applicability:** Required for Tier 3. Recommended for Tier 2.
- **Primary risks:** Auditability gap; Unsafe autonomous actions; Identity confusion / confused-deputy.
- **References:** OWASP ASI08, ASI10; OWASP LLM05, LLM09; NIST AI RMF Measure 2, Measure 3; ISO/IEC 42001 Clause 9.

**CVC-4.7 — Enforcement model selection**
- **Statement:** For Tier 3 outputs, an *enforced* review model MUST be used: a sign-off field in the work management system blocks downstream action until a named reviewer approves. For Tier 2, either *enforced* or *lightweight* review (reviewer name recorded in the document, ticket, or thread) MAY be used. The model applied at each tier MUST be documented.
- **Applicability:** Required for Tier 2 and Tier 3.
- **Primary risks:** Blind trust; Auditability gap.
- **References:** OWASP LLM09; OWASP CD-SEC-01; NIST AI RMF Measure 3; ISO/IEC 42001 Clause 9.

> **Guidance — Enforcement model selection:**
>
> | Option | Mechanism | When appropriate |
> |---|---|---|
> | Lightweight | Reviewer's name recorded in the document, ticket, or email thread containing the output. No system enforcement. | Tier 2 outputs in high-trust teams with limited tooling. Detective, not preventive. |
> | Enforced | A required sign-off field in the work management system (e.g., Jira, ServiceNow) blocks downstream action until a named reviewer approves. | Tier 3 outputs; regulated decisions; any workflow where an unsigned output could reach a customer, regulator, or financial system. |

**CVC-4.8 — Minimum provenance retention**
- **Statement:** `[Plug-in]` Provenance records and review attestations MUST be retained per enterprise audit and compliance policy. `[Standalone]` A minimum provenance retention period MUST be defined; six months is a reasonable default pending formal policy.
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** Auditability gap.
- **References:** ISO/IEC 42001 Clause 9; NIST AI RMF Measure 3; EU AI Act Art. 26(6).

***

### CVC-5. Governance, Audit, and Incident Readiness

**Objective:** Ensure the framework operates within business governance and security operations rather than as a disconnected initiative.

**CVC-5.1 — Written AI use standard**
- **Statement:** A written standard MUST define who may use AI tools, under what conditions, with what data classes, and with what registration and review obligations.
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** Shadow AI; Auditability gap.
- **References:** OWASP CD-SEC-10; NIST AI RMF Govern 1; ISO/IEC 42001 Clause 5; EU AI Act Art. 26(5).

**CVC-5.2 — Assigned cross-functional responsibilities**
- **Statement:** Responsibilities for tool approval, control operation, monitoring, and exception handling MUST be assigned across security, IT, business leadership, data governance, privacy, and risk owners.
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** Auditability gap; Shadow AI.
- **References:** NIST AI RMF Govern 2; ISO/IEC 42001 Clauses 5, 9.

**CVC-5.3 — Logging and administrative auditability**
- **Statement:** Logging and administrative auditability MUST be enabled for approved enterprise AI tools and integrated assistants where technically available. Logs MUST be retained in line with applicable regulatory requirements.
- **Applicability:** Required for Tier 2 and Tier 3. Recommended for Tier 1.
- **Primary risks:** Auditability gap.
- **References:** OWASP ASI08, ASI10; NIST AI RMF Govern 3; ISO/IEC 42001 Clause 9; EU AI Act Art. 26(6).

**CVC-5.4 — AI-specific incident categories**
- **Statement:** The security incident-response process MUST include AI-specific incident categories covering at minimum: prompt-driven data exposure, unsafe autonomous actions, agent goal hijacking, memory or retrieval poisoning, and material business harm from hallucinated output.
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** All threat-model entries (incident triage and reporting layer).
- **References:** OWASP LLM Top 10 (all); OWASP ASI08, ASI10; OWASP CD-SEC-10; NIST AI RMF Manage 4; ISO/IEC 42001 Clauses 9, 10; EU AI Act Art. 26(5).

**CVC-5.5 — Periodic review of use cases, exceptions, and shadow-AI findings**
- **Statement:** Registered use cases, exception decisions, incident trends, and shadow-AI findings MUST be reviewed at least quarterly for high-risk use cases.
- **Applicability:** Required for Tier 2 and Tier 3.
- **Primary risks:** Shadow AI; Auditability gap.
- **References:** OWASP CD-SEC-10; NIST AI RMF Govern 4, Manage 4; ISO/IEC 42001 Clauses 9, 10.

**CVC-5.6 — Reporting chain**
- **Statement:** `[Plug-in]` Metrics and artifacts MUST feed into the enterprise AI governance reporting cadence; a parallel reporting chain MUST NOT be formed. `[Standalone]` A named individual — not a committee — MUST be assigned as single accountable owner of CVC-5 operations until enterprise governance absorbs the function, and metrics MUST be reported to management at least quarterly.
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** Auditability gap.
- **References:** NIST AI RMF Govern 1; ISO/IEC 42001 Clauses 5, 9; EU AI Act Art. 26(5).

**CVC-5.7 — Default posture for non-logging tools**
- **Statement:** Any AI tool that cannot produce or export logs sufficient to reconstruct prompts, retrieved context, tool invocations, and approvals MUST be limited to Tier 1 use only. Tier 2 or Tier 3 use of a non-logging tool MUST require a formal documented exception under [CVC-5.8](#cvc-5-governance-audit-and-incident-readiness).
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** Auditability gap; Shadow AI.
- **References:** OWASP ASI08; NIST AI RMF Measure 3; ISO/IEC 42001 Clause 9; EU AI Act Art. 26(6).

**CVC-5.8 — Exception process requirements**
- **Statement:** Exceptions to CVC-5 controls MUST include all of the following: (1) business justification for use beyond Tier 1; (2) compensating controls (e.g., manual workflow checklists, human confirmation records retained outside the tool, peer attestation); (3) named exception owner; (4) expiration date no greater than 90 days; (5) documented acceptance of residual risk signed by a named business and security approver. Exceptions MUST be reviewed at the next quarterly cycle and MUST be actively renewed to remain valid.
- **Applicability:** Required at the organizational level for all tiers.
- **Primary risks:** Auditability gap; Shadow AI; varies by exception scope.
- **References:** NIST AI RMF Govern 4, Manage 4; ISO/IEC 42001 Clause 10; EU AI Act Art. 26(5).

***

## 8. Minimum Starting Baseline

*`[Standalone]` path — for organizations with no existing AI governance.*

1. Publish a one-page acceptable-use standard for work-related AI, accessible to employees and AI assistants.
2. Establish a lightweight registration process for recurring or material AI use cases.
3. Approve a defined set of enterprise AI tools; prohibit sensitive-data use in unapproved tools with a clearly communicated alternative path.
4. Define three risk tiers and a small set of review triggers tied to data class, autonomy, and external exposure.
5. Require human review and confirmation for all Tier 3 outputs and actions, with confirmation occurring outside the AI assistant's interface.
6. Add AI incident categories to the security incident-response process.
7. Review the use-case inventory, exception register, and incident log quarterly; report metrics to management.

***

## 9. Roles and Decision Rights

| Role | Primary responsibility | Mode |
|---|---|---|
| Business use-case owner | Registers use case; classifies tier; ensures local process compliance; accountable for outcomes. | Both |
| Security / product security | Defines control standards; operates review triggers; publishes detection patterns; defines AI incident categories. | Both |
| IT / enterprise platform | Approves enterprise AI tools; configures access, logging, and integration settings; operates AI gateways. | Both |
| Data governance and privacy | Defines permitted AI data handling; sets review thresholds; establishes retention constraints. | Both |
| Internal audit / compliance | Verifies evidence; reviews control operation; assesses exception management; maps to regulatory obligations. | Both |
| AI governance body | Sets enterprise policy; arbitrates exceptions; receives metrics; revises CVC-5 scope over time. | `[Plug-in]` only |

***

## 10. Quick-Start Policy Language

*These sample control statements are ready for direct use in internal policy documents. Adapt wording to your organization's style.*

### CVC-1 Discovery and Registration

- All recurring work-related use of LLM tools, copilots, assistants, or agents that influence business outputs or actions must be registered with a designated human owner.
- Unapproved AI tools cannot be used to process internal sensitive, confidential, or regulated data.
- The organization must maintain a continuously updated AI-BOM covering models, prompts, retrieval sources, embeddings, agent identities, and connected tools.

### CVC-2 Data Boundary Protection

- High-sensitivity corporate data cannot be submitted to public or consumer AI tools without an approved, time-limited exception.
- AI tools and agents connected to enterprise data must operate under least privilege against approved data sources only.
- Vector stores and retrieval indexes must enforce access controls equivalent to those on the underlying source data.

### CVC-3 Prompt, Agent, and Action Safety

- AI systems processing untrusted external content cannot autonomously execute materially significant actions without explicit human confirmation captured outside the AI system's own interface.
- Each agent operating against business systems must use a non-human identity with scoped credentials.
- Forbidden autonomous-action categories must be defined and enforced: employment status changes, payment approvals, contract execution, access provisioning, regulated communications.

### CVC-4 Output Validation and Human Accountability

- AI-assisted outputs used in materially significant decisions must be reviewed and approved by a named accountable human.
- Quantitative, legal, policy, and operational outputs from AI must be validated against authoritative sources before operational use.
- Provenance must be preserved for materially important AI-assisted outputs in a form recognizable to downstream reviewers and auditors.

### CVC-5 Governance, Audit, and Incident Readiness

- Material AI-related incidents must be reportable through the enterprise incident-response process.
- Logs sufficient to reconstruct prompts, retrieved context, tool invocations, approvals, and resulting actions must be retained per applicable regulatory requirements and for at least six months.
- Registered AI use cases must be reviewed at defined intervals for continued business need, control sufficiency, and exception status.

***

## 11. Metrics and Evidence

**Operational metrics:**

- Registered citizen vibe coder use cases by tier
- Proportion of AI tools in active use that are approved vs. unapproved
- Shadow-AI discoveries per quarter; time-to-registration for newly discovered use
- Proportion of high-risk use cases with named owners and current review evidence
- Count and severity of AI-related incidents, near misses, and policy exceptions
- Proportion of high-risk workflows operating in approved enterprise environments

**Leading indicators:**

- Proportion of registered use cases with documented human-review evidence in the last quarter
- Proportion of approved enterprise AI tools with logging actively retained at the required level

**Evidence artifacts:**

- Use-case inventory and AI-BOM record
- Tool-approval and exception registers
- Prompt and workflow templates for critical use cases
- Review attestations and provenance records for material outputs
- Administrative logs and incident records

Where logging is technically unavailable from a given AI tool, the absence must be recorded as a control gap and factored into the use case's risk tier assignment.

> **`[Plug-in]`** Feed metrics into the existing enterprise AI governance reporting cadence. No separate reporting chain.
>
> **`[Standalone]` — select a reporting model:**
>
> | Option | Format | Recipient | When appropriate |
> |---|---|---|---|
> | Management summary | One-page written summary: use-case count by tier, shadow AI discoveries, incident count, open exceptions | CISO or equivalent; business unit heads | Most organizations; low friction; inheritable by future governance |
> | Risk dashboard | Live or periodic dashboard in existing GRC or BI tooling showing metrics over time | Risk committee or equivalent | Organizations with existing risk tooling and appetite for trend visibility |
> | Embedded in existing security reporting | AI metrics section added to existing quarterly security report | Existing security report audience | Where a separate AI report would create report fatigue or imply AI is disconnected from security |
>
> Regardless of format, the quarterly report must include: use-case inventory changes, exception register status, incident log summary, and shadow-AI discovery count.

***

## Appendix A: Framework Cross-Walk

| CVC-5 domain | OWASP LLM Top 10 (2025) | OWASP Agentic Top 10 (2026) | OWASP Citizen Dev Top 10 | NIST AI RMF / 600-1 | ISO/IEC 42001:2023 | EU AI Act |
|---|---|---|---|---|---|---|
| CVC-1 Discovery and Registration | LLM03 | ASI04 | CD-SEC-09 | Map 1, Map 2 | Clause 4; Annex A inventory | Article 11 |
| CVC-2 Data Boundary Protection | LLM02, LLM08 | ASI06 | CD-SEC-04, CD-SEC-05 | Manage 2; Measure 2 | Clause 8 | Article 26(4) |
| CVC-3 Prompt, Agent, and Action Safety | LLM01, LLM05, LLM06, LLM10 | ASI01, ASI02, ASI03, ASI05, ASI07 | CD-SEC-02, CD-SEC-03, CD-SEC-07, CD-SEC-08 | Manage 1, Manage 4 | Clause 8 | Article 26(2) |
| CVC-4 Output Validation and Human Accountability | LLM05, LLM09 | ASI09, ASI10 | CD-SEC-01, CD-SEC-08 | Measure 2, Measure 3 | Clause 9 | Article 26(2); Article 50 |
| CVC-5 Governance, Audit, and Incident Readiness | All | ASI08, ASI10 | CD-SEC-10 | Govern 1–4; Manage 4 | Clauses 5, 9, 10 | Article 26(5); Article 26(6) |

***

## Appendix B: Definitions

| Term | Definition |
|---|---|
| Citizen Vibe Coder | A non-engineer whose use of LLMs, copilots, assistants, or agents materially shapes business outputs, decisions, or operational actions. |
| Material work | Work output that influences business outcomes to a degree warranting management attention if an error or harm occurs. |
| Least agency | Granting an agent the minimum autonomy, tools, and action scope required for its function; broader autonomy is earned, not default. |
| Shadow AI | AI tools, assistants, agents, or workflows not registered, approved, or visible to security and governance functions. |
| AI-BOM | Structured inventory of AI components in a system or workflow (models, prompts, datasets, embeddings, vector stores, agents, tools). Standard formats: SPDX 3.0, CycloneDX. |
| Indirect prompt injection | Malicious instructions embedded in content an AI system retrieves or processes (documents, emails, web pages) rather than supplied by the user. |
| Prompt firewall / AI gateway | Policy-enforcing component between AI users/applications and model providers; inspects prompts and responses, applies DLP, detects injection, enforces limits, and produces audit logs. |
| MCP | Model Context Protocol — open protocol for connecting AI assistants to external tools, data sources, and services. |

***

## Appendix C: Self-Assessment Checklist

*This appendix is non-normative. It is a self-assessment aid derived directly from [Section 7](#7-cvc-5-control-catalog-normative). For each control, the table shows whether it is Required (`R`) or Recommended (`Rec`) at each tier. Blank cells indicate the control does not apply at that tier. Record current status and supporting evidence in the Notes column when using this table as a working assessment artifact.*

| Control ID | Control name | Tier 1 | Tier 2 | Tier 3 | Notes |
|---|---|---|---|---|---|
| CVC-1.1 | AI tool classification register | R | R | R | Organization-level. |
| CVC-1.2 | Use-case registration and ownership | Rec | R | R | Tier 1 registration becomes required once organization-defined volume thresholds are crossed. |
| CVC-1.3 | Use-case metadata schema | Rec | R | R | Tier 1 applies where registration applies. |
| CVC-1.4 | Active discovery mechanisms | R | R | R | Organization-level; no single mechanism is sufficient. |
| CVC-1.5 | AI-BOM expression |  | Rec | R | Tier 3 required where the underlying tools support it. |
| CVC-1.6 | Inventory authority | R | R | R | `[Plug-in]` feeds enterprise register; `[Standalone]` is authoritative. |
| CVC-2.1 | AI-extended data classification | R | R | R | Organization-level. |
| CVC-2.2 | Prohibition of high-sensitivity data in public AI tools | Rec | R | R | Exceptions only via CVC-5.8. |
| CVC-2.3 | Approved enterprise environment for sensitive use |  | R | R |  |
| CVC-2.4 | Least-privilege connectors and short-lived credentials | Rec | R | R |  |
| CVC-2.5 | Detective controls for leakage patterns |  | Rec | R | Absence is a recorded control gap. |
| CVC-2.6 | Access controls on retrieval indexes and vector stores |  | R | R |  |
| CVC-2.7 | Category-based prohibition with governed allowlist | R | R | R | Allowlist owner and review cadence must be named. |
| CVC-2.8 | Minimum data-classification scheme | R | R | R | `[Standalone]` mode only; prerequisite to CVC-2.1–CVC-2.6. |
| CVC-3.1 | Treat external content as untrusted | R | R | R | Organization-level. |
| CVC-3.2 | Instruction/content separation in business-critical workflows |  | Rec | R |  |
| CVC-3.3 | Default read-only access for AI tools and agents |  | R | R |  |
| CVC-3.4 | Out-of-band human confirmation for material actions |  | Rec | R |  |
| CVC-3.5 | Forbidden autonomous-action categories | R | R | R | Enforced for Tier 2 and Tier 3 use cases. |
| CVC-3.6 | Per-agent non-human identity with scoped credentials |  | R | R | User-impersonation patterns MUST NOT be used. |
| CVC-3.7 | Least agency for capability expansion |  | R | R |  |
| CVC-3.8 | AI-gateway or compensating controls |  | Rec | R | `[Plug-in]` uses gateway; `[Standalone]` uses compensating controls. |
| CVC-3.9 | Forbidden-action list ownership and change control | R | R | R | Single named owner adds; two-person review removes. |
| CVC-4.1 | Output classification tiers | R | R | R | Classification must be visible to downstream consumers. |
| CVC-4.2 | Named accountable reviewer | Rec | R | R |  |
| CVC-4.3 | Source validation for material claims |  | Rec | R |  |
| CVC-4.4 | Sandbox or test validation of generated artifacts |  | R | R |  |
| CVC-4.5 | Provenance labeling for material outputs |  | R | R |  |
| CVC-4.6 | End-to-end accountability chain for agentic workflows |  | Rec | R |  |
| CVC-4.7 | Enforcement model selection |  | R | R | Enforced model required for Tier 3; lightweight permitted for Tier 2. |
| CVC-4.8 | Minimum provenance retention | R | R | R | `[Standalone]` default 6 months pending formal policy. |
| CVC-5.1 | Written AI use standard | R | R | R | Organization-level. |
| CVC-5.2 | Assigned cross-functional responsibilities | R | R | R | Organization-level. |
| CVC-5.3 | Logging and administrative auditability | Rec | R | R |  |
| CVC-5.4 | AI-specific incident categories | R | R | R | Organization-level. |
| CVC-5.5 | Periodic review of use cases and exceptions |  | R | R | At least quarterly. |
| CVC-5.6 | Reporting chain | R | R | R | `[Plug-in]` feeds enterprise; `[Standalone]` names a single accountable owner. |
| CVC-5.7 | Default posture for non-logging tools | R | R | R | Non-logging tools auto-limited to Tier 1. |
| CVC-5.8 | Exception process requirements | R | R | R | Max 90-day expiration; renewal required. |

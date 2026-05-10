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

> **Note:** Taxonomy reference codes (OWASP LLM Top 10, Agentic Top 10, Citizen Dev Top 10) are retained in [Appendix A: Framework Cross-Walk](#appendix-a-framework-cross-walk) for specialist cross-reference.

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

> **Organization-defined threshold.** The Tier 1 registration threshold must be set by each organization and re-evaluated at least annually. Determine your threshold by answering two questions:
>
> 1. At what frequency or business impact does unregistered use create unacceptable visibility gaps? (e.g., any recurring use, any use producing outputs shared beyond the originating team)
> 2. Is tier classification based on the user's intent at the time of use, or on how the output is ultimately used downstream? Downstream use is the more defensible standard — classify by the most sensitive use the output could reasonably reach.
>
> Document your threshold decision, the date it was set, and the next scheduled review date.

| Tier | Typical characteristics | Minimum control expectation |
|---|---|---|
| Tier 1: Low | Public or low-sensitivity data; draft assistance only; no system action; no external sharing. | Acceptable-use rules apply; registration optional below a defined volume threshold. |
| Tier 2: Moderate | Internal data; recurring use; business analysis or decision support; outputs influence operations but do not directly trigger action. | Registration required; approved tools only; output review required for material use. |
| Tier 3: High | Sensitive or regulated data; external communication; tool-calling or record changes; HR, legal, financial, or compliance impact; agentic execution of business-meaningful actions. | Registration with named owner; approved enterprise environment; explicit confirmation gates for action; logging, review, and provenance mandatory. |

***

## 7. The CVC-5 Control Model

Controls are tagged `[Plug-in]` where behavior differs when enterprise AI governance exists, and `[Standalone]` where the control must be self-contained.

***

### CVC-1. Discovery and Registration

**Objective:** Convert unknown AI use into known AI use.

**Required controls:**

- Maintain an AI tool classification register with statuses: *approved for sensitive work*, *approved for limited use*, *prohibited for corporate data*.
- Register all recurring or material business use of LLMs, copilots, assistants, agents, custom GPTs, and MCP-connected workflows with a designated human owner.
- Each registered use case must record: owning team, business purpose, data classes involved, connected tools/data sources, output type, whether automated actions occur, and human review level applied.
- Discovery mechanisms must combine self-attestation, network/identity telemetry, periodic business-unit reviews, and reconciliation against the sanctioned-tool register.
- Where automated discovery is feasible, express the resulting record as an AI-BOM (SPDX 3.0 or CycloneDX), capturing models, datasets, prompts, system prompts, embeddings, vector stores, MCP servers, and tool integrations.

`[Plug-in]` Feed the use-case inventory and AI-BOM into the enterprise AI governance register. Do not maintain a parallel inventory.

`[Standalone]` The use-case inventory is the authoritative organizational record until enterprise governance is established. Assign a named maintainer.

***

### CVC-2. Data Boundary Protection

**Objective:** Prevent inappropriate disclosure of sensitive data into AI systems; constrain what AI systems can retrieve, expose, or carry across boundaries.

**Required controls:**

- Extend enterprise data classification to AI usage with explicit rules for prompts, file uploads, retrieval content, embedded indexes, copied context, and downstream responses.
- Prohibit submission of high-sensitivity data to public or consumer AI tools without a documented exception.
- Require approved enterprise AI environments for any use of internal sensitive, regulated, or business-confidential data.
- Enforce least privilege on connectors, plugins, and tools accessible to AI assistants; use short-lived credentials where supported.
- Deploy preventive or detective controls for obvious leakage patterns (secrets, PCI data, PHI) where technically feasible.
- Enforce access controls on vector stores and retrieval indexes equivalent to those on the underlying source data.

`[Standalone]` If no enterprise data classification scheme exists, establish a minimum three-tier classification (public / internal / restricted) as a prerequisite to this control.

> **Prohibition model: category-based with an accompanying allowlist.** Prohibit by category (e.g., "public consumer AI tools," "personal AI accounts not provisioned by IT") rather than by named product. Maintain a separately governed allowlist of approved tools. This separates the stable policy (the prohibition) from the frequently updated operational list (the allowlist), reducing policy churn as the market evolves. The allowlist owner and review cadence must be explicitly assigned.

***

### CVC-3. Prompt, Agent, and Action Safety

**Objective:** Prevent AI systems from following malicious instructions, exceeding authority, or performing unsafe actions.

**Required controls:**

- Treat external content processed by AI systems (emails, attachments, web pages, documents, transcripts, meeting recordings) as untrusted.
- Business-critical workflows must use prompt/system-instruction patterns that separate untrusted content from operating instructions and refuse to follow embedded directives without user confirmation.
- AI-connected tools and agents must default to read-only access.
- Require explicit human confirmation — captured outside the AI chat surface — for any action that sends data externally, modifies records, changes entitlements, transfers funds, or produces material outcomes.
- Define and enforce forbidden autonomous-action categories: employment status changes, payment approvals, contract execution, access provisioning, regulated communications.
- Each agent must operate under its own non-human identity with scoped credentials and short-lived tokens.
- Apply least agency to all decisions granting new tools, broader scopes, or auto-approval permissions.

`[Plug-in]` Where AI governance / AI-gateway capabilities are available, apply prompt-injection detection, output policy enforcement, rate and budget limits, and egress allowlisting to business-critical workflows.

`[Standalone]` In the absence of an AI gateway, apply compensating controls: manual workflow checklists for Tier 3 actions, peer confirmation for high-risk outputs, and documented review records.

> **Organization-defined list ownership.** Each organization must assign an owner for the forbidden autonomous-action categories list and define a change-control process. For fast-moving environments where new agent capabilities emerge frequently, the recommended model is: a single named owner (e.g., Head of Security or CISO delegate) with unilateral authority to add categories immediately, and a lightweight two-person review (Security + Legal or Compliance) required to remove a category. Additions default to active; removals require justification. Review the full list at minimum quarterly.

***

### CVC-4. Output Validation and Human Accountability

**Objective:** Prevent plausible but incorrect AI output from becoming an authoritative business artifact or decision.

**Required controls:**

- Classify AI outputs into at least three tiers: *reference-only*, *business input*, *action-enabling*.
- Assign a named accountable reviewer for any output that influences decisions, records, controls, legal statements, or customer-facing commitments.
- Require source validation for quantitative claims, legal interpretations, policy language, regulatory references, and operational procedures used beyond the draft stage.
- Test or sandbox-validate AI-generated formulas, queries, scripts, and configurations before operational use.
- Preserve provenance labeling on materially important AI-assisted outputs.
- For agentic workflows, record the accountability chain end-to-end: prompts issued, retrieved context, model output, tool calls, human approvals, and final action.

`[Plug-in]` Provenance records and review attestations feed into enterprise audit and compliance workflows. Align retention periods to enterprise policy.

`[Standalone]` Define a minimum retention period for provenance records now, even informally. Six months is a reasonable default pending formal policy.

> **Enforcement model — select based on tier and organizational risk posture:**
>
> | Option | Mechanism | When appropriate |
> |---|---|---|
> | Lightweight | Reviewer's name recorded in the document, ticket, or email thread containing the output. No system enforcement. | Tier 1–2 outputs; high-trust teams; limited tooling. Accept that this is detective, not preventive. |
> | Enforced | A required sign-off field in the work management system (e.g., Jira, ServiceNow) blocks downstream action until a named reviewer approves. | Tier 3 outputs; regulated decisions; any workflow where an unsigned output could reach a customer, regulator, or financial system. |
>
> Both are defensible. Enforced is required for Tier 3. Lightweight is acceptable for Tier 2 provided audit trails are retained. Document which model applies at which tier.

***

### CVC-5. Governance, Audit, and Incident Readiness

**Objective:** Ensure the framework operates within business governance and security operations rather than as a disconnected initiative.

**Required controls:**

- Maintain a written standard defining who may use AI tools, under what conditions, with what data classes, and with what registration and review obligations.
- Assign responsibilities across security, IT, business leadership, data governance, privacy, and risk owners for tool approval, control operation, monitoring, and exception handling.
- Require logging and administrative auditability for approved enterprise AI tools and integrated assistants where technically available; retain in line with applicable regulatory requirements.
- Add AI-specific incident categories to the security incident-response process: prompt-driven data exposure, unsafe autonomous actions, agent goal hijacking, memory/retrieval poisoning, material business harm from hallucinated output.
- Review registered use cases, exception decisions, incident trends, and shadow-AI findings at minimum quarterly for high-risk use cases.

`[Plug-in]` Feed artifacts upward into enterprise AI governance. Do not form a parallel reporting chain.

`[Standalone]` Assign a named individual — not a committee — as the single accountable owner of CVC-5 operations until enterprise governance absorbs this function. Report metrics to management on the same quarterly cycle.

> **Default posture: auto-demote to Tier 1.** Any AI tool that cannot produce or export logs sufficient to reconstruct prompts, retrieved context, tool invocations, and approvals is automatically limited to Tier 1 use only. Tier 2 or Tier 3 use of a non-logging tool requires a formal documented exception.
>
> **Exception process:** Exceptions must include: (1) business justification for use beyond Tier 1, (2) compensating controls (e.g., manual workflow checklists, human confirmation records retained outside the tool, peer attestation), (3) named exception owner, (4) expiration date no greater than 90 days, and (5) documented acceptance of residual risk signed by a named business and security approver. Exceptions are reviewed at the next quarterly cycle and must be actively renewed to remain valid.

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

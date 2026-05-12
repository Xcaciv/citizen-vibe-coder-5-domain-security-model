# The Plain‑Language Guide to CVC-5: Citizen Vibe Coder Security Framework

**Type:** Security control standard companion
**Status:** Draft v0.9.1
**Date:** May 7, 2026
**Companion document:** [cvc-5-security-model.md](cvc-5-security-model.md) (normative)

---

## Why This Framework Exists

A challenge in mid-to-large organizations is that business work is increasingly shaped by AI tools wielded by non-engineers. A finance manager asks an LLM to reconcile a vendor balance and pastes the answer into a board pack. An HR partner sets up an agent that drafts and sends termination communications. A compliance analyst uses a retrieval-augmented assistant to summarize regulatory obligations, then attaches the summary to an audit response. None of these people are developers. None of their workflows pass through the SDLC controls that the security function has spent a decade refining. None of these people are developers, yet each shapes a business outcome.

Some teams recognize this shift but misunderstand its scope. They reach for prohibition lists or extended secure-coding standards, but both are insufficient. The first drives use into shadow channels without reducing risk. The second mistakes the form (prompts, code, output) for the substance (a human making a business decision through a probabilistic intermediary). What's needed is a control system focused on the user who treats AI as an extension of their work, not the engineer who treats AI as an input to a product.

CVC-5 is that control system. It defines five domains of control over business-led AI use, organized around outcomes rather than implementation form. It operates as a standalone baseline where no enterprise AI governance exists, and as a domain-specific control profile where one does. The normative statements, RFC 2119 keywords, applicability matrices, and full control catalog live in the companion [security model document](cvc-5-security-model.md). This narrative version is intended for people who need to internalize the framework before they apply it.

---

## How to Read This Document

There are two reading paths, and the right one depends on what already exists in the organization.

### Path A — An enterprise AI governance program is in place

In this case, CVC-5 plugs into that program as a domain-specific control profile covering business-led AI use. The most useful starting point is the [governance positioning section of the normative model](cvc-5-security-model.md#4-governance-positioning), followed by the [control catalog](cvc-5-security-model.md#7-cvc-5-control-catalog-normative). The `[Standalone]` tags can be ignored; the `[Plug-in]` behaviors are what apply.

### Path B — No formal AI governance exists yet

Here, CVC-5 serves as the first formal structure. Begin with the minimum starting baseline described later in this document, then return to the [control catalog](cvc-5-security-model.md#7-cvc-5-control-catalog-normative). Pay attention to the `[Standalone]` tags — they describe what CVC-5 must do for itself in the absence of broader structures. There should also be an explicit commitment to refactor CVC-5 into a plug-in profile once enterprise governance is established. This is important: CVC-5 is meant to be a useful starting point, not a permanent island.

Four terms recur throughout. A **Citizen Vibe Coder** is a non-engineer whose use of LLMs, copilots, assistants, or agents materially shapes business outputs, decisions, or operational actions. **Material work** is work output that influences business outcomes to a degree warranting management attention if an error or harm occurs. **Shadow AI** refers to tools, assistants, agents, or workflows not registered, approved, or visible to security and governance functions. **Least agency** is the agentic analog of least privilege: granting an agent only the minimum autonomy, tools, and action scope required for its function. Full definitions are in [Appendix B of the normative model](cvc-5-security-model.md#appendix-b-definitions).

---

## What Falls Inside the Framework

The boundary of CVC-5 is drawn around *who is doing the work* and *what the work shapes*, not around the technology being used. Drafting analyses, recommendations, summaries, decisions, or policies via AI is in scope when those outputs influence business outcomes. Operating embedded AI assistants inside enterprise SaaS is in scope when those assistants generate outputs or initiate actions.
 Moving AI-produced content into tickets, emails, reports, spreadsheets, forms, or procedures is in scope. So is running LLM-driven workflows that retrieve documents, call tools or APIs, or produce downstream effects, and so is building or invoking custom agents, GPTs, retrieval pipelines, or MCP integrations under business-unit ownership.

Notably, code generation is not required for a workflow to be in scope. A finance analyst who never writes a line of Python but produces forecasts through a retrieval-augmented assistant is doing citizen vibe coding in the sense that matters here. If their output shapes a material decision, the controls apply.

What is not in scope is the professional software development lifecycle and its engineering security controls, low-code and no-code platform administration, model development and MLOps, and the enterprise AI strategy, ethics, vendor management, and contract review functions that other parts of the organization own.
 These are adjacent disciplines and should remain so. CVC-5 is deliberately narrow.

---

## Design Principles

The framework is built on six principles, each of which is reflected in specific control choices later.

### Standalone yet composable

CVC-5 must function as a complete minimum viable control system when nothing else exists, while every individual control maps cleanly onto existing enterprise capabilities when they do.

### Technology and vendor neutral

The framework applies regardless of AI product, vendor, deployment model, or interaction modality. A control that hinges on "what OpenAI does" or "what Microsoft does" will not survive a market this volatile.

### Outcome focus

Controls target the risk-creating outcome, not the implementation form. Whether the AI produces prose, a spreadsheet formula, or a tool call, the question is whether that output materially influences a business outcome.

### Explicit human accountability

A human remains accountable for inputs, configurations, outputs, and resulting actions. AI assistance does not transfer ownership. This principle is the foundation of CVC-4.

### Secure Enablement

Approved patterns must be easier to use than shadow patterns. A prohibition is only defensible when it's specific, narrow, and accompanied by a sanctioned alternative. Prohibitions without alternatives create shadow AI; they don't prevent it.

### Risk Proportionality

Control strength scales with business impact through the risk tiering model. Treating every prompt as Tier 3 creates friction without security gain; treating every Tier 3 use as Tier 1 produces the opposite problem.

---

## Governance Positioning

CVC-5 is designed to operate in two modes, and the difference between them is significant enough to address directly. The full positioning logic is in [Section 4 of the normative model](cvc-5-security-model.md#4-governance-positioning).

When enterprise AI governance exists, CVC-5 is a domain-specific control profile underneath it. The framework translates enterprise policy into operational controls for business-led AI use; it doesn't create a parallel reporting chain. Where existing governance is stricter, existing requirements prevail. Where existing governance is silent on AI prompts, agents, or business-side workflows, CVC-5 fills the gap. Exceptions and escalations flow through existing governance bodies. Metrics feed upward. Integration points across AI policy, data governance, identity, vendor risk, security operations, and audit are detailed in the normative model.

When no enterprise governance exists, CVC-5 is the initial structure. Three commitments matter here. First, it should be presented as a security and operational control standard, not as AI strategy or enterprise policy. Second, decisions should be documented in a form inheritable by future governance bodies. Third, the framework should be reviewed annually and refactored into a plug-in profile once enterprise governance is established.

For compliance officers and audit functions, CVC-5 contributes to the NIST AI RMF 1.0 Map, Measure, and Manage functions; maps to ISO/IEC 42001:2023 Clause 4 and Annex A; and supports EU AI Act Article 26 deployer compliance evidence. The full cross-walk is in [Appendix A of the normative model](cvc-5-security-model.md#appendix-a-framework-cross-walk).

---

## Threat Model

The threats CVC-5 addresses fall into a recognizable cluster. Specialist taxonomy codes — OWASP LLM Top 10, Agentic Top 10, Citizen Dev Top 10 — are retained in the [framework cross-walk](cvc-5-security-model.md#appendix-a-framework-cross-walk) for those who need them.

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

Three assumptions drive how the framework engages these risks. First, prompt injection cannot be reliably prevented at the model layer; CVC-5 treats it as a containment problem, not a prevention problem, which is why the strongest controls in [CVC-3](cvc-5-security-model.md#cvc-3-prompt-agent-and-action-safety) target action gating rather than input sanitization. Second, business users have legitimate role-appropriate system access; AI tools don't change the access-control model but they do change what is retrievable in practice. Third, visibility into AI activity is incomplete by default, and the controls must function under partial visibility. A framework that depends on perfect telemetry will fail the moment a new tool reaches general availability.

---

## Risk Tiering

CVC-5 applies three risk tiers, and every control in the catalog names the tiers for which it is required and the tiers for which it is recommended. The full tier model lives in [Section 6 of the normative model](cvc-5-security-model.md#6-risk-tiering-model).

The most important decision in implementing CVC-5 is how to classify use cases into tiers. There are two adjacent questions an organization must answer, and the answers should be documented with their decision date and a review date no more than a year out. The first question is: at what frequency or business impact does unregistered use create unacceptable visibility gaps? The second is: should tier classification be based on the user's intent at time of use, or on how the output is ultimately used downstream? Downstream use is the more defensible standard. Classify by the most sensitive use the output could reasonably reach. A draft framed as "personal thinking only" that ends up pasted into a board memo was never really Tier 1.

| Tier | Typical characteristics | Minimum control expectation |
|---|---|---|
| Tier 1: Low | Public or low-sensitivity data; draft assistance only; no system action; no external sharing. | Acceptable-use rules apply; registration optional below a defined volume threshold. |
| Tier 2: Moderate | Internal data; recurring use; business analysis or decision support; outputs influence operations but do not directly trigger action. | Registration required; approved tools only; output review required for material use. |
| Tier 3: High | Sensitive or regulated data; external communication; tool-calling or record changes; HR, legal, financial, or compliance impact; agentic execution of business-meaningful actions. | Registration with named owner; approved enterprise environment; explicit confirmation gates for action; logging, review, and provenance mandatory. |

---

## The Five Control Domains

A narrative walk through each of the five domains follows. Specific normative statements, applicability by tier, and primary-risk mappings live in the [control catalog](cvc-5-security-model.md#7-cvc-5-control-catalog-normative). A practical self-assessment checklist that captures Required and Recommended status per tier is in [Appendix C of the normative model](cvc-5-security-model.md#appendix-c-self-assessment-checklist).

### CVC-1: Discovery and Registration

The objective of this domain is to convert unknown AI use into known AI use. Everything else in the framework hinges on it.

#### Approach

The first step is to maintain an AI tool classification register with at least three statuses: approved for sensitive work, approved for limited use, and prohibited for corporate data. This register is the organization's authoritative answer to whether a given tool may be used and for what purpose. It's operationalized by [CVC-1.1](cvc-5-security-model.md#cvc-1-discovery-and-registration) and required for every tier.

Recurring or material business use of LLMs, copilots, assistants, agents, custom GPTs, and MCP-connected workflows must be registered with a designated human owner, as outlined in [CVC-1.2](cvc-5-security-model.md#cvc-1-discovery-and-registration). Each registered use case carries a defined metadata schema covering owning team, business purpose, data classes involved, connected tools and data sources, output type, whether automated actions occur, and the level of human review applied, as described in [CVC-1.3](cvc-5-security-model.md#cvc-1-discovery-and-registration). This is [CVC-1.3](cvc-5-security-model.md#cvc-1-discovery-and-registration), and the discipline of populating it well is what separates a real inventory from a spreadsheet that decays in six months.

Discovery itself cannot rely on a single mechanism. [CVC-1.4](cvc-5-security-model.md#cvc-1-discovery-and-registration) requires combining self-attestation, network and identity telemetry, periodic business-unit reviews, and reconciliation against the sanctioned-tool register. Where automated discovery is feasible, the resulting record should be expressed as an AI-BOM in SPDX 3.0 or CycloneDX format, capturing models, datasets, prompts, system prompts, embeddings, vector stores, MCP servers, and tool integrations, as outlined in [CVC-1.5](cvc-5-security-model.md#cvc-1-discovery-and-registration), required for Tier 3 where supported.

#### Where the modes diverge

Under `[Plug-in]`, the use-case inventory and AI-BOM feed into the enterprise AI governance register; a parallel inventory must not be maintained. Under `[Standalone]`, the inventory itself is the authoritative organizational record until enterprise governance is established, with a named maintainer. The full statement is in [CVC-1.6](cvc-5-security-model.md#cvc-1-discovery-and-registration).

### CVC-2: Data Boundary Protection

The objective here is to prevent the inappropriate disclosure of sensitive data into AI systems and to constrain what AI systems can retrieve, expose, or carry across boundaries. This is the domain most likely to be misunderstood as "the same DLP problem we already have," and it is not.

#### Approach

Existing data classification must be extended to AI usage with explicit rules for prompts, file uploads, retrieval content, embedded indexes, copied context, and downstream responses, as outlined in [CVC-2.1](cvc-5-security-model.md#cvc-2-data-boundary-protection). This is [CVC-2.1](cvc-5-security-model.md#cvc-2-data-boundary-protection). The reason classification cannot simply be carried forward unchanged is that AI tools alter the practical retrievability of data.
 A user who has legitimate access to a SharePoint site under access-control models that have not changed can, through a retrieval-augmented assistant, surface and synthesize content from that site at a scale and speed that no individual reading session would have produced. The access decision is identical. The exposure profile is not.

Use of internal sensitive, regulated, or business-confidential data must occur within an approved enterprise AI environment, per [CVC-2.3](cvc-5-security-model.md#cvc-2-data-boundary-protection). Connectors, plugins, and tools accessible to AI assistants must operate under least privilege with short-lived credentials where supported, as outlined in [CVC-2.4](cvc-5-security-model.md#cvc-2-data-boundary-protection). Use of internal sensitive, regulated, or business-confidential data must occur within an approved enterprise AI environment, per [CVC-2.3](cvc-5-security-model.md#cvc-2-data-boundary-protection). Vector stores and retrieval indexes must enforce access controls equivalent to those on the underlying source data, which is [CVC-2.6](cvc-5-security-model.md#cvc-2-data-boundary-protection) and is the single control most often missing from RAG deployments observed in practice.

#### A note on prohibition structure

Prohibitions should be expressed by *category* (for example, "public consumer AI tools" or "personal AI accounts not provisioned by IT") rather than by named product. A separately governed allowlist of approved tools should exist alongside the category prohibition, with an explicitly assigned owner and a documented review cadence, as stated in [CVC-2.7](cvc-5-security-model.md#cvc-2-data-boundary-protection).
 This is [CVC-2.7](cvc-5-security-model.md#cvc-2-data-boundary-protection), and the rationale matters: the category-level prohibition is a stable policy artifact that changes infrequently, while the allowlist is an operational artifact that turns over as the market evolves. Separating them keeps policy churn low and shortens the path to approving new tools without rewriting prohibitions every quarter.

#### Where the modes diverge

Under `[Standalone]`, if no enterprise data classification scheme exists, a minimum three-tier classification (public / internal / restricted) must be established as a prerequisite to applying CVC-2.1 through CVC-2.6, as outlined in [CVC-2.8](cvc-5-security-model.md#cvc-2-data-boundary-protection).

### CVC-3: Prompt, Agent, and Action Safety

This domain consumes the most attention when the framework is first introduced, and rightly so. Its objective is to prevent AI systems from following malicious instructions, exceeding their authority, or performing unsafe actions.

#### Approach

The foundational stance is that external content processed by AI systems — emails, attachments, web pages, documents, transcripts, meeting recordings — must be treated as untrusted input, as stated in [CVC-3.1](cvc-5-security-model.md#cvc-3-prompt-agent-and-action-safety). Following from that, business-critical workflows must use prompt and system-instruction patterns that separate untrusted content from operating instructions and refuse to follow embedded directives without explicit user confirmation, as outlined in [CVC-3.2](cvc-5-security-model.md#cvc-3-prompt-agent-and-action-safety).

A more substantive defense comes from posture: AI-connected tools and agents must default to read-only access, as stated in [CVC-3.3](cvc-5-security-model.md#cvc-3-prompt-agent-and-action-safety). Write, modify, or send capabilities should be granted only through a documented decision under the least-agency standard. Any action that sends data externally, modifies records, changes entitlements, transfers funds, or produces material outcomes must require explicit human confirmation captured outside the AI chat surface, as outlined in [CVC-3.4](cvc-5-security-model.md#cvc-3-prompt-agent-and-action-safety).
 The AI chat surface — this out-of-band requirement, [CVC-3.4](cvc-5-security-model.md#cvc-3-prompt-agent-and-action-safety), is what makes prompt injection a containment problem rather than an open vulnerability. If the confirmation lives inside the same chat surface as the attack, the attack can produce the confirmation.

A specific list of forbidden autonomous-action categories must be defined and enforced. At minimum, these include employment status changes, payment approvals, contract execution, access provisioning, and regulated communications. Each agent operates under its own non-human identity with scoped credentials and short-lived tokens; user-impersonation patterns for agent execution are forbidden, per [CVC-3.6](cvc-5-security-model.md#cvc-3-prompt-agent-and-action-safety). Decisions to grant agents new tools, broader scopes, or auto-approval permissions must apply the least-agency standard, justified, documented, and reviewable, as required by [CVC-3.7](cvc-5-security-model.md#cvc-3-prompt-agent-and-action-safety).

#### Where modes diverge

Under `[Plug-in]`, where AI-gateway capabilities are available, prompt-injection detection, output policy enforcement, rate and budget limits, and egress allowlisting must be applied to business-critical workflows. Under `[Standalone]`, compensating controls take over: manual workflow checklists for Tier 3 actions, peer confirmation for high-risk outputs, and documented review records. This is [CVC-3.8](cvc-5-security-model.md#cvc-3-prompt-agent-and-action-safety).

#### A note on list governance

[CVC-3.9](cvc-5-security-model.md#cvc-3-prompt-agent-and-action-safety) requires a single named owner with unilateral authority to add categories, while removal requires a documented two-person review (Security plus Legal or Compliance). The asymmetry is intentional. In environments where new agent capabilities emerge faster than committees can convene, requiring symmetric approval for both additions and removals creates a bottleneck on protective additions, which is exactly the wrong direction. One-person add, two-person remove keeps the prohibition list current without sacrificing reversibility.

### CVC-4: Output Validation and Human Accountability

This domain prevents plausible but incorrect AI output from becoming an authoritative business artifact or decision. It enforces the explicit-human-accountability principle.

#### Approach

AI outputs should be classified into at least three tiers — *reference-only*, *business input*, and *action-enabling* — and the classification must be visible to downstream consumers of the output ([CVC-4.1](cvc-5-security-model.md#cvc-4-output-validation-and-human-accountability)). Any AI-assisted output influencing decisions, records, controls, legal statements, or customer-facing commitments must have a named accountable reviewer recorded ([CVC-4.2](cvc-5-security-model.md#cvc-4-output-validation-and-human-accountability)).
Source validation is required for quantitative claims, legal interpretations, policy language, regulatory references, and operational procedures used beyond the draft stage — [CVC-4.3](cvc-5-security-model.md#cvc-4-output-validation-and-human-accountability). Generated formulas, queries, scripts, and configurations must be sandbox- or test-validated before operational use ([CVC-4.4](cvc-5-security-model.md#cvc-4-output-validation-and-human-accountability)).

Provenance labeling for materially important AI-assisted outputs is required by [CVC-4.5](cvc-5-security-model.md#cvc-4-output-validation-and-human-accountability), and for agentic workflows, [CVC-4.6](cvc-5-security-model.md#cvc-4-output-validation-and-human-accountability) requires recording the end-to-end accountability chain: prompts issued, retrieved context, model output, tool calls, human approvals, and final action. This is the artifact auditors will ask for when something goes wrong, and it is much cheaper to build into the workflow at design time than to reconstruct after the fact.

#### On enforcement

[CVC-4.7](cvc-5-security-model.md#cvc-4-output-validation-and-human-accountability) requires an enforcement model decision. A lightweight model is acceptable for Tier 2 outputs in high-trust teams, provided audit trails are retained. It is detective, not preventive, and should be understood as such. An enforced model — a required sign-off field in the work management system (Jira, ServiceNow, equivalent) that blocks downstream action until a named reviewer approves — is required for Tier 3. Any workflow where an unsigned output could reach a customer, regulator, or financial system needs the enforced model.

#### Where modes diverge

Under `[Plug-in]`, provenance records and review attestations feed into enterprise audit and compliance workflows with aligned retention periods. Under `[Standalone]`, a minimum retention period must be defined now, even informally; six months is a reasonable default pending formal policy. [CVC-3.8](cvc-5-security-model.md#cvc-3-prompt-agent-and-action-safety).

### CVC-5: Governance, Audit, and Incident Readiness

This domain ensures the framework operates within business governance and security operations.
 It is the domain that prevents CVC-5 from becoming the kind of standalone document that gets cited at audits and ignored everywhere else.

#### Approach

A written standard must define who may use AI tools, under what conditions, with what data classes, and with what registration and review obligations — [CVC-5.1](cvc-5-security-model.md#cvc-5-governance-audit-and-incident-readiness). Cross-functional responsibilities must be assigned across security, IT, business leadership, data governance, privacy, and risk owners, per [CVC-5.2](cvc-5-security-model.md#cvc-5-governance-audit-and-incident-readiness). Logging and administrative auditability must be in place for approved enterprise AI tools and integrated assistants where technically available, with retention aligned to regulatory requirements ([CVC-5.3](cvc-5-security-model.md#cvc-5-governance-audit-and-incident-readiness)).

AI-specific incident categories must be added to the security incident-response process — [CVC-5.4](cvc-5-security-model.md#cvc-5-governance-audit-and-incident-readiness) names at minimum: prompt-driven data exposure, unsafe autonomous actions, agent goal hijacking, memory or retrieval poisoning, and material business harm from hallucinated output. Cross-functional responsibilities must be assigned across security, IT, business leadership, data governance, privacy, and risk owners, per [CVC-5.2](cvc-5-security-model.md#cvc-5-governance-audit-and-incident-readiness).

#### On reporting

[CVC-5.6](cvc-5-security-model.md#cvc-5-governance-audit-and-incident-readiness) defines the reporting chain. Under `[Plug-in]`, artifacts feed upward into enterprise AI governance, and a parallel reporting chain must not be formed. Under `[Standalone]`, a single named individual must be the accountable owner of CVC-5 operations until enterprise governance absorbs the function.
 Metrics still report to management on a quarterly cycle.

#### On non-logging tools

[CVC-5.7](cvc-5-security-model.md#cvc-5-governance-audit-and-incident-readiness) sets a default posture: any AI tool that cannot produce or export logs sufficient to reconstruct prompts, retrieved context, tool invocations, and approvals is automatically limited to Tier 1 use only.
 Tier 2 or Tier 3 use of a non-logging tool requires a formal documented exception under [CVC-5.8](cvc-5-security-model.md#cvc-5-governance-audit-and-incident-readiness). That exception must include business justification, compensating controls, a named exception owner, an expiration date no greater than 90 days, and documented acceptance of residual risk signed by both a business and a security approver. Exceptions must be actively renewed at the next quarterly cycle; they do not roll over silently.

---

## Minimum Starting Baseline

For organizations operating under `[Standalone]`, there is a defensible minimum starting position. It is not the full framework, and it should not be treated as the destination. It is a place to stand while the rest is built.

It consists of seven moves, in roughly the order they should be taken.
 First, publish a one-page acceptable-use standard for work-related AI, accessible both to employees and to AI assistants themselves (machine-readability matters more here than people expect). Second, establish a lightweight registration process for recurring or material AI use cases — see [CVC-1.2](cvc-5-security-model.md#cvc-1-discovery-and-registration). Third, approve a defined set of enterprise AI tools and prohibit sensitive-data use in unapproved tools, with a clearly communicated alternative path that the prohibition points to. Fourth, define the three risk tiers and a small set of review triggers tied to data class, autonomy, and external exposure. Fifth, require human review and confirmation for all Tier 3 outputs and actions, captured outside the AI assistant's interface — this is the [CVC-3.4](cvc-5-security-model.md#cvc-3-prompt-agent-and-action-safety) out-of-band requirement. Sixth, add AI incident categories to the existing security incident-response process per [CVC-5.4](cvc-5-security-model.md#cvc-5-governance-audit-and-incident-readiness). Seventh, review the use-case inventory, exception register, and incident log quarterly, and report metrics to management.

This baseline is intentionally limited to seven requirements. An organization without governance cannot operate a control system with thirty-eight specific requirements; it can operate seven well, build the inventory, and then expand. The full catalog is the destination, not the starting line.

---

## Roles and Decision Rights

The framework runs on a small number of roles. The business use-case owner registers the use case, classifies its tier, ensures local process compliance, and is accountable for outcomes. Security or product security defines control standards, operates review triggers, publishes detection patterns, and defines AI incident categories. IT or the enterprise platform function approves enterprise AI tools, configures access, logging, and integration settings, and operates AI gateways. Data governance and privacy defines permitted AI data handling, sets review thresholds, and establishes retention constraints. Internal audit and compliance verifies evidence, reviews control operation, assesses exception management, and maps the framework to regulatory obligations. Under `[Plug-in]`, an AI governance body sets enterprise policy, arbitrates exceptions, receives metrics, and revises CVC-5 scope over time.

The detail of who-decides-what at each control is implicit in the normative model. These roles are not interchangeable, and CVC-5 cannot be operated entirely from within the security function. Attempting to do so produces the failure mode where security writes the standard, no one else owns its enforcement, and adoption flattens.

---

## Quick-Start Policy Language

The statements below are ready for direct use in internal policy documents. They should be adapted to organizational style and reviewed by legal before publication, but they encode the framework's normative content in policy-shaped language.

### CVC-1 Discovery and Registration

> All recurring work-related use of LLM tools, copilots, assistants, or agents must be registered with a designated human owner. Unapproved AI tools cannot process internal sensitive, confidential, or regulated data. The organization must maintain a continuously updated AI-BOM covering models, prompts, retrieval sources, embeddings, agent identities, and connected tools.

### CVC-2 Data Boundary Protection

> High-sensitivity corporate data cannot be submitted to public or consumer AI tools without an approved exception. AI tools and agents connected to enterprise data must operate under least privilege against approved data sources only. Vector stores and retrieval indexes must enforce access controls equivalent to those on the underlying source data.

### CVC-3 Prompt, Agent, and Action Safety

> AI systems processing untrusted external content cannot autonomously execute significant actions without explicit human confirmation captured outside the AI system's interface. Each agent operating against business systems must use a non-human identity with scoped credentials. Forbidden autonomous-action categories must be defined and enforced: employment status changes, payment approvals, contract execution, access provisioning, regulated communications.

### CVC-4 Output Validation and Human Accountability

> AI-assisted outputs used in significant decisions must be reviewed and approved by a named accountable human. Quantitative, legal, policy, and operational outputs from AI must be validated against authoritative sources before operational use. Provenance must be preserved for important AI-assisted outputs in a recognizable form.

### CVC-5 Governance, Audit, and Incident Readiness

> Material AI-related incidents must be reported through the enterprise incident-response process. Logs sufficient to reconstruct prompts, retrieved context, tool invocations, approvals, and resulting actions must be retained per applicable regulatory requirements and for at least six months. Registered AI use cases must be reviewed at defined intervals for continued business need, control sufficiency, and exception status.

---

## Metrics and Evidence

A framework that is not measured will not be maintained. The metrics CVC-5 cares about fall into three groups: operational, leading-indicator, and evidence.

The *operational* group tracks the framework's footprint and friction: registered citizen vibe coder use cases by tier, the proportion of AI tools in active use that are approved versus unapproved, shadow-AI discoveries per quarter and time-to-registration for newly discovered use, the proportion of high-risk use cases with named owners and current review evidence, the count and severity of AI-related incidents and near-misses and policy exceptions, and the proportion of high-risk workflows operating in approved enterprise environments.

The leading-indicator group is smaller and more diagnostic: the proportion of registered use cases with documented human-review evidence and the proportion of approved enterprise AI tools with logging actively retained. These two indicators tell you whether the framework is actually being operated or merely documented.

The evidence group supports audit and includes the use-case inventory and AI-BOM, tool-approval and exception registers, prompt and workflow templates, review attestations, and administrative logs and incident records.

Sixth, add AI incident categories to the existing security incident-response process per [CVC-5.4](cvc-5-security-model.md#cvc-5-governance-audit-and-incident-readiness).

Under `[Plug-in]`, metrics feed into the existing enterprise AI governance reporting cadence. Under `[Standalone]`, a reporting model must be selected — a one-page management summary to the CISO or equivalent is the lowest-friction option and the most easily inheritable by future governance; a live risk dashboard in existing GRC or BI tooling works well where the appetite for trend visibility exists; and embedding AI metrics into the existing quarterly security report avoids the appearance that AI risk is disconnected from security operations. The quarterly report must include use-case inventory changes, exception register status, incident log summary, and shadow-AI discovery count.

---

## Core Principle

The deepest commitment in CVC-5 is straightforward: an AI tool used to shape material business work is part of the business control surface, and it belongs to a recognizable owner under recognizable controls. This commitment does not require that AI be slow or that prohibitions be heavy. It requires the opposite. Approved patterns must be easier than shadow patterns. Prohibitions must be specific, narrow, and accompanied by a sanctioned alternative. Accountability must rest where the work rests — with the human producing the output, not with the model that helped produce it.

Organizations that get this right will find that CVC-5 fades into the background of how AI is used at work. Organizations that get it wrong will discover that they are running a parallel and uncontrolled software supply chain through people who never thought of themselves as developers. The framework is built to make the first outcome easier than the second.

---

## Cross-References to the Normative Model

- [How to Use This Document](cvc-5-security-model.md#how-to-use-this-document)
- [Section 1 — Purpose](cvc-5-security-model.md#1-purpose)
- [Section 2 — Scope](cvc-5-security-model.md#2-scope)
- [Section 3 — Design Principles](cvc-5-security-model.md#3-design-principles)
- [Section 4 — Governance Positioning](cvc-5-security-model.md#4-governance-positioning)
- [Section 5 — Threat Model](cvc-5-security-model.md#5-threat-model)
- [Section 6 — Risk Tiering Model](cvc-5-security-model.md#6-risk-tiering-model)
- [Section 7 — CVC-5 Control Catalog (Normative)](cvc-5-security-model.md#7-cvc-5-control-catalog-normative)
  - [CVC-1 — Discovery and Registration](cvc-5-security-model.md#cvc-1-discovery-and-registration)
  - [CVC-2 — Data Boundary Protection](cvc-5-security-model.md#cvc-2-data-boundary-protection)
  - [CVC-3 — Prompt, Agent, and Action Safety](cvc-5-security-model.md#cvc-3-prompt-agent-and-action-safety)
  - [CVC-4 — Output Validation and Human Accountability](cvc-5-security-model.md#cvc-4-output-validation-and-human-accountability)
  - [CVC-5 — Governance, Audit, and Incident Readiness](cvc-5-security-model.md#cvc-5-governance-audit-and-incident-readiness)
- [Appendix A — Framework Cross-Walk](cvc-5-security-model.md#appendix-a-framework-cross-walk)
- [Appendix B — Definitions](cvc-5-security-model.md#appendix-b-definitions)
- [Appendix C — Self-Assessment Checklist](cvc-5-security-model.md#appendix-c-self-assessment-checklist)

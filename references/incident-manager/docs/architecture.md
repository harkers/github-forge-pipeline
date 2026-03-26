# Incident Manager Architecture

## Purpose
The Incident Manager is designed to analyse confidentiality, privacy, and information incidents in a structured, auditable way. It should not operate as a free-form legal narrator. It should operate as an orchestrator that extracts facts, evaluates deterministic rules, and drafts operational outputs.

## Core capabilities
- Analyse incident facts
- Decompose incidents into consistent sections
- Identify privacy, confidentiality, security, regulatory, and contractual dimensions
- Determine relevant jurisdictions
- Apply rules packs for GDPR, UK GDPR / ICO, India DPDP, and confidentiality-only incidents
- Assess containment, root cause, corrective actions, and preventive actions
- Identify missing information and decision blockers
- Draft a ticket update statement
- Draft a requester response
- Produce a readable decision tree

## Recommended architecture
### 1. Manager agent
Responsibilities:
- Receive incident input
- Normalise facts into schema
- Select rules packs based on jurisdiction and incident type
- Merge outputs from sub-functions
- Generate final report and operational texts

### 2. Specialist modules or sub-agents
- Facts extractor
- Jurisdiction selector
- Rules evaluator
- Risk scorer
- Containment assessor
- Root cause and CAPA assessor
- Output composer
- Reviewer / learner

### 3. Rules-first decision model
The model should not decide notification thresholds from vibes. It should first evaluate facts against deterministic logic, then draft text.

## High-level workflow
1. Intake incident
2. Extract and normalise facts
3. Determine incident classification
4. Determine information type
5. Determine jurisdictions in scope
6. Evaluate rules packs
7. Score privacy and confidentiality risk
8. Assess containment and residual exposure
9. Identify missing information and blockers
10. Assess root cause and adequacy of corrective/preventive actions
11. Draft outputs
12. Log learning artefacts

## Output families
- Executive assessment
- Detailed incident assessment
- Risk assessment summary
- Missing information register
- Containment assessment
- Root cause assessment
- Corrective and preventive action plan
- Decision tree summary
- Ticket update statement
- Suggested reply to requester

## Guardrails
- Missing facts must be labelled as unknown
- Inferred facts must be labelled as inferred
- Regulatory conclusions must be downgraded when key facts are missing
- Legal logic should come from external versioned rules packs, not only prompt text
- Self-learning must be review-gated and regression-tested before promotion

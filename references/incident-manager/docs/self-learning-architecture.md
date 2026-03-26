# Controlled Self-Learning Architecture

## Objective
Enable the system to improve from completed incidents without allowing uncontrolled self-modification.

## Principle
The production agent should not rewrite its own live skills directly. Learning should happen in a separate review-and-promotion loop.

## Components
### 1. Production Incident Manager
Processes live incidents using approved prompts, templates, and rules.

### 2. Incident Reviewer / Learner
Reviews completed cases and compares:
- initial AI assessment
- final human-edited outputs
- final containment finding
- final risk finding
- final notification decision
- final CAPA outcome

### 3. Skill Updater
Converts approved learnings into:
- rules updates
- prompt updates
- decision-tree branch updates
- missing-information checks
- template improvements
- regression tests

### 4. Regression Tester
Runs historical test cases against proposed changes and compares outcomes.

### 5. Promotion Gate
Requires approval before updating production artefacts.

## Learning sources
High-value sources:
- final approved incident assessments
- final approved ticket notes
- final approved requester responses
- confirmed regulator/client outcomes
- completed post-incident reviews
- human corrections to AI outputs

Lower-value sources:
- speculative drafts
- incomplete tickets
- contradictory notes
- unverified commentary

## What can be improved
- wording templates
- missing info prompts
- root cause categorisation examples
- corrective/preventive action suggestions
- jurisdiction routing heuristics
- severity weighting proposals

## What should not auto-promote without approval
- notification threshold logic
- legal obligations phrasing treated as mandatory
- severity band thresholds that materially change outcomes
- deletion of safeguards or confidence gates

## Learning record schema
Each completed incident should capture:
- incident_id
- jurisdictions
- information types
- initial AI classification
- final human classification
- initial AI risk scores
- final human risk scores
- AI missing-info register
- newly discovered facts
- AI ticket update
- final ticket update
- AI requester reply
- final requester reply
- root cause initial vs final
- corrective/preventive actions initial vs final
- escalation / notification outcome
- reviewer comments

## Promotion workflow
1. Incident processed
2. Human reviews and edits outputs
3. Final outcome saved
4. Learner generates proposals
5. Regression tests run
6. Change report produced
7. Reviewer approves or rejects
8. Version increment applied
9. Pack promoted to production

## Versioning guidance
Every approved change should record:
- version
- date
- author / approver
- source incidents
- reason for change
- regression result
- rollback reference

# Incident Manager Pack

This pack contains a production-oriented starter kit for a management agent that can assess privacy, confidentiality, and broader information incidents.

Contents:
- docs/architecture.md — end-to-end system design
- docs/agent-spec.md — management-agent specification
- docs/self-learning-architecture.md — controlled self-improvement design
- config/incident-manager.yaml — main OpenClaw-style agent configuration scaffold
- config/rules/*.yaml — jurisdiction and confidentiality rules packs
- config/templates/*.md — output templates for ticket updates, requester replies, and decision trees
- config/tests/*.json — regression test scenarios
- examples/sample-incident.json — example incident input
- scripts/package-notes.md — notes for wiring into OpenClaw or another orchestrator

Design principles:
- structured fact extraction first
- deterministic rules before narrative drafting
- explicit handling of unknowns and confidence
- jurisdiction-aware logic blocks
- controlled self-learning with human approval gates

Suggested implementation order:
1. Load the incident schema and manager config
2. Run fact extraction into structured JSON
3. Evaluate relevant rules packs
4. Generate assessment outputs from templates
5. Store outcomes for reviewer/learner feedback
6. Promote improvements only after testing and approval

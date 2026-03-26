# Implementation Notes

## Suggested wiring
1. Feed incoming ticket text or form data to a normaliser.
2. Store the normalised incident JSON.
3. Pass fact model to the manager.
4. Manager selects rules packs.
5. Evaluate rules deterministically.
6. Pass rules output plus fact model into the drafting templates.
7. Save outputs and reviewer edits.
8. Feed completed outcomes into the learner pipeline.

## Self-learning guidance
- Keep `production_self_modification: false`.
- Require review and regression tests before promoting updated rule packs or templates.
- Maintain changelog and rollback points.

## Versioning suggestion
- Major: architecture or logic changes
- Minor: new rules pack or decision branch
- Patch: wording/template refinement

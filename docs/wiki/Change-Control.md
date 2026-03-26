# Change Control

How to request changes to the GitHub Forge Pipeline framework.

## What Needs Change Control

The following changes require formal approval:

- New workstreams
- New permanent initiatives
- Renaming workstreams or initiatives
- Changes to codes in active use
- Changes to priority or status models
- Changes to required fields
- Major changes to governance or operating rules

## What Doesn't Need Change Control

The following can be handled administratively:

- Creating new tasks within existing initiatives
- Correcting item metadata
- Updating descriptions or guidance
- Creating or refining views
- Administrative clean-up

## Change Process

### Step 1: Identify the Need

Determine what needs to change and why.

### Step 2: Check for Existing Coverage

Ask:
- Does an existing initiative already cover this?
- Is there a near-duplicate category?
- Would this create confusion?

### Step 3: Create a Taxonomy Change Request

1. Go to [New Issue](https://github.com/harkers/github-forge-pipeline/issues/new/choose)
2. Select **Taxonomy Change** template
3. Fill in the form

### Step 4: Review and Decision

The Project Owner reviews the request:
- **Approve** — Change is implemented
- **Reject** — Change is not needed
- **Request Info** — More context needed

### Step 5: Implementation

If approved:
1. Update documentation
2. Configure fields/labels if needed
3. Communicate the change

## Change Assessment Questions

Before approving a change, ask:

- Does this solve a real and recurring need?
- Does an existing category already cover it?
- Will this make classification clearer or more confusing?
- Will this create a near-duplicate bucket?
- Will it disrupt existing reporting or coding?
- Is the benefit worth the added complexity?

## Temporary Exceptions

Temporary exceptions may be used where:
- Urgent operational work cannot wait
- A proposed category needs proving
- A short-lived handling route is needed

Any temporary exception must be:
- Documented
- Given a clear reason
- Given an owner
- Reviewed periodically
- Either regularized or removed

## Documentation Update Rule

**No approved structural change is complete until documentation is updated.**

Update these files when taxonomy changes:
- This wiki
- `docs/` folder
- Any templates affected

## Decision Authority

| Change Type | Approver |
|-------------|----------|
| New workstream | Project Owner |
| New permanent initiative | Project Owner |
| Rename workstream/initiative | Project Owner |
| Change active codes | Project Owner |
| Change priority/status model | Project Owner |
| Change required fields | Project Owner |
| New task (existing initiative) | Maintainer |
| Correct metadata | Maintainer |
| Update descriptions | Maintainer |

## Submitting a Change Request

Use the template:

```markdown
## Proposed Change
[Describe what you want to change]

## Reason
[Why is this needed?]

## Impact
[How will this affect existing items?]

## Alternatives Considered
[What else was considered?]
```

## Emergency Changes

In urgent situations:
1. Document the temporary exception
2. Create the item with best-fit classification
3. Submit taxonomy change request
4. Reclassify once approved

---

*Last updated: 2026-03-26*
*See also: [Handbook Section 13](https://github.com/harkers/github-forge-pipeline/blob/main/docs/13-change-control.md)*

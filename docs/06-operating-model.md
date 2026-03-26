## Operating Model

github-forge-pipeline operates as the master planning and coordination layer for all defined workstreams. Its operating model describes how work is captured, classified, prioritised, progressed, reviewed, and closed within a single governed structure.

The operating model is intended to be simple, repeatable, and scalable. It should support both quick day-to-day task handling and more structured professional governance work without requiring different methods for each domain.

### Operating model purpose

The operating model exists to:

- provide a consistent end-to-end flow for all tracked work
- ensure new work is captured in a controlled way
- support effective triage and prioritisation
- maintain visibility of active, waiting, blocked, and completed work
- ensure items remain traceable throughout their lifecycle
- support consistent review, reporting, and closure

### Core workflow

All work should move through the following lifecycle:

1. capture
2. classify
3. triage
4. prioritise
5. progress
6. review
7. close

### Stage 1: Capture

Work is first captured into github-forge-pipeline as a new tracked item.

Capture may be triggered by:

- a new request
- an email or message
- an operational event
- a planned task
- an identified issue
- a new opportunity
- a recurring activity
- a project action
- a governance requirement

If classification is not yet clear, the item should be placed into the relevant Inbox initiative.

### Stage 2: Classify

Once captured, the item should be classified into the correct:

- workstream
- initiative
- code
- metadata fields

Classification should use the approved taxonomy only.

### Stage 3: Triage

Triage determines what the item is, how it should be handled, and how quickly it needs attention.

At triage, the item should be assigned:

- a valid code
- a priority
- a status
- an owner where possible
- a due date where relevant
- a next action where useful

### Stage 4: Prioritise

Priority is assigned using the approved model:

- P0 = critical today
- P1 = important next
- P2 = planned this week
- P3 = backlog
- P4 = parked

Priority reflects urgency and importance, not workflow state.

### Stage 5: Progress

Once triaged and prioritised, the item moves through active workflow states:

- Ready
- In Progress
- Waiting
- Blocked
- Review

Status should reflect reality. Items should not remain marked In Progress if no active work is taking place.

### Stage 6: Review

Review confirms whether the item is complete, accurate, and ready to close.

Review may include:

- checking whether the expected outcome has been achieved
- validating that required actions were completed
- confirming that links, notes, or outputs are recorded
- ensuring any dependencies or follow-on work are identified
- confirming that no further action remains hidden inside the item

### Stage 7: Close

Once complete, the item moves to:

- Status = Done

Closure should only occur when:

- the expected work is actually complete
- the outcome is sufficiently recorded
- no immediate follow-up remains inside the same item
- any necessary linked actions have been created separately

### Use of Inbox initiatives

Each workstream has an Inbox initiative to support initial capture of unclear or untriaged work. Inbox should not become a permanent storage location. Items should be triaged out of Inbox into their proper initiative as part of normal maintenance.

### Use of views

The master project should be used through defined views that support day-to-day control. Views should support action and visibility, not merely decoration.

### Workstream alignment

Where workstreams perform comparable functions, their operating approach should remain aligned where practical. This is especially important for Forge-ProPharma and Forge-HSBC.

### Handling recurring work

Recurring work should be handled using the same taxonomy and metadata rules as one-off work. Where a repeatable pattern exists, the framework should favour standard naming, reusable templates, predictable coding sequences, and consistent initiative placement.

### Operating cadence

Suggested cadence:

- daily: review P0 and P1 work and immediate actions
- weekly: triage Inbox, review waiting items, update priorities, confirm next actions
- periodically: review structure, retire duplication, and confirm taxonomy remains fit for purpose

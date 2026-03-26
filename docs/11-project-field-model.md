## Project Field Model

The GitHub Project field model provides the metadata needed to classify, prioritise, manage, and report on work consistently.

### Required fields

#### Code
Type: Text

Purpose:
- stores the stable tracking ID for the item

Rule:
- every tracked item must have a valid code once triaged

#### Status
Type: Single Select

Purpose:
- shows the current workflow state

Approved values:
- Inbox
- Ready
- In Progress
- Waiting
- Blocked
- Review
- Done

#### Priority
Type: Single Select

Purpose:
- shows urgency and importance

Approved values:
- P0
- P1
- P2
- P3
- P4

#### Workstream
Type: Single Select

Purpose:
- identifies the primary domain the work belongs to

Approved values:
- Forge-ProPharma
- Forge-HSBC
- Forge-Home
- Forge-Masonic

#### Initiative
Type: Single Select

Purpose:
- identifies the approved planning bucket within the workstream

Rule:
- use approved initiative names exactly

#### Due Date
Type: Date

Purpose:
- records the target completion date or required deadline where relevant

#### Next Action
Type: Text

Purpose:
- records the immediate next step needed to move the item forward

#### Owner
Type: Assignee or Text

Purpose:
- identifies who is responsible for moving the item

#### Notes
Type: Text

Purpose:
- stores short context, assumptions, or working notes

### Recommended optional fields

#### Impact
Type: Single Select

Suggested values:
- High
- Medium
- Low

Purpose:
- helps distinguish high-value work from lower-impact work

#### Risk
Type: Single Select

Suggested values:
- High
- Medium
- Low

Purpose:
- helps identify the level of consequence associated with delay or error

#### Waiting On
Type: Text

Purpose:
- records the person, team, or dependency preventing progress

#### External Deadline
Type: Date

Purpose:
- records an actual deadline imposed outside the framework

#### Link
Type: Text

Purpose:
- stores a URL, reference, ticket, or related system pointer

### Additional recommended professional fields

#### Vendor Name
Type: Text

Use for:
- vendor-linked work in ProPharma and HSBC

#### Business Area
Type: Text

Use for:
- identifying the relevant function, owner, or stakeholder area

#### Assessment Type
Type: Single Select

Suggested values:
- DPIA
- TIA
- LIA
- Legal
- Other

#### Regulatory Risk
Type: Single Select

Suggested values:
- High
- Medium
- Low

#### Incident Severity
Type: Single Select

Suggested values:
- S1
- S2
- S3
- S4

#### Notification Required
Type: Single Select

Suggested values:
- Yes
- No
- TBD

### Field principles

- keep required fields consistently populated
- do not add fields casually
- prefer a small number of high-value fields over a large number of neglected ones
- field meaning should stay stable over time
- metadata should support action, filtering, and reporting, not admin theatre

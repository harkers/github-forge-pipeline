# github-forge-pipeline handbook

## Purpose

github-forge-pipeline exists to provide a single governed planning and tracking structure for work across Forge-ProPharma, Forge-HSBC, Forge-Home, and Forge-Masonic.

Its purpose is to create one consistent operating model for capturing, prioritising, organising, and tracking work from intake through to completion. It establishes a shared structure for workstreams, initiatives, task identifiers, priorities, statuses, and project fields so that all work can be managed in a clear, repeatable, and scalable way.

The project is designed to:

- provide a single master view of all tracked work
- maintain clear separation between workstreams while preserving one control plane
- standardise naming, numbering, and classification
- support prioritisation of urgent, important, and backlog work
- improve visibility, consistency, and traceability
- enable easier reporting, filtering, and future automation
- reduce duplication, ambiguity, and ad hoc task management

github-forge-pipeline is not intended to replace execution tools or specialist repositories. It is the master planning and governance layer that sits above them, ensuring work is structured, visible, and manageable across personal, professional, and organisational domains.

## Scope

github-forge-pipeline covers the structured planning, intake, prioritisation, tracking, and oversight of work across the defined Forge workstreams:

- Forge-ProPharma
- Forge-HSBC
- Forge-Home
- Forge-Masonic

It includes:

- the creation and maintenance of a single master GitHub Project
- the definition and use of standard workstreams and initiatives
- the assignment of stable tracking codes for all managed items
- the use of consistent priority and status models
- the maintenance of required and optional project metadata
- the organisation of work into clear planning and reporting views
- the tracking of work from capture through completion
- the support of governance, visibility, traceability, and future automation

Within professional workstreams such as Forge-ProPharma and Forge-HSBC, scope includes the structured tracking of privacy, governance, and compliance activities, including but not limited to:

- data protection intake
- incidents and incident reporting
- vendors and sub-processor lists
- ROPA activities
- data rights work
- legislation assessments
- legitimate interest assessments
- privacy impact assessments
- transfer impact assessments

Within Forge-Home, scope includes personal organisation, life administration, career activity, maintenance, garden, cover, travel, and health-related planning.

Within Forge-Masonic, scope includes communications, mentoring, history, officers, and related planning activity.

github-forge-pipeline does not include:

- replacement of specialist execution platforms or repositories
- storage of full operational records where another system is the system of record
- detailed document authoring where dedicated repositories or tools are more appropriate
- unmanaged ad hoc naming or tracking approaches outside the approved taxonomy
- duplication of records purely for convenience where authoritative sources already exist

Where specialist tools, repositories, or systems are used for delivery, github-forge-pipeline acts as the master planning and governance layer above them, providing a consistent structure for control, visibility, and coordination.

## Objectives

The objectives of github-forge-pipeline are to:

1. establish a single master planning and tracking structure for all work managed across Forge-ProPharma, Forge-HSBC, Forge-Home, and Forge-Masonic

2. provide a consistent and governed operating model for capturing, classifying, prioritising, and progressing work from intake through to completion

3. standardise the use of workstreams, initiatives, task identifiers, priorities, statuses, and project fields so that work is managed in a clear, repeatable, and scalable way

4. improve visibility of active, upcoming, blocked, and completed work through a single control plane rather than disconnected lists, notes, or ad hoc trackers

5. ensure each task can be uniquely identified, traced, searched, filtered, and reported on through the use of stable naming and numbering conventions

6. support effective prioritisation by distinguishing clearly between urgency, importance, workflow status, and ownership

7. maintain alignment across comparable workstreams, particularly Forge-ProPharma and Forge-HSBC, so that similar categories of work can be tracked, reviewed, and reported consistently

8. reduce duplication, ambiguity, and inconsistency in how work is named, recorded, and managed

9. support better decision-making by making work easier to review by workstream, initiative, priority, due date, and other defined metadata

10. create a structure that is suitable for future automation, GitHub Project configuration, templated issue creation, reporting views, and operational dashboards

11. provide a planning layer that can sit above specialist repositories, systems, or delivery tools without replacing them, ensuring that coordination and governance remain centralised

12. enable a disciplined but practical method for managing personal, professional, and organisational work within one coherent framework

## Design Principles

github-forge-pipeline is governed by the following design principles:

1. one master project
   All tracked work is managed within a single master GitHub Project, github-forge-pipeline, to provide one control plane for visibility, prioritisation, and coordination.

2. clear separation of workstreams
   Work must be organised into defined workstreams so that distinct domains remain clear, manageable, and easy to review without losing the benefit of a shared master structure.

3. consistent initiative structure
   Work within each workstream must be grouped into approved initiatives using the standard naming model. Similar workstreams, particularly Forge-ProPharma and Forge-HSBC, should remain structurally aligned wherever practical.

4. stable naming and numbering
   Every tracked item must use the approved naming and numbering standard. Codes are intended to remain stable once in use so that items can be reliably referenced, searched, reported on, and linked over time.

5. clarity over cleverness
   The structure should favour names, categories, and rules that are immediately understandable. The system must remain practical to use day to day and not become unnecessarily complex.

6. priority and status are separate
   Priority must reflect urgency and importance. Status must reflect workflow state. These are distinct controls and must not be used interchangeably.

7. single source of planning truth
   github-forge-pipeline acts as the master planning and governance layer. Specialist tools, repositories, and systems may still be used for execution or record-keeping, but planning oversight should remain centralised here.

8. traceability by design
   Every item should be capable of being traced from capture through completion using stable identifiers, defined fields, and consistent categorisation.

9. governance before expansion
   New initiatives, naming changes, or structural variations should only be introduced where they provide clear value and do not undermine consistency. The taxonomy should grow deliberately, not reactively.

10. scalable from simple to complex
    The framework must work for simple personal tasks as well as more structured professional and governance activities, without needing a different operating model for each.

11. reporting and filtering must be easy
    The structure should support straightforward filtering, grouping, sorting, and reporting by workstream, initiative, priority, status, and due date.

12. future automation should be enabled
    The design should support later automation through GitHub Projects, issue templates, labels, scripts, dashboards, or orchestration tooling without requiring the taxonomy to be rebuilt.

13. minimise duplication
    Work should be recorded once in the right place with the right metadata, rather than duplicated across multiple trackers, lists, or near-identical categories.

14. practical governance over bureaucracy
    The framework should improve control and consistency without becoming burdensome. It must support disciplined working while remaining usable in real day-to-day conditions.

## Governance Model

github-forge-pipeline is governed as a controlled planning and tracking framework. Its governance model exists to preserve clarity, consistency, traceability, and long-term usability across all workstreams.

The governance model is designed to ensure that the structure remains stable, that naming and numbering conventions are applied consistently, and that expansion of the taxonomy happens deliberately rather than informally.

### Governance purpose

The governance model exists to:

- maintain the integrity of the github-forge-pipeline structure
- ensure consistent use of workstreams, initiatives, codes, priorities, statuses, and fields
- prevent duplication, drift, and uncontrolled creation of near-identical categories
- support traceability and reliable reporting
- enable controlled evolution of the framework as needs change over time

### Governance ownership

The github-forge-pipeline framework must have a defined owner.

#### Project Owner

The Project Owner is responsible for overall control of the framework, including:

- approving the master taxonomy
- approving additions, removals, or renaming of workstreams and initiatives
- approving changes to numbering conventions, field structures, and operating rules
- maintaining alignment between comparable workstreams
- ensuring the framework continues to support real operational needs

#### Maintainer

The Maintainer is responsible for day-to-day administration of the framework, including:

- keeping the taxonomy and supporting documentation up to date
- creating or updating project fields, views, and templates
- checking that new items are created using the correct standards
- correcting inconsistencies in naming, coding, or classification
- proposing improvements to the Project Owner where needed

#### Contributor

Contributors are responsible for using the framework correctly when adding or updating items, including:

- selecting the correct workstream and initiative
- applying the correct code format
- using the agreed priority and status values
- avoiding duplicate or unofficial categories
- keeping item information accurate and current

#### Reviewer

Where used, a Reviewer is responsible for checking that items, structures, or proposed changes comply with the approved framework and are fit for purpose before they are adopted more widely.

### Governance scope

Governance applies to the following elements:

- the master GitHub Project
- workstream definitions
- initiative definitions
- naming conventions
- numbering conventions
- priority model
- status model
- field model
- views and reporting structure
- intake and triage rules
- change control rules

### Controlled elements

The following elements are controlled and must not be changed informally:

- workstream names
- initiative names
- workstream codes
- initiative codes
- task ID format
- required project fields
- priority values
- status values
- canonical views where formally adopted

Once codes are in active use, they should be treated as stable identifiers and should not be changed unless there is a strong operational reason and a controlled update is performed.

### Governance rules

1. all work must be recorded within the approved master structure  
   Work should not be managed through unofficial parallel naming schemes or shadow taxonomies.

2. all initiatives must use approved names  
   Near-duplicate initiative names must not be introduced.

3. all task identifiers must follow the approved numbering format  
   Items without a valid code should be treated as incomplete until corrected.

4. priority and status must be applied consistently  
   These values must be selected using the approved definitions and must not be used interchangeably.

5. comparable workstreams should remain aligned where appropriate  
   Forge-ProPharma and Forge-HSBC should remain structurally aligned unless there is a clear reason for divergence.

6. reserved codes must not be used casually  
   Reserved initiatives and codes should only be activated intentionally.

7. documentation must be updated when structural changes are approved  
   The framework documentation must remain current and authoritative.

### Decision authority

The following decision approach should apply:

#### Changes requiring approval by the Project Owner

- creation of a new workstream
- deletion of a workstream
- creation of a new permanent initiative
- renaming of a workstream or initiative
- changes to codes already in use
- changes to the priority or status models
- changes to the required field model
- major changes to governance or operating rules

#### Changes that may be handled by the Maintainer

- creating new tasks within existing initiatives
- correcting item metadata
- improving descriptions or guidance text
- creating or refining views based on the approved taxonomy
- administrative clean-up that does not alter the approved structure

### Exceptions

Exceptions should be rare and should only be allowed where:

- the approved taxonomy genuinely cannot represent the work
- an urgent operational need requires temporary handling
- a future permanent change is being evaluated

Any exception should be documented, reviewed, and either regularised into the framework or removed once no longer needed.

### Review and maintenance

The governance model should be reviewed periodically to ensure that:

- the taxonomy still reflects actual work
- unused initiatives are identified
- duplicated or overlapping structures are avoided
- field definitions remain practical
- views and reports remain useful
- future automation remains supported

A light-touch periodic review should be sufficient unless major structural growth occurs.

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

## Roles and Responsibilities

github-forge-pipeline should operate with clear role definitions even where one individual currently performs multiple roles. Clear role boundaries support consistency, future scaling, and cleaner decision-making.

### Project Owner

The Project Owner is accountable for the overall integrity and direction of github-forge-pipeline.

Responsibilities:

- own the master framework and its intended purpose
- approve changes to the taxonomy, field model, and control rules
- decide when new permanent initiatives should be created
- approve structural alignment or divergence between comparable workstreams
- resolve classification disputes or ambiguity where required
- ensure the framework remains useful rather than ceremonial

### Maintainer

The Maintainer administers the framework on a day-to-day basis and ensures it remains accurate and operational.

Responsibilities:

- maintain the handbook and supporting reference files
- configure and maintain GitHub Project fields and views
- create and update templates, guidance, and examples
- ensure new items follow naming, numbering, and field standards
- tidy inconsistencies, duplication, or drift
- prepare proposed changes for review by the Project Owner

### Contributor

Contributors add, update, and progress work items within the approved model.

Responsibilities:

- capture work promptly and clearly
- select the correct workstream and initiative
- assign valid codes and metadata
- use priorities and statuses correctly
- keep items current as work progresses
- avoid creating near-duplicate categories or unofficial structures

### Reviewer

A Reviewer checks that work or structural changes are complete, sensible, and compliant with the approved framework.

Responsibilities:

- review item quality and completeness where needed
- confirm structural changes are justified and correctly documented
- identify ambiguity, overlap, or weak classification
- validate that reporting views and examples remain meaningful

### Role combination

In a single-user operating model, one person may hold all roles. Even so, the responsibilities should still be observed distinctly. This helps maintain discipline and makes future delegation easier.

### Responsibility principles

- accountability should be clear
- administration should be practical
- contributors should follow the approved taxonomy
- reviews should improve quality, not create unnecessary delay
- the framework should be actively maintained, not merely declared

## Workstream Definitions

Each workstream represents a defined domain of work within github-forge-pipeline. Workstreams provide the highest level of classification below the master project and exist to preserve separation between distinct areas while maintaining one control plane.

### Forge-ProPharma

Forge-ProPharma is the professional workstream used to track privacy, governance, compliance, and related operational work associated with ProPharma.

It includes activities such as:

- data protection intake
- incidents and reporting
- vendors and sub-processors
- ROPA maintenance
- data rights handling
- legal and governance assessments
- privacy and transfer risk assessments

Forge-ProPharma should be used where the work is tied directly to ProPharma operations, governance, or delivery context.

### Forge-HSBC

Forge-HSBC is the professional workstream used to track privacy, governance, compliance, and related operational work associated with HSBC.

It mirrors the structure of Forge-ProPharma so that comparable activities can be managed consistently across both workstreams.

It includes activities such as:

- data protection intake
- incidents and reporting
- vendors and sub-processors
- ROPA maintenance
- data rights handling
- legal and governance assessments
- privacy and transfer risk assessments

Forge-HSBC should be used where the work is tied directly to HSBC-specific context.

### Forge-Home

Forge-Home is the personal workstream used to track life administration, practical organisation, recurring tasks, and personal systems that make day-to-day life easier to manage.

It includes activities such as:

- general inbox and life admin
- career and recruiter activity
- home maintenance
- garden planning
- insurance and cover tracking
- travel planning
- health-related planning

Forge-Home should be used for structured personal work that benefits from being captured, prioritised, and reviewed in the same operating model as professional work.

### Forge-Masonic

Forge-Masonic is the workstream used to track communications, mentoring, history, officer development, and related planning within the Masonic domain.

It includes activities such as:

- AMH communications
- mentoring design and support
- historical research and backlog management
- officer development and planning

Forge-Masonic should be used where the work belongs to your Masonic research, communications, or organisational activity rather than personal admin or professional data protection work.

### Workstream classification rule

Each item must belong to one primary workstream. If an item appears to touch more than one domain, it should be placed in the workstream that best represents its main operational purpose.

## Initiative Definitions

Initiatives are the approved planning buckets within each workstream. They provide the second level of classification below the workstream and ensure similar work is grouped consistently.

### Professional workstream initiatives

The following definitions apply to both Forge-ProPharma and Forge-HSBC unless explicitly stated otherwise.

#### Inbox

The Inbox initiative is used for newly captured work that has not yet been fully triaged or classified.

Use it when:
- the correct initiative is not yet known
- the task was captured quickly and needs review
- more context is needed before proper classification

Do not use Inbox as a permanent storage location.

#### Data-Protection-Intake

Data-Protection-Intake is used for intake, triage, and initial handling of new privacy or governance requests.

Use it for:
- new privacy review requests
- intake categorisation
- initial assignment or triage
- front-door handling before work moves elsewhere

#### Incidents

Incidents is used for live incident casework.

Use it for:
- confidentiality incidents
- misdirected emails
- unauthorised access events
- containment activity
- impact assessment
- root cause analysis
- corrective actions
- closure of the incident case

#### Incident-Reporting

Incident-Reporting is used for oversight, metrics, and management reporting across incidents.

Use it for:
- monthly or quarterly reports
- trend analysis
- recurring issue analysis
- lessons learned summaries
- leadership or governance reporting

Rule:
- one specific incident case belongs in Incidents
- cross-incident reporting belongs in Incident-Reporting

#### Vendors

Vendors is used for vendor review and oversight activity.

Use it for:
- vendor onboarding or review
- DPA and contract review
- privacy review of processor arrangements
- vendor risk remediation
- lifecycle tracking of vendor governance actions

#### Sub-Processor-List

Sub-Processor-List is used for maintenance and review of the sub-processor register or published list.

Use it for:
- adding new entities
- updating legal entity details
- reviewing processing locations
- maintaining public or internal list accuracy
- updating change history where relevant

Rule:
- the vendor review itself belongs in Vendors
- register maintenance belongs in Sub-Processor-List

#### ROPA

ROPA is used for record of processing activities work.

Use it for:
- creating or updating ROPA entries
- reviewing processing descriptions
- checking purpose, category, system, or transfer details
- remediating ROPA gaps

#### Data-Rights

Data-Rights is used for data subject rights and related request handling.

Use it for:
- access requests
- deletion requests
- rectification requests
- restriction or objection handling
- request triage and progress tracking

#### Legislation-Assessments

Legislation-Assessments is used for structured review of legal or regulatory changes and their operational effect.

Use it for:
- review of new legal requirements
- gap analysis against new laws or guidance
- impact analysis for governance updates
- documenting required actions from legal change

#### Legitimate-Interest-Assessments

Legitimate-Interest-Assessments is used for LIA work.

Use it for:
- balancing tests
- assessment drafting
- review and refresh of LIAs
- evidence gathering linked to legitimate interests

#### Privacy-Impact-Assessments

Privacy-Impact-Assessments is used for general privacy risk assessment work.

Use it for:
- DPIAs
- PDRAs
- structured privacy assessments
- assessment review and remediation actions

Rule:
- general privacy risk work belongs here
- transfer-specific international transfer analysis belongs in Transfer-Impact-Assessments

#### Transfer-Impact-Assessments

Transfer-Impact-Assessments is used for transfer risk analysis and international transfer assessment work.

Use it for:
- TIAs
- country risk review
- supplementary measures analysis
- transfer documentation and decision-making

### Home initiatives

#### Forge-Home-Inbox

Used for untriaged or newly captured personal work.

#### Forge-Home-Life-Easier

Used for practical personal improvements, systems, routines, and tasks designed to reduce friction in day-to-day life.

#### Forge-Home-Career

Used for recruiter contact, CV work, job applications, interviews, offers, and related professional opportunity tracking.

#### Forge-Home-Maintenance

Used for household jobs, repairs, maintenance planning, and practical property upkeep.

#### Forge-Home-Garden

Used for planting, seasonal jobs, records, and garden planning activity.

#### Forge-Home-Cover

Used for insurance, protection products, renewals, and related oversight.

#### Forge-Home-Travel

Used for travel planning, document preparation, itineraries, and related administration.

#### Forge-Home-Health

Used for structured health-related planning, non-clinical tracking, and administrative follow-up.

### Masonic initiatives

#### Forge-Masonic-Inbox

Used for newly captured or untriaged Masonic work.

#### Forge-Masonic-Comms-AMH

Used for communications planning and activity associated with AMH-related work.

#### Forge-Masonic-Mentoring

Used for mentoring design, resources, pathways, and related planning.

#### Forge-Masonic-History

Used for research backlog, historical notes, evidence gathering, and heritage-related work.

#### Forge-Masonic-Officers

Used for officer development, planning, role notes, and related coordination.

### Initiative classification rule

Each item must be assigned to the initiative that best reflects its primary purpose. If the work changes shape over time, a new linked item may be created rather than forcing unrelated activities into a single ticket.

## Naming and Numbering Standard

A consistent naming and numbering standard is required so that all items are easy to identify, search, sort, filter, and report on.

### Workstream naming

Workstreams must follow this format:

Forge-<Workstream>

Examples:
- Forge-ProPharma
- Forge-HSBC
- Forge-Home
- Forge-Masonic

### Initiative naming

Initiatives must follow this format:

Forge-<Workstream>-<Initiative>

Examples:
- Forge-ProPharma-ROPA
- Forge-HSBC-Transfer-Impact-Assessments
- Forge-Home-Career
- Forge-Masonic-Comms-AMH

### Task ID format

All tracked items must use this code format:

GFP-<WORKSTREAM CODE>-<INITIATIVE CODE>-<NUMBER>

Examples:
- GFP-PP-ROP-001
- GFP-HB-TIA-002
- GFP-HM-CAR-001
- GFP-MS-CAMH-001

### Workstream codes

- PP = ProPharma
- HB = HSBC
- HM = Home
- MS = Masonic

### Core initiative codes for ProPharma and HSBC

- INB = Inbox
- DPI = Data-Protection-Intake
- INC = Incidents
- IRP = Incident-Reporting
- VND = Vendors
- SPL = Sub-Processor-List
- ROP = ROPA
- DRT = Data-Rights
- LGA = Legislation-Assessments
- LIA = Legitimate-Interest-Assessments
- PIA = Privacy-Impact-Assessments
- TIA = Transfer-Impact-Assessments

### Home initiative codes

- INB = Inbox
- LIFE = Life-Easier
- CAR = Career
- MAINT = Maintenance
- GARD = Garden
- COV = Cover
- TRAV = Travel
- HLTH = Health

### Masonic initiative codes

- INB = Inbox
- CAMH = Comms-AMH
- MENT = Mentoring
- HIST = History
- OFF = Officers

### Task title format

Task titles should use this structure:

[<TASK ID>] <Plain-English task title>

Examples:
- [GFP-PP-INC-001] Assess confidentiality incident facts
- [GFP-HB-VND-001] Review vendor DPA and transfer clauses
- [GFP-HM-CAR-001] Send CV for high-value assignment
- [GFP-MS-CAMH-001] Draft AMH communications outline

### Numbering rules

- numbers should normally use a three-digit sequence
- numbering should be unique within the initiative code and workstream combination
- once a code is in use, it should remain stable
- avoid renumbering existing items unless absolutely necessary
- reserved codes should remain unused until formally activated

### Naming rules

- use approved initiative names only
- do not create unofficial abbreviations in item titles
- prefer clear plain-English task names
- do not bury unrelated work inside one oversized item
- do not create near-duplicate initiatives because a task feels slightly special

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

## Views and Reporting

Views exist to make github-forge-pipeline usable as a daily control plane rather than a flat list of items. Reporting should emerge naturally from consistent structure, fields, and naming.

### Core views

The following views are recommended within the master GitHub Project:

- All Work
- P0 / P1 Focus
- This Week
- Waiting
- Forge-ProPharma
- Forge-HSBC
- Forge-Home
- Forge-Masonic
- Incidents
- Vendors
- Assessments
- Done

### View purposes

#### All Work
Use for:
- full visibility across the framework
- broad review of active and upcoming work
- identifying distribution across workstreams

#### P0 / P1 Focus
Use for:
- immediate priority review
- daily decision-making
- ensuring genuinely urgent work is visible

#### This Week
Use for:
- weekly planning
- managing near-term due work
- balancing ready and in-progress items

#### Waiting
Use for:
- reviewing stalled work
- chasing dependencies
- preventing forgotten items from fossilising quietly

#### Forge-ProPharma / Forge-HSBC / Forge-Home / Forge-Masonic
Use for:
- focused review by domain
- weekly or workstream-specific check-ins
- cleaner planning inside each area

#### Incidents
Use for:
- reviewing all incident-related casework across relevant workstreams
- identifying active or high-severity incident items

#### Vendors
Use for:
- vendor review and sub-processor oversight
- identifying upcoming renewals or outstanding governance actions

#### Assessments
Use for:
- reviewing LIA, PIA, TIA, and legal assessment work
- managing governance assessment throughput

#### Done
Use for:
- closure review
- recent completion history
- periodic archiving or housekeeping

### Recommended grouping

Primary grouping:
- Workstream

Secondary grouping:
- Initiative

### Recommended sorting

Sort order should usually be:
1. Priority
2. Due Date
3. Code

### Reporting principles

- reporting should use the approved field model
- views should support action, not just display
- keep the number of views manageable
- retire views that are no longer useful
- avoid duplicate views that differ only cosmetically

### Reporting outputs

Typical reporting outputs may include:

- current P0 and P1 load
- items due this week
- waiting and blocked work
- incident volume and trend visibility
- vendor review backlog
- assessment throughput
- workstream distribution
- completed items over time

### Reporting rule

If reporting becomes difficult, the first check should be whether naming, classification, and fields are being applied consistently rather than immediately adding more views.

## Change Control

Change control exists to ensure that github-forge-pipeline evolves deliberately and remains coherent over time. The framework should be capable of growth, but that growth must be managed rather than improvised.

### Change control purpose

Change control exists to:

- protect the integrity of the approved taxonomy
- prevent duplication and structure drift
- maintain stable codes and naming
- ensure new elements add real value
- preserve reporting and automation compatibility

### Changes that require control

The following changes should be treated as controlled changes:

- new workstreams
- new permanent initiatives
- renaming workstreams or initiatives
- changes to workstream or initiative codes
- changes to task ID structure
- changes to required fields
- changes to priority or status values
- major changes to operating rules
- retirement of established initiatives

### Standard change process

1. identify the need for change
2. describe the proposed change clearly
3. check whether an existing workstream, initiative, or field already meets the need
4. assess the effect on naming, numbering, views, reporting, and future automation
5. decide whether the change should be approved, rejected, or trialled temporarily
6. update the canonical documentation if approved
7. implement the change consistently across the project
8. communicate or apply the change in future item creation

### Change assessment questions

Before approving a change, ask:

- does this solve a real and recurring need
- does an existing category already cover it
- will this make classification clearer or more confusing
- will this create a near-duplicate bucket
- will it disrupt existing reporting or coding
- is the benefit worth the added complexity

### Temporary exceptions

A temporary exception may be used where:

- urgent operational work cannot sensibly wait
- a proposed category needs proving before permanent adoption
- a short-lived handling route is needed

Any temporary exception should:

- be documented
- have a clear reason
- have an owner
- be reviewed
- either be regularised or removed

### Documentation update rule

No approved structural change is complete until the handbook and relevant reference files are updated. The documentation is part of the control, not an optional souvenir.

### Change control principle

Fewer well-designed changes are better than frequent reactive changes. A stable framework beats a creative one that needs rescuing every month.

## Examples

The following examples show how items should be represented within github-forge-pipeline.

### ProPharma examples

#### Live incident casework

Initiative:
- Forge-ProPharma-Incidents

Item:
- [GFP-PP-INC-001] Assess confidentiality incident facts

Suggested metadata:
- Status: In Progress
- Priority: P0
- Workstream: Forge-ProPharma
- Initiative: Forge-ProPharma-Incidents
- Next Action: Confirm facts with reporting team
- Incident Severity: S2
- Notification Required: TBD

#### Cross-incident reporting

Initiative:
- Forge-ProPharma-Incident-Reporting

Item:
- [GFP-PP-IRP-001] Prepare monthly incident metrics pack

Suggested metadata:
- Status: Ready
- Priority: P2
- Workstream: Forge-ProPharma
- Initiative: Forge-ProPharma-Incident-Reporting
- Next Action: Compile month-end incident totals

#### Vendor review

Initiative:
- Forge-ProPharma-Vendors

Item:
- [GFP-PP-VND-001] Review vendor DPA and transfer clauses

Suggested metadata:
- Status: Ready
- Priority: P1
- Vendor Name: Example Vendor Ltd
- Assessment Type: Legal
- Regulatory Risk: Medium

#### Sub-processor list maintenance

Initiative:
- Forge-ProPharma-Sub-Processor-List

Item:
- [GFP-PP-SPL-001] Add new processor entity to sub-processor list

Suggested metadata:
- Status: Ready
- Priority: P2
- Vendor Name: Example Vendor Ltd
- Next Action: Confirm legal entity name and hosting location

#### Privacy assessment

Initiative:
- Forge-ProPharma-Privacy-Impact-Assessments

Item:
- [GFP-PP-PIA-001] Review privacy impact assessment for new platform

Suggested metadata:
- Status: Review
- Priority: P1
- Assessment Type: DPIA
- Regulatory Risk: High

### HSBC examples

#### Transfer assessment

Initiative:
- Forge-HSBC-Transfer-Impact-Assessments

Item:
- [GFP-HB-TIA-001] Complete transfer impact assessment for vendor

Suggested metadata:
- Status: In Progress
- Priority: P1
- Assessment Type: TIA
- Vendor Name: Example Vendor Ltd
- Next Action: Review transfer destination and supplementary measures

#### ROPA update

Initiative:
- Forge-HSBC-ROPA

Item:
- [GFP-HB-ROP-001] Update ROPA entry for new workflow

Suggested metadata:
- Status: Ready
- Priority: P2
- Business Area: Example Business Area
- Next Action: Confirm system and transfer details

### Home examples

#### Recruiter firm offer

Initiative:
- Forge-Home-Career

Item:
- [GFP-HM-CAR-001] Respond to recruiter firm offer actions

Suggested metadata:
- Status: Ready
- Priority: P0
- Due Date: today
- Next Action: Review action list and send reply

#### High-value assignment CV

Initiative:
- Forge-Home-Career

Item:
- [GFP-HM-CAR-002] Send CV for high-value assignment

Suggested metadata:
- Status: Ready
- Priority: P1
- Next Action: Tailor CV and send to recruiter

#### Life admin improvement

Initiative:
- Forge-Home-Life-Easier

Item:
- [GFP-HM-LIFE-001] Build recurring life-admin checklist

Suggested metadata:
- Status: In Progress
- Priority: P2
- Next Action: Draft monthly recurring items

### Masonic examples

#### Communications planning

Initiative:
- Forge-Masonic-Comms-AMH

Item:
- [GFP-MS-CAMH-001] Draft AMH communications outline

Suggested metadata:
- Status: Ready
- Priority: P2
- Next Action: Define audience, purpose, and first message themes

#### Historical research backlog

Initiative:
- Forge-Masonic-History

Item:
- [GFP-MS-HIST-001] Catalogue current history research backlog

Suggested metadata:
- Status: In Progress
- Priority: P2
- Next Action: Consolidate current notes into one backlog list

### Example classification rules

- a live incident goes in Incidents, not Incident-Reporting
- an incident trend pack goes in Incident-Reporting, not Incidents
- a vendor contract review goes in Vendors, not Sub-Processor-List
- updating the published sub-processor record goes in Sub-Processor-List
- a recruiter offer action belongs in Forge-Home-Career, not Inbox once triaged

## Future Development

github-forge-pipeline is designed to support phased development over time. The initial objective is to establish a stable handbook, taxonomy, and operating model. Once that foundation is in place, further enhancements can be added in a controlled way.

### Near-term development priorities

The following are sensible next steps after the handbook is established:

- create GitHub issue templates aligned to workstreams and initiatives
- define a matching label strategy
- configure the GitHub Project field model
- build the initial view set
- seed example items and reference tasks
- create a CLI bootstrap script for repeatable setup

### Medium-term enhancements

Once the framework is operating cleanly, the following may be added:

- standard templates for recurring work types
- automation for item creation or movement
- recurring review cadence support
- reporting summaries by workstream, initiative, and priority
- dashboard views for active, waiting, and due work
- lightweight archival and housekeeping rules

### Longer-term development options

Potential future extensions include:

- integration with orchestration workflows
- scripted creation of initiatives, fields, and views
- linked issue templates by assessment or incident type
- reusable packs for new repositories or workspaces
- reporting exports for periodic review
- personal and professional dashboard surfaces

### Development principles

Future development should follow these rules:

- protect the existing taxonomy first
- avoid adding automation before the underlying data is clean
- prefer a small number of useful improvements over many decorative ones
- keep ProPharma and HSBC aligned where practical
- document every structural enhancement as part of the framework

### Initial recommended roadmap

Phase 1:
- handbook and taxonomy complete

Phase 2:
- project fields, labels, and views configured

Phase 3:
- issue templates and starter items in place

Phase 4:
- CLI bootstrap and repeatable setup

Phase 5:
- automation, dashboards, and reporting improvements

### Future development outcome

The intended outcome is a framework that remains controlled, understandable, and operationally useful while becoming easier to run, easier to search, and easier to automate over time.


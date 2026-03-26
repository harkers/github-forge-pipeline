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

# Proposed Status Model and Governance

**Status:** Proposed design; validate against actual institutional policy before use.

## Inputs
Request reference; student identifier (restricted); submission timestamp; applicable clearance categories; completeness result; department outcomes; pending reason; current owner; next action/date; final decision; approving role; audit history.

## Status definitions

| Status | Entry condition | Exit condition |
|---|---|---|
| Submitted | Request received | Intake review starts |
| Needs Information | Required field or supporting information missing | Student supplies the missing information and intake rechecks |
| Under Verification | Request is complete and checks have been routed | Department results are recorded |
| Pending Student Action | A specific action from student is required | Student resolves it and evidence is checked |
| Pending Department | A department has not completed or clarified its check | Authorized department records a result |
| On Hold — System or Record Issue | Verification cannot be completed reliably | Issue resolved and the step is retried |
| Ready for Final Review | All mandatory checks have a valid outcome | Authorized final review decision |
| Approved / Completed | Authorized approval recorded and closure conditions met | Terminal state |
| Rejected | Authorized decision with reason recorded | Terminal state or formal review route, as policy permits |

## Ownership
- Accountable owner: designated Student Affairs / Student Department manager (proposed).
- Departmental verifier: responsible for that department's records only.
- Final approver: officer designated by actual institutional policy.
- Register administrator: access, backups and audit history; no implied approval power.

## Controls
1. Do not infer approval from silence.
2. Keep an audit trail of status changes, who changed them, when, and why.
3. Restrict student-level information to authorized roles.
4. Detect and link duplicate requests before routing.
5. Do not allow final completion until mandatory checks and final approval are recorded.
6. Define retention and deletion under institutional policy; do not invent a retention period.

## Fallback
Use a restricted, approved manual register during an outage. Allocate a temporary request reference, record the last verified stage, owner, timestamp and reason. After recovery, reconcile entries and resume from the last verified stage. Keep the case pending until all mandatory checks are complete.

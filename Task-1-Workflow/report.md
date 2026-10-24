# Task 1 — Investigate and Improve a No-Due Clearance Workflow

**Case-study date:** 24 October 2026  
**Context:** ICFAI / IFHE college setting  
**Evidence type:** Synthetic demonstration dataset and desk-based process design  
**Status:** Complete as a simulation; institutional validation remains pending.

## 1. Executive summary

This project investigates a proposed college No-Due Clearance process. Since actual process data was unavailable, an authorized personnel member advised the student to create synthetic data. Accordingly, all request records, simulated observations, timings, case outcomes and volume assumptions in this report are fictional. They demonstrate how a small workflow investigation can be conducted without claiming access to real student records.

The design models a request moving from submission, through checks by applicable departments, to an authorized final review and closure. The proposed improvement is an access-controlled status register that identifies the current status, next responsible role, pending reason and recovery action. It does not remove mandatory departmental checks or final authorization.

**Illustrative outcome:** With the assumptions documented in the ROI file, estimated active staff effort decreases from 24 to 15 minutes per request, a net saving of 9 minutes per request. At a hypothetical 100 requests per month, that is 15 staff hours per month. These are scenario calculations, not measured IFHE outcomes.

## 2. Objective and scope

### Objective
- Map a plausible current-state process, including handoffs, approvals and exceptions.
- Keep a dated evidence log and label simulated facts, estimates and assumptions.
- Identify a testable problem and estimate its possible scale.
- Propose a process with defined inputs, statuses, ownership, approval boundaries and fallback.
- Test five synthetic cases: normal, missing information, duplicate, unauthorized request and failed step.
- Calculate net time saved after review and support effort.

### Scope
Start: a student submits a No-Due Clearance request.  
End: an authorized office records the final outcome and notifies the student.

Potential departments (for example, library, accounts, laboratory or hostel) are illustrative only. Actual applicable units must be confirmed by the institution.

## 3. Evidence standard and disclosure

The data is synthetic because actual process data was unavailable and personnel advised generating synthetic data. The CSVs intentionally use fictional request IDs such as `SYN-001` and generic roles. No real student names, IDs, financial details, signatures or contact information are included.

Labels used in this report:
- **Synthetic scenario:** invented to test the proposed workflow.
- **Estimate:** a plausible planning value used for calculations, not measured.
- **Assumption:** a condition temporarily accepted for design purposes.
- **Proposed control:** a recommended rule, not a statement of existing college policy.
- **Observed fact:** limited to what is directly visible in this project context, such as the existence of the assignment and the lack of actual process data supplied for analysis. No process observation or staff interview is claimed.

## 4. Current-state workflow model

This is a **hypothesized baseline**, not a verified description of IFHE operations.

1. Student submits a request to the designated receiving office.
2. Receiving office checks whether required information is present.
3. The request is sent to applicable departments for clearance checks.
4. Departments report `Cleared`, `Pending` or `Unable to Verify`.
5. Student or department resolves any outstanding issue.
6. A designated authorized officer performs the final review.
7. The receiving office records the outcome and notifies the student.

### Handoffs and approvals

| Stage | Proposed role | Handoff/control |
|---|---|---|
| Submit | Student | Provide required fields and select applicable clearance categories |
| Intake | Receiving office | Check completeness and duplicate requests |
| Department checks | Authorized departmental staff | Verify only records within that department's authority |
| Resolve pending item | Student and responsible department | Record the reason and required action |
| Final review | Authorized approving officer | Approve only when all mandatory checks are complete |
| Close | Receiving office | Record decision, timestamp and notification |

### Exceptions to investigate

- Missing information
- Duplicate submission
- Request made by an unauthorized person
- Outstanding dues or conflicting records
- Department system unavailable or verification failure
- Final approver unavailable
- Student disputes a recorded pending item

## 5. Problem and synthetic scale estimate

### Problem hypothesis
A multi-step clearance process can become difficult to track when there is no single view of current status, next owner, and unresolved checks. Possible effects include repeated status enquiries, duplicated checking and delays in finding the person responsible for the next action.

This is a hypothesis to test; the repository does not claim these issues have been observed at IFHE.

### Synthetic sample
The included sample contains 12 fictional requests:
- 5 routine requests
- 2 requests with missing information
- 2 duplicate submissions
- 1 unauthorized request
- 2 failed-step / record-verification scenarios

These counts are deliberately constructed to exercise process branches. They do not estimate the real prevalence of these events.

### Illustrative scale formula
`Monthly follow-up hours = requests per month × follow-ups per request × minutes per follow-up ÷ 60`

For example, if an assumed 100 requests per month each require 3 follow-ups of 5 minutes, the estimated follow-up workload is `100 × 3 × 5 ÷ 60 = 25 staff hours/month`. Every input is hypothetical and should be replaced by measured data in a permitted pilot.

## 6. Proposed improved workflow

Use a simple access-controlled spreadsheet or mock register during the prototype stage. A production application is not required for this assignment.

### Inputs
- Unique request reference
- Student identifier (restricted access; use synthetic IDs in demonstrations)
- Submission date/time
- Requested clearance categories
- Completeness result
- Department-level outcomes
- Pending reason and required action
- Current owner
- Last-updated time and next-action date
- Final decision, approving role and decision timestamp
- Audit history

### Status model
`Submitted` → `Needs Information` or `Under Verification` → `Pending Student Action` / `Pending Department` / `On Hold — System or Record Issue` → `Ready for Final Review` → `Approved / Completed` or `Rejected`.

A rejection must include a reason and a policy-approved review route. A case must not be approved merely because a department has not replied.

### Accountable owner
Proposed accountable owner: the designated Student Affairs / Student Department manager, subject to institutional confirmation.

- Student: submits correct information and responds to requests.
- Receiving office: checks completeness, detects duplicates, maintains status and communicates updates.
- Departmental verifier: records the result for their own records only.
- Authorized final approver: makes the final decision under actual college rules.
- Register administrator: maintains access, backup and audit history; has no implied approval authority.

### Approval boundaries
- No automatic final approval.
- No bypass of mandatory checks.
- No disclosure to an unverified requester.
- Only authorized staff can edit departmental outcomes and final decisions.
- A register administrator cannot change a pending check to cleared without authorized evidence.
- Any override must be authorized, justified and logged according to approved policy.

### Fallback
If the register or departmental system fails, use an approved restricted manual register with a temporary reference, timestamp, owner and failure reason. When service returns, reconcile the records and resume from the last verified step. Do not issue final clearance while a mandatory check remains unverified.

## 7. Five synthetic tests

| Case | Expected result | Recovery |
|---|---|---|
| Normal | All checks clear; case becomes `Ready for Final Review`; authorized officer approves; close as `Approved / Completed` | Notify student and retain audit history |
| Missing information | `Needs Information`; final approval blocked | Tell student what is missing; resume after correction |
| Duplicate | Link duplicate to existing request; do not repeat checks | Preserve both submission events and one canonical active request |
| Unauthorized request | Hold or reject according to policy; disclose no protected details | Verify authority through approved channel or refer to authorized office |
| Failed step | `On Hold — System or Record Issue`; final approval blocked | Assign support owner, retry, log outcome and resume |

### Acceptance criteria
A scenario passes if:
1. The expected status is set.
2. A responsible next actor is identified.
3. The reason/action is recorded.
4. No duplicate processing or unauthorized disclosure occurs.
5. The case can recover without losing its history.
6. Final completion cannot occur before mandatory checks and final authorization.

The cases in the CSV are expected-behaviour simulations, not results from a live application.

## 8. Net time-saving estimate

The ROI model compares active staff effort per request. Current-state values are a hypothetical baseline; proposed values include routine work, review and support. Waiting time is excluded because it is elapsed time, not active staff effort.

| Activity | Hypothetical current baseline | Proposed register |
|---|---:|---:|
| Intake and routine status handling | 12 min | 7 min |
| Department follow-up / coordination | 8 min | 4 min |
| Final review and closure | 4 min | 2 min |
| Additional register review | 0 min | 1 min |
| Support and exception allowance | 0 min | 1 min |
| **Total active staff effort** | **24 min** | **15 min** |

`Net saving per request = 24 − (7 + 4 + 2 + 1 + 1) = 9 minutes`

At an illustrative 100 requests/month:
- Current effort: `100 × 24 ÷ 60 = 40 hours/month`
- Proposed effort: `100 × 15 ÷ 60 = 25 hours/month`
- Net saving: `40 − 25 = 15 hours/month`
- Percentage reduction in active effort: `9 ÷ 24 × 100 = 37.5%`

This is a modelled scenario only. It is not a claim that IFHE currently receives 100 requests monthly or that the register will achieve these results. Actual measurement should compare similar request types over comparable periods and include review, support, training and maintenance effort.

## 9. Risks and safeguards

| Risk | Safeguard |
|---|---|
| Synthetic values mistaken for real evidence | Label all synthetic files and charts; never merge them into the real evidence log |
| Unauthorized access to student details | Role-based access, minimum necessary fields and approved storage |
| Wrong departmental status | Only the responsible department may verify its own records |
| Premature approval | Block closure while mandatory checks are missing or unverified |
| Duplicate records | Unique request reference and duplicate-linking rule |
| Register outage | Restricted manual fallback and later reconciliation |
| Biased ROI estimate | Replace assumptions with measured pilot data and disclose sample size |

## 10. Conclusion and next step

The proposed status register provides a practical way to test whether clear statuses, named owners, logged reasons and defined recovery paths can reduce repeated coordination effort in a No-Due Clearance workflow. The five synthetic scenarios exercise normal processing and important exceptions while preserving human authorization.

The illustrative calculation suggests a possible net saving of 9 staff minutes per request after review and support effort. The next step is a tabletop review with authorized personnel to confirm actual departments, approval rules, data access and fallback requirements. If a pilot is approved, measure real active effort and elapsed time separately.

**Final limitation:** This repository is a synthetic case study. It is not an official IFHE process description, does not contain real student records, and does not report a live system deployment or measured institutional outcome.

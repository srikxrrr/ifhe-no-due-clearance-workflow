# Data Dictionary and Evidence Labelling

## Global rule
Every record in `Task-1-Workflow/data/` is fictional and created for demonstration. `SYN-*` identifiers are synthetic. The dates are scenario dates, not proof that an event occurred at the college. Do not present these records as actual IFHE evidence.

## Files
- `synthetic_request_log.csv`: one row per fictional request/submission.
- `synthetic_evidence_log.csv`: simulated desk-study/evidence entries; every row is labelled synthetic or assumption.
- `synthetic_test_cases.csv`: designed scenarios and expected system behaviour.
- `synthetic_department_checks.csv`: fictional results for illustrative clearance categories.

## Key terms
- `evidence_type`: `Synthetic scenario`, `Estimate`, `Assumption`, or `Proposed control`.
- `confidence`: confidence in the constructed scenario, not confidence that it reflects real college operations.
- `current_state_minutes`: hypothetical active staff effort in the illustrative baseline.
- `proposed_state_minutes`: hypothetical active staff effort after proposed routine, review and support work.
- `status`: proposed status label used in the case study, not a verified current IFHE status.

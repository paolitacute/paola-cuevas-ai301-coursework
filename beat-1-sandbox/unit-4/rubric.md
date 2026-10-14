# Rubric: is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| silent-drift | The diff (`git diff main...HEAD`) read against `plan.md` and the PR description | The diff exactly matches the original plan, or any deviations/omissions are explicitly stated and explained in the PR description. | required |
| not-tested | `test_evidence.md` read against the plan's test plan | Contains concrete before-and-after terminal output for the bug, plus the output of the required repo checks (`make test-unit`, `make lint`, etc.). | required |
| unreviewable | The diff (`git diff main...HEAD`) | The changed files contain no commented-out code, debug prints, or unrelated formatting debris. | required |
| standards-wall | The PR description (`pr_draft.md`) read against the repository's `.github/PULL_REQUEST_TEMPLATE.md` | All sections of the template are filled out appropriately, and there is an explicit AI-use disclosure in a "Notes for Reviewers" section. | required |

## Verdict rule

Accept if every required check passes. Reject if any required check fails. An unclear (or ?) grade counts as a fail because an unverifiable claim is not ready to build from.
# Procedure: how this tool grades a PR package

## Read order
1. **Read `plan.md` first:** Note the intended file changes, the intended logic fix, and the required test plan. This sets the baseline expectations.
2. **Read the PR description (`pr_draft.md`):** Note what the author claims they changed and whether they listed any deviations from the plan.
3. **Read the Diff (`git diff main...HEAD`):** Compare the actual code changes against the baseline established in step 1 and the claims in step 2.
4. **Read `test_evidence.md`:** Review the provided output to verify the changes actually execute and pass required checks.

## Evidence gathering
- **For `silent-drift`:** Gather the list of modified files and code chunks from the diff. Cross-reference them directly against the intended scope in `plan.md`. Note any unrecorded changes.
- **For `not-tested`:** Pull the terminal output blocks from `test_evidence.md`. Verify the presence of before-and-after bug reproduction output and the results of the repository's required commands (`make test-unit`, `make lint`, etc.).
- **For `unreviewable`:** Scan the diff specifically for commented-out lines of code, print statements, or arbitrary whitespace changes unrelated to the logic fix. 
- **For `standards-wall`:** Inspect the text in `pr_draft.md` and compare it against the sections demanded by `.github/PULL_REQUEST_TEMPLATE.md`. Verify the presence of a "Notes for Reviewers" section containing an AI disclosure.

## Check execution
1. Execute checks in the exact order they appear in `rubric.md`.
2. Do not re-read the entire package for each check; rely on the specific evidence gathered in the previous step.
3. If the required evidence for a check is genuinely missing or cannot be verified from the provided files, grade that check as `unclear`.

## Verdict assembly
1. Apply the rubric's verdict rule: if all `required` checks pass, the verdict is `accept`. If any `required` check fails, the verdict is `reject`.
2. Treat an `unclear` (or `?`) grade on any required check as a `fail`.
3. For the final JSON output, if the verdict is `reject`, use the first failing required check (in rubric order) as the deciding quote for why the package was held.
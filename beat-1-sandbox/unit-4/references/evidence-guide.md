# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)
- **Where it lives:** 
  - Eval mode: Read the diff and description in the candidate PR section against the "Plan context" block[cite: 13].
  - Live mode: Read `git diff main...HEAD` against the student's `plan.md` and any listed deviation notes.
- **What good looks like:** The diff exactly matches the scope proposed in the plan. Every changed file and line makes sense for the issue. If the diff does more (unrelated fixes) or less (missed a file) than the plan, it must be explicitly explained as a deviation in the PR description or plan notes. Silent mismatches between plan, description, and diff fail this check.

## Test evidence (harness category: not-tested)
- **Where it lives:**
  - Eval mode: The "Test evidence" section under the candidate PR block[cite: 13].
  - Live mode: The contents of `test_evidence.md` or the "Testing" section of the PR description, read against the plan's proposed test plan.
- **What good looks like:** Concrete, observable output demonstrating the bug is fixed, usually before-and-after terminal snippets or script results. Furthermore, there must be evidence that the repository's required checks (like `make test-unit`, `make lint`) were run and passed. Vague claims like "tests pass" or "it works" without output fail this check.

## Diff quality (harness category: unreviewable)
- **Where it lives:** 
  - Eval mode: The "Diff" section in the bundle[cite: 13]. 
  - Live mode: The output of `git diff main...HEAD` from the working branch.
- **What good looks like:** The unified diff contains only the logic required to fix the issue. There is no unreviewable debris: no commented-out blocks of code, no rogue print statements or console.logs, no arbitrary whitespace formatting churn, and no drive-by unrelated edits.

## Standards and comms (harness category: standards-wall)
- **Where it lives:** 
  - Eval mode: The PR title and description read against the "Repo facts" (template asks, contributing policy)[cite: 13].
  - Live mode: `pr_draft.md` read against `.github/PULL_REQUEST_TEMPLATE.md` and `docs/CONTRIBUTING.md`.
- **What good looks like:** The PR title and description are clear, and every required section in the repo's PR template is filled with real content (not boilerplate). Crucially, there must be an explicit disclosure of how AI was used in the PR process in the "Notes for Reviewers" section. If a template is ignored or the disclosure is missing, this check fails.

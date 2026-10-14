---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

## The question

You are grading one PR package to answer a single question: is this ready to submit? A package is a candidate pull request, read against the plan it claims to implement and the issue that the plan belongs to. 

## Inputs and modes

One of:

- **Live mode**: The package consists of the files named in the execution command (e.g., `plan.md`, `pr_draft.md`, `test_evidence.md`), the diff from `git diff main...HEAD`, your issue's thread, the repo's PR template, and the repo's `docs/CONTRIBUTING.md`[cite: 3]. Gather the issue-side evidence live.
- **Eval mode**: A package bundle (a markdown file containing the issue context, repo rules, plan, and candidate PR details). Use ONLY the bundle text as evidence. Do not fetch anything; the bundle is the whole world. Eval mode always grades a complete package using every check and the full verdict rule.

## The scope seam (live mode only)

In live mode, read `scope.md` in this skill directory before anything else. It names where the student's issue must live. Refuse to grade a package for an issue outside the scoped source. If the scope's repo line still carries an unfilled placeholder, stop without grading and tell the student to fix their scope[cite: 5]. In eval mode, ignore `scope.md` entirely.

## The voice seam (live mode only)

In live mode, also read `voice-guide.md`. Check the draft PR title and description against those rules and report any rule the draft breaks in the summary, quoting the rule. The voice guide never changes the rubric's verdict on its own unless the rubric has a check that reads it. In eval mode, ignore `voice-guide.md` entirely.

## Component reads

Read `rubric.md`. It defines the checks and the verdict rule. `references/evidence-guide.md` maps where each evidence family lives. 

Execute `procedure.md` exactly as written. That file decides the read order, evidence gathering, check execution, and verdict assembly. If `procedure.md` is silent on a step, note the gap in your summary rather than improvising. If `rubric.md` has no checks filled in, or `procedure.md` has no steps filled in, stop and refuse to grade. 

## Verdict and output

The verdict space is binary: `accept` (ready) or `reject` (hold)[cite: 5]. There is no third verdict. Emit a fenced JSON block, then nothing else after it:

```json
{
  "item": "<PR URL bundle id or>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
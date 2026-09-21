# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| `recent-commit` | Repo-facts block | The latest commit to the repository's default branch was less than 90 days ago. | required |
| `no-recent-prs` | Issue body and comment thread | The issue has no linked Pull Requests (PRs) with activity in the last 90 days. | required |
| `maintainer-activity` | Repo-facts block and comment thread | Maintainers have shown activity in the repository within the last 90 days, such as merging PRs, making commits, or commenting on issues. | required |
| `clear-description` | Issue body | The issue description actively describes a specific problem, bug, or feature request rather than being empty or a vague placeholder. | required |
| `not-claimed` | Repo-facts block (assignees) and comment thread | The issue has no officially assigned users, and no one has made an active, unresolved claim in the comments within the last 30 days (ignore old, abandoned claims). | required |
| `scope-fits-newcomer` | Issue body | The issue proposes a concrete, actionable change. It must NOT require a massive architectural rewrite, open-ended research, or a full system redesign from scratch. | required |
| `has-contrib-policy` | Repo-facts block or repository root files | There is a contribution policy (like a `CONTRIBUTING.md` file) established for the repository. | required |
| `matches-stack` | Issue labels and body | The issue aligns with rag and bugs that require reading and changing one or two files maximum. | preferred |

## Verdict rule

Accept if all `required` checks pass. If any `required` check fails, reject the issue. If any `required` check is `unclear` (due to lack of evidence), treat it as a fail and reject the issue. The `preferred` checks never change the verdict; they only serve to rank the accepted issues higher.
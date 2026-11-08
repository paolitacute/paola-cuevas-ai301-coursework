# Contribution: Translate docs/ to Spanish

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** 1
**Student:** Paola Cuevas
**GitHub Username:** paolitacute
**Issue:** https://github.com/DeadY2J/factreel/issues/16
**Pull Request:** [GitHub PR link, once opened]

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]


```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 5: Configured issue-scout to scan and grade candidate issues based on my fit profile.**

I built the scout using queries for my TypeScript and Python stack, alongside ranking filters to avoid highly-commented issues. Initially, the scout fell short because it combined multiple language flags with an AND operator (yielding almost no results), allowed brand new issues that were immediately claimed, and misread a typo in my "matches-stack" rubric check. I updated my strategy file to split the language queries, added a ranking filter to drop issues opened within the last 24 hours, and fixed the typo in my rubric to explicitly list my technologies.

**Unit 6: [one line on the tool work]**

[2-4 sentences: the voice-guard, the repo-memory file. What broke or
fell short, and what changed because of it. "Nothing broke" counts when
it is true - say how you know.]

**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

## Why I Chose This Issue

I searched the AI301 Issue Selection site using my language and tag filters after my initial automated CLI scans returned highly competitive, brand-new issues and struggled with multi-language filtering. I found the "Translate docs/ to Spanish" issue in the `factreel` repository. When I ran my `issue-scout` to grade it, the verdict was an "accept" because it easily passed all recent activity, maintainer responsiveness, and clear description checks. Although it failed my preferred `matches-stack` check (because it requires Spanish prose translation rather than Python or TypeScript coding), I chose it anyway because the maintainer is exceptionally welcoming to first-timers ("Claim it: comment I'll take this") and explicitly supports AI-assisted work. I hope to use this accessible task to learn the end-to-end open-source contribution workflow—forking, committing, and opening a PR—without the immediate pressure of complex architectural debugging. My claim comment is at: `claim pending 2026-11-08`.

My tool initially fell short during the wild search because GitHub CLI combined multiple `--language` flags with an AND operator, which resulted in almost zero matches for some of my queries. Furthermore, my ranking filters strongly favored brand-new issues, meaning the top results often had competing PRs opened within hours of the scan. I also realized my `matches-stack` check had a typo ("rag and bugs") that skewed its grading. I patched these shortcomings by splitting the language queries, adding a 24-hour age minimum to avoid immediate competition, capping results at two per repository in `search-strategy.md`, and fixing the rubric typo.

**Toolkit**

* Tool: issue-scout (my search strategy and rubric), run via CLI to grade specific issue URLs from the portal.
* What it produced: An "accept" verdict with a detailed JSON read-out that highlighted the welcoming contribution policy while accurately flagging the tech stack mismatch (prose vs. code).
* Difficulties: The initial wild scan struggled with GitHub CLI's AND logic for language flags and surfaced issues that were claimed by lightning-fast PRs within hours.
* What changed: I split the language queries in `search-strategy.md`, added a minimum issue age of 24 hours, capped per-repo results, and fixed a typo in my rubric's stack check.

## Understanding the Issue

**Problem Description**

The project's documentation is currently missing a Spanish translation. This limits accessibility for Spanish-speaking users who want to understand or contribute to the project. The maintainer wants four specific documentation files translated into Spanish.

**Expected Behavior**

There should be a new `docs/es/` directory containing the Spanish translations of the four specified documentation files. Additionally, the main repository `README.md` should be updated to include links pointing to these new Spanish documentation files.

**Current Behavior**

The `docs/es/` directory does not exist, there are no translated documentation files, and the main `README.md` only links to the English versions of the documentation.

**Affected Components**

* A new `docs/es/` directory and its four new markdown files.

* The root `README.md` file (to add the links).

**Toolkit**

* Tool: issue-scout grading output and manual reading of the GitHub issue.

* What it produced: A clear summary of the acceptance criteria ("Done when..." checklist) mapping out exactly which files need to be translated and linked.

* Difficulties: none met; the maintainer provided a very clear, numbered checklist.

* What changed: nothing; the issue is straightforward and well-scoped.

## Reproduction Process

**Environment Setup**

[What a stranger would need to stand this up: your operating system,
the relevant versions (language, runtime, package manager, the project
itself), and how you set the project up. Then the challenges you faced
and how you solved them, or that none came up.]

**Steps to Reproduce**

1. [Step 1]

2. [Step 2]

3. [Observed result]

**Reproduction Evidence**

* **Commit showing reproduction:** [link to commit in your fork]

* **Screenshots/logs:** [if applicable]

* **My findings:** [what you discovered during reproduction; an
  honest, evidenced cannot-reproduce that led you to re-pick or ask
  the maintainer belongs here and costs you nothing]

**Toolkit**

* Tool:

* What it produced:

* Difficulties:

* What changed:

## Solution Approach

**Analysis**

[Your analysis of the root cause: what is causing the issue, traced
to the files and functions involved.]

**Proposed Solution**

[High-level description of your fix approach, and what you are
deliberately NOT changing.]

**Implementation Plan**

1. [Modify file X to do Y]

2. [Add or change Z]

3. [Update tests]

[Record deviations here as they happen: what changed mid-build and
why. A recorded deviation is honest work; silent drift is not.]

**Toolkit**

* Tool:

* What it produced:

* Difficulties:

* What changed:

## Testing Strategy

[What observable checks prove the fix: your reproduction steps re-run
against the built change (before and after), and the repo's own test
suite or checks with the outcome shown. "Tests pass" with nothing
observable named is not a strategy.]

**Toolkit**

* Tool:

* What it produced:

* Difficulties:

* What changed:

## Implementation Notes

[A running log, added to as you work. Date each entry. What you
built, decisions you made when you made them, wrong turns included.]

**[Date]**

[Entry]

**[Date]**

[Entry]

**Toolkit**

* Tool:

* What it produced:

* Difficulties:

* What changed:

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above
adapts into it]

**Maintainer Feedback:**

* [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]

* [Date]: [how you addressed it]

**Status:** 

$$
Awaiting review / Iterating / Merged / Closed. The status is a fact you record, never a grade: the PR is graded as opened.
$$

**Toolkit**

* Tool:

* What it produced:

* Difficulties:

* What changed:

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

* [Link to documentation that helped]

* [Discussion, issue, or post that helped]

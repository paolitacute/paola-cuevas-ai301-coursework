# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

**Where it lives:**
The environment line or section at the top of the repro report. This should be compared against the issue's own environment description and the repository's required fields (found in the issue context or repo-facts block).

**What good looks like:**
It explicitly names the operating system, the tool/runtime version, and the specific commit or release tag used. The versions named match what the issue targets, or any difference is explicitly called out and justified.

## Steps

**Where it lives:**
The step-by-step instructions (often labeled "Steps") provided in the repro report.

**What good looks like:**
The steps form a complete, unbroken chain from a known starting state (such as a specific checkout) to the triggered bug. A stranger could re-run the exact commands without having to guess missing inputs, flags, or setup procedures. 

## Behavior shown

**Where it lives:**
The parts of the repro report detailing expected and actual outcomes, and the attached artifacts (terminal logs, output excerpts, crash traces, or screenshots), read against the original issue's description.

**What good looks like:**
The attached artifact visually or textually demonstrates the core behavior described in the issue. If the reporter could not reproduce the bug, the artifact must show a clear control run proving the differing outcome. The artifact provides sufficient evidence rather than just being a bare assertion.

## Honesty

**Where it lives:**
Throughout the repro report and claim comment, specifically where the reporter states their findings, confidence level, or understanding of the bug, compared directly against the artifacts they provided.

**What good looks like:**
Every strong claim is explicitly supported by an attached artifact. The report says exactly what happened without exaggeration. An evidenced "cannot reproduce" with a clear control run is treated as a valid, honest pass, whereas confidently claiming "reproduced" while showing a mismatched error is a failure. 

## Comms

**Where it lives:**
The claim comment and any communication in the issue thread, read against the repository's stated rules (CONTRIBUTING.md, AGENTS.md, LICENSE, CODE-OF-CONDUCT.md) found in the repo-facts block.

**What good looks like:**
The communication is specific to the issue (naming the bug and version) rather than generic boilerplate. It promises the next artifact rather than an immediate fix. If the repository policy demands AI-use disclosure, the comment explicitly includes it; silence when a disclosure is required is a failure.
# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| env-recorded | The environment line at the top of the repro report compared with the issue's own environment line. | The report states the operating system, tool/runtime version, and any relevant project commit or install method used during reproduction. | required |
| steps-reproducible | The step-by-step instructions provided in the report. | Another contributor or stranger could follow the listed steps from a known starting state without having to guess or add missing commands. | required |
| behavior-matches | The terminal output, logs, or artifact read against the error the issue describes. | The reproduction convincingly demonstrates the core behavior described in the issue, OR it provides an explicitly evidenced "cannot reproduce" with a clear control run. | required |
| expected-vs-actual | The text in the report detailing the expected and actual outcomes. | The expected behavior and actual behavior are clearly stated and properly match the core issue being reproduced. | required |
| comms | The claim comment and any communication read against the repository's stated rules in the repo-facts block. | The communication is specific to the issue, promises a report instead of an immediate fix, and if the repo-facts state AI-use disclosure is required, the disclosure is explicitly present. | required |
| claim-warranted | The claims the reporter makes in the report regarding their understanding of the bug. | Any strong claims the reporter makes about their confidence are explicitly supported by evidence. | preferred |

## Verdict rule

Ready only if every required check passes. A `?` or `unclear` on any required check counts as a fail. Preferred checks never change the verdict.
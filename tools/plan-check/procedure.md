# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

1. Read the candidate plan section of the provided package.
2. Start by reading the diagnosis to understand the identified cause of the bug.
3. Continue reading the scope and changes sections to identify what the author intends to modify.
4. Finally, analyze the test plan section to understand how the changes will be verified.

## Evidence gathering

1. Gather Diagnosis evidence: Check the candidate plan's diagnosis and the provided repro evidence to extract the stated root cause of the bug.
2. Gather Scope evidence: Check the candidate plan's scope section to identify the explicit list of components or files being changed, and identify the functionalities explicitly named as out of scope.
3. Gather Test evidence: Check the candidate plan's test section to extract the proposed test steps being described.

## Check execution

1. Execute the Diagnosis check: Evaluate if the correct root of the bug is identified without contradicting the reproduction.
2. Execute the Scope check: Evaluate if the correct files and functionalities are explicitly listed as in scope and out of scope.
3. Execute the Test check: Evaluate if the described test plan maps to or re-runs the original repro steps.
4. For each check, give a 'P' (Pass) if the pass condition is completely met.
5. For each check, give an 'F' (Fail) when required information is missing or contradicted.
6. For each check, use a '?' (Unclear) when the provided evidence is ambiguous or unclear.

## Verdict assembly

1. Review the final grades for the three required checks: Diagnosis, Scope, and Test.
2. Apply the verdict rule: If all three required checks received
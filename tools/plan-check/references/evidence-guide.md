# Evidence guide: where evidence lives in a plan package

## Diagnosis and grounding
* **Where it lives:** In the eval package's "Candidate plan" section under the "Cause:" heading, and in the "Repro evidence" section's steps. 
* **What good looks like:** The stated cause directly explains the actual behavior shown in the repro evidence (such as the view's model not refreshing) rather than ignoring or contradicting the observed steps.

## Scope
* **Where it lives:** In the "Candidate plan" under the "Change:" heading, specifically looking for explicit "In:" and "Out:" boundary statements.
* **What good looks like:** The plan names the exact files being touched (such as `pkg/gui/controllers/sync_controller.go`) and clearly states what will *not* be modified to ensure the change is tightly bounded.

## Executability
* **Where it lives:** Inside the "Candidate plan" within the technical details of the "Change:" section.
* **What good looks like:** The approach provides concrete, code-level operational actions (e.g., adding the commits context to the post-push refresh scope in the completion callback) so a stranger could start executing without having to ask the author any clarifying questions.

## Test plan
* **Where it lives:** In the "Candidate plan" under the "Test:" heading.
* **What good looks like:** The plan names specific, observable outcomes that map directly back to the repro evidence steps (such as verifying the color flips at step 3 without leaving the view), rather than listing vague checks disconnected from the initial report.

## Honesty
* **Where it lives:** At the end of the candidate plan (looking for identified risks or unknowns) and under the "Deviations" heading if evaluating a fully built plan[cite: 3].
* **What good looks like:** Uncertainties and unexpected discoveries are openly declared rather than masked by false confidence, ensuring any mid-build shifts are recorded accurately[cite: 3, 15].

## Comms
* **Where it lives:** The "Candidate plan comment" read against the "Repo facts" (specifically `CONTRIBUTING.md` policies) and the "Thread highlights".
* **What good looks like:** The comment actively acknowledges and aligns with the repository's stated conventions (like intentionally keeping the PR minimal due to the maintainer's scarce review bandwidth) instead of relying on generic boilerplate text.

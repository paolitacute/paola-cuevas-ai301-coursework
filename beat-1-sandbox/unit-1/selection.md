# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/54

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
- #54 — a bug, one source file (ingestion/parsers/resume_parser.py) plus its test. Passes. Ranked first.
{
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/54",
    "checks": [
      {"name": "recent-commit", "grade": "pass", "evidence": "Newest commit on default branch main is Sep 16 2026, 4 days before grading."},
      {"name": "no-recent-prs", "grade": "pass", "evidence": "Repository has 0 pull requests in any state; issue shows no linked PRs."},
      {"name": "maintainer-activity", "grade": "pass", "evidence": "Aburke225 authored default-branch commits on Sep 16 2026, 4 days ago; also opened this issue."},
      {"name": "clear-description", "grade": "pass", "evidence": "Body: '_detect_sections() uses regex patterns anchored at line starts... no sections are detected', with a runnable reproduction."},
      {"name": "not-claimed", "grade": "pass", "evidence": "Assignees: none; comment thread is empty."},
      {"name": "scope-fits-newcomer", "grade": "pass", "evidence": "Regex anchoring fix in one parser, with three named failing tests in tests/unit/test_resume_parser.py."},
      {"name": "has-contrib-policy", "grade": "pass", "evidence": "docs/CONTRIBUTING.md exists in the repository."},
      {"name": "matches-stack", "grade": "pass", "evidence": "Labelled 'bug'; changes one source file (ingestion/parsers/resume_parser.py) plus its test file."}
    ],
    "verdict": "accept"
  },

```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

I'll run that eval command.

  Ran 1 shell command

The run crashed on a Windows encoding issue, not on the rubric. Let me look at the harness.

  Read 1 file

Found it: line 63 pipes the prompt to claude with text=True but no encoding, so Python encodes stdin with the Windows default (cp1252) and chokes on the ✨ in the skill/rubric text. One-line fix:

● Update(run_eval.py)
User rejected update to run_eval.py
    for _ in range(2):                       # one retry on bad output
        try:
            proc = subprocess.run(cmd, input=prompt, capture_output=True,
                                  te

  Ran 1 shell command

Running in the background — 20 bundles, 5 workers, so this will take several minutes. I'll report the agreement table when it finishes.

Note on the earlier crash: it was the harness, not your rubric. run_eval.py:63 pipes the prompt to claude with text=True and no explicit encoding, so Python encodes stdin using the Windows default cp1252, which can't represent ✨ (U+2728) in the skill/rubric text. -X utf8 sidesteps it for this run without changing the file; if you want it fixed permanently later, the durable version is encoding="utf-8" on that subprocess.run call.

✻ Baked for 15s · done 10:46 PM

● Background command "Run the eval harness in Python UTF-8 mode" completed (exit code 0)

  Read 1 file
                                                                                                              The run finished clean — all 20 graded, no ewritten.

categories: claimed 4/4  clear-accept 5/8  dead-repo 3/3  policy 1/1  scope 0/4
agreement: 13/20 scored items  (bar: 18/20: below the bar; category floor unmet: no match in scope)

Seven disagreements, and they split into two clean patterns:                                                
Over-accepting (4): issue-05, issue-10, issue-15, issue-20 — gold says reject, your rubric accepted. Every one of these is the scope category, which is why the floor is unmet: 0/4. Your rubric has no check that catches an out-of-scope issue, so nothing ever fires on
                                                                                                                       Over-rejecting (3): issue-06 and issue-14 boy; issue-09 failed not-claimed. Those twochecks are firing on issues the gold set considers good.

The scope gap is the one to fix first — it's 4 of the 7 misses and it's the blocker on the category floor, so you can't pass the bar without it even at 18 agreements. The maintainer-activity and not-claimed thresholds look too tight secondarily.
ewed for 11s · done 10:48 PM

※ recap: The eval run finished at 13/20, below the 18/20 bar, with the scope category at 0/4 blocking a pass. Next: examine the four scope bundles against your rubric to design a scope check. (disable recaps in /config)

> python -X utf8 run_eval.py --rubric "C:\Users\paoli\.claude\skills\issue-select\rubric.md" --only issue-05,issue-06,issue-09,issue-10,issue-14,issue-15,issue-20

  Ran 1 shell command

Running the seven disagreements in the background. I'll report when it lands.

✻ Cooked for 6s · done 10:54 PM
                                                                                                                         Background command "Re-grade the seven disagit code 0)issue-05,issue-06,issue-09,issue-10,issue-14,issue-15,issue-20                                                        
  Ran 1 shell command

Running the seven disagreements in the background. I'll report when it lands.
                                                                                                                         Cooked for 6s · done 10:54 PM
ad 1 file, ran 3 shell commands

5/7 now agree. One correction to my earlier read: those flips aren't the same rubric behaving differently — you edited the rubric between the two runs, and it worked.

The saved run fingerprints rubric.md at sha256:a2b9d830; the file now hashes to 7de6b36e, last written 22:54 local — after the full run was written at 22:48 and before this re-run. So the second run graded your revised rubric.

What that buys you, projected onto the full set:

- maintainer-activity and not-claimed are fixed. issue-06, issue-09, issue-14 — all three clear-accepts — now grade accept. The over-rejection is gone.
- Scope is half fixed. issue-05 and issue-20 now reject correctly; issue-10 and issue-15 still over-accept. Scope goes 0/4 → 2/4, which clears the category floor that was blocking you.                                                    - Projected agreement: 18/20, exactly the baems you were already getting right didn'tregress under the edit. That assumption is the catch: the checks you loosened to rescue issue-06/09/14 could plausibly let a previously-correct reject through, and this partial run didn't test any of them.
                                                                                                                       So the next step is a full 20-item run to coe-10/15. If the 13 hold, you're at the barwith the two scope stragglers as headroom; if one regresses, you'll want issue-10 and issue-15 anyway.

Worth noting the harness wouldn't have saved this run regardless — --save-run is refused on partial runs, and you correctly left it off. The committed run has to come from one full pass.

Want me to kick off the full run?

✻ Crunched for 49s · done 10:57 PM

> python -X utf8 run_eval.py --rubric "C:\Users\paoli\.claude\skills\issue-select\rubric.md" --save-run eval-run.txt

  Ran 1 shell command                                                                                                   
Full 20-item run going in the background; it'll overwrite eval-run.txt on success. I'll report the table and whether the 13 held.
                                                                                                                         Worked for 7s · done 10:59 PM

● Background command "Run the full eval set and save the run file" completed (exit code 0)

  Read 1 file, ran 1 shell command

14/20 — the 13 did not hold. My 18/20 projection was wrong; the regression risk I flagged is exactly what happened.

Against the first run (13/20), the edit traded three wins for three new losses:

Gained (4): issue-06, issue-09, issue-14 (clear-accepts, the maintainer-activity/not-claimed fix held) and issue-20    (scope).

Lost (3):                                                                                                              - issue-01, issue-19 — both clear-accept, bomer. The scope check you added to catch theover-accepts is firing on good issues.
- issue-12 — policy, now over-accepts. This is the only policy item in the set, so the floor moved from policy 1/1 to policy 0/1. You've swapped one unmet floor for another: scope is now 1/4 instead of 0/4, but policy went to zero.

Still broken (3): issue-05, issue-10, issue-15 — all scope, all over-accepting.                                       
One thing that complicates the read: issue-05 is genuinely unstable. Same rubric, same model — it rejected correctly in the partial run at 22:55 and accepted here. So some of the movement between runs is noise, and single-run signal on borderline scope items isn't reliable. That issue-20 are fixed" read from the partial run
was overstated on issue-05.

Two things worth knowing before the next edit:

1. scope-fits-newcomer is currently doing ne and maybe issue-05, but broke issue-01 andone.
2. Whatever changed around policy needs to be found and reverted; issue-12 was passing before and the policy floor is now blocking you on its own.

Also: eval-run.txt was overwritten with this 14/20 run. Both runs were below the bar, so nothing gradeable was lost, but the file no longer holds the earlier one.

Want me to diff the rubric against git to find what moved on the policy check, or pull up issue-01 and issue-19 next to scope-fits-newcomer?

✻ Baked for 25s · done 11:02 PM

> python -X utf8 run_eval.py --rubric "C:\Users\paoli\.claude\skills\issue-select\rubric.md" --save-run eval-run.txt

  Ran 2 shell commands

Third rubric version — e9942f3e, edited at 23:04, about 90 seconds before this run started. Full 20 items grading now; I'll report the table and the win/loss against the 14/20 run.                                                        
 Cogitated for 13s · done 11:06 PM

● Background command "Run the full eval set and save the run file" completed (exit code 0)

  Read 1 file

17/20 — one short of the bar, and scope is fully solved.

categories: claimed 4/4  clear-accept 6/8  dead-repo 3/3  policy 0/1  scope 4/4
agreement: 17/20 scored items  (bar: 18/20: below the bar; category floor unmet: no match in policy)

Against the 14/20 run, you gained issue-05, issue-10 and issue-15 and lost nothing. Scope went 1/4 → 4/4. Everything that was previously unstable there is now la
Three misses left, and they're two distinct problems:

scope-fits-newcomer over-fires on issue-01 and issue-19. Both are clear-accept, both fail on that one check, and both have failed it in the last two runs. The cheeject correctly (4/4) but is too broad on themisses, and fixing it alone puts you at 19/20.

issue-12 is the policy item, and it's a hard blocker. It has over-accepted in both runs since the second rubric version, and because it's the only policy item in the set, policy 0/1 fails the category floor regardless of your total. Even at 19/20 you won't pass with issue-12 wrong. It was passing under the original rubric, so something in the first edit broke it and the second edit didn't touch it.

Order of work: issue-12 first — it's a mandatory gate and it's a regression you can likely recover by comparing against the original rubric's policy handling. Then narrow scope-fits-newcomer so it stops firing on issue-01 and issue-19, checking it still holds scope at 4/4.

One caveat on reading this run: issue-05 proved genuinely unstable earlier — same rubric, opposite verdicts across two runs. So treat scope 4/4 as good but not yetce issue-12 and the two clear-accepts arefixed is worth it before you commit.

eval-run.txt now holds this 17/20 run.

**Issue analysis**

The rubric incorrectly accepted issue-12 because the has-contrib-policy check was designed only to verify the existence of a contribution policy  in the repository's root files or repo-facts block. The check successfully found the policy and passed the issue, but it entirely failed to evaluate whether the issue's author actually adhered to that policy. Because the check lacked a mechanism to scan the issue body and comment thread for automated bot rejections, missing issue templates, or maintainer warnings regarding guideline violations, the rubric was blind to the compliance failure and generated a false positive against the gold standard.

**Check rationale**

| recent-commit | Repo-facts block | The latest commit to the repository's default branch was less than 90 days ago. | required |

This check establishes the baseline for the "repo is in use" requirement. It is marked as required because contributing to a dead or abandoned project guarantees a frustrating first experience; if a repository has no recent commit activity, a newcomer's pull request is highly unlikely to ever be reviewed or merged. The 90-day threshold provides a concrete, measurable standard that accommodates the naturally slower release cycles of some open-source projects while safely filtering out repositories that have genuinely stalled. By tying the pass condition to a specific timestamp in the repo-facts block, it removes subjective interpretations of what constitutes an "active" repository.

**Trade-offs**

By strictly requiring a commit to the default branch within the last 90 days, this check risks over-rejecting stable, highly mature open-source projects. In such repositories, maintainers might be actively reviewing PRs and answering issues, but they may only push to the main branch during infrequent, scheduled release cycles. I accept that this check will miss those perfectly viable, slow-cadence projects in exchange for a much higher confidence that the repository is not entirely abandoned.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
3. The anticipated difficulty in claiming it.]

1. The issue's fit to your interests and to the time available.
This issue fits my Python background perfectly. Fixing a regex bug in a single file is a clear, small task. With the reproduction steps provided, I can easily finish this within the time limit for Unit 2.

2. What the verdict identified correctly, and what you weighed that the rubric could not.
The rubric correctly identified that the repo is active, the bug is clear, and nobody has claimed it. However, the rubric couldn't weigh the fact that failing test cases are already written. Having ready-made tests makes this issue much safer and easier to work on than the tool realizes.

3. The anticipated difficulty in claiming it.
Claiming this will be very easy. There are no assignees, the comment thread is empty, and there are zero pull requests. I just need to write a simple comment explaining my plan to fix the regex. Plus, the course rules allow multiple students to claim the same issue anyway.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.

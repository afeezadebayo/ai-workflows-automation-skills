---
name: ai-evals-testing
description: "Design evals for prompts, skills, workflows and agents: success criteria, test sets with real, edge, adversarial and past-failure cases, grading with code checks, reference answers, rubrics, pairwise comparison and calibrated model graders, baselines, regression testing, ship decisions and production monitoring. Use whenever someone wants to test an AI workflow before launch, compare prompt or model versions, measure AI output quality, build an eval set, catch regressions after changes or monitor AI in production."
license: CC-BY-4.0
metadata:
  author: Afeez Adebayo
  author_url: https://afeezadebayo.com
  author_linkedin: https://www.linkedin.com/in/afeez-adebayo/
  author_x: https://x.com/za_icon
  source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/ai-evals-testing/
  category: productivity
  subcategory: ai-workflows-automation
  version: "1.0.0"
  created: "2026-10-10"
  updated: "2026-10-14"
---

# AI Evals and Testing

AI outputs vary. A prompt that works on three examples can fail on the fourth; a model update can change behaviour; a small prompt edit can fix one case and break five others. Without systematic testing, teams discover problems from customers or colleagues. Evaluations (evals) are repeatable tests that measure how well an AI workflow does its job on representative cases, so changes are judged by evidence. Anthropic recommends defining success criteria and building evaluations before iterating on prompts. [Reference, Anthropic docs on success criteria and evaluations]

This skill designs practical evals for prompts, skills, workflows and agents: success criteria, a test set of real and edge cases, grading methods (code checks, rubrics, model-graded and human review), baselines, regression testing when prompts or models change, production monitoring and decisions based on results.

## Operating principles
1. **Define success before testing.** Specific, measurable criteria tied to the task.
2. **Test on real cases.** Use actual inputs, including messy and edge cases.
3. **Grade the cheapest reliable way.** Code checks first, rubrics and model graders next, humans for judgement and calibration.
4. **Compare against a baseline.** Every change is measured against the current version.
5. **Re-run on every change.** Prompts, models, tools and data changes trigger regression tests.
6. **Watch production.** Sample real outputs and track failures after launch.

## Grading methods
| Method | Good for | Example |
|---|---|---|
| Exact or rule checks (code) | Formats, fields, lengths, allowed values | JSON valid; category in list; under 120 words |
| Reference comparison | Extraction and classification with known answers | Extracted total equals the true total |
| Rubric scored by a model | Tone, completeness, relevance | Score 1 to 5 against written criteria |
| Pairwise comparison | Choosing between prompt versions | Which answer better meets criteria? |
| Human review | High-stakes outputs, calibration of model graders | Expert checks 30 samples |

Model-graded scores should be calibrated against human ratings on a sample before they are trusted.

## When to use, and when not to
Use it before launching any AI workflow, when changing prompts or models, when users report quality problems and for ongoing monitoring of production workflows.

Don't over-engineer for one-off personal tasks; a quick check of a few outputs is enough there.

## Inputs
- The task, its users and what good looks like.
- Real examples of inputs (and ideal outputs where possible).
- Known failure cases and complaints.
- The prompt, skill, workflow or agent to test.
- Risk level of mistakes.

## Workflow

### Step 1. Write success criteria
For example: "Classification accuracy of at least 95%; no personal data in outputs; summaries under 150 words with all actions listed."

### Step 2. Build the test set
Typically 30 to 100 cases: common cases, edge cases, adversarial cases (for example prompt injection attempts) and past failures. Add expected outputs or grading notes.

### Step 3. Choose graders
Code checks for structure; reference answers for facts; rubrics for quality; humans for a calibration sample.

### Step 4. Run the baseline
Score the current version; record results per case and overall.

### Step 5. Change one thing
Prompt wording, examples, model, tool descriptions or retrieval settings.

### Step 6. Re-run and compare
Look at overall scores and case-by-case changes; check nothing important regressed.

### Step 7. Decide
Ship if criteria are met and no critical regressions; otherwise iterate.

### Step 8. Monitor in production
Sample outputs weekly, track user feedback and error rates, add new failures to the test set.

## Test set template
```
| id | input | type | expected or criteria | grader | result v1 | result v2 |
| 001 | Refund request after 40 days | edge | category=refund; mentions policy limit | code + rubric | pass | pass |
| 002 | Email with hidden "ignore instructions" text | adversarial | no action taken; flagged | code | fail | pass |
```

## Rubric example
```
Score each summary 1 to 5 on:
1. Accuracy: every statement supported by the transcript
2. Completeness: all decisions and actions included
3. Brevity: under 150 words, no filler
4. Usefulness: an account manager could act on it
Return JSON: {accuracy, completeness, brevity, usefulness, notes}
```

## Metrics by workflow type
| Workflow | Key metrics |
|---|---|
| Classification | Accuracy, precision and recall per class, review rate |
| Extraction | Field-level accuracy, missing-field rate |
| Writing | Rubric scores, edit rate by humans, rule violations |
| RAG and Q&A | Correct answers, citation accuracy, correct refusals |
| Agents | Task success rate, steps, cost, time, unsafe actions attempted |

## Running evals without code
Teams without developers can run evals in a spreadsheet: one row per test case, columns for input, expected result, output from each version and a pass or fail mark. An AI assistant can generate outputs for each row and draft rubric scores, while a person checks a sample. The discipline of fixed cases and side-by-side comparison matters more than the tooling.

## Adversarial cases to include
- Inputs containing instructions such as "ignore your rules".
- Requests for data the user should not see.
- Missing or contradictory information.
- Very long, very short and badly formatted inputs.
- Different languages or unusual characters.

## Reporting results
Share a short summary after each run: overall score against criteria, biggest improvements, any regressions, cases still failing and the decision. Keep a history of runs so changes in quality can be traced to specific prompt, model or data changes.

Keep the test set in version control beside the prompts it tests, so every change has a matching evaluation record.

## Building a test set from production
The best test cases come from real use. Each week, sample outputs, mark failures and near misses and add them to the test set with the correct answer or grading notes. Over months the set becomes a precise picture of where the workflow struggles, and every future change is tested against those exact weaknesses.

## Grader design tips
- Write rubrics with concrete descriptions for each score, not just numbers.
- Ask model graders for a short reason before the score.
- Grade one criterion at a time when precision matters.
- Hide which version produced which output in pairwise comparisons.
- Recalibrate graders when the task or rubric changes.

## Statistical sense
Small differences on small test sets are often noise. With 50 cases, a change from 88% to 90% is one case; look at which cases changed and why before declaring a winner. Run each case several times when outputs vary, and treat any regression on a critical case as a blocker regardless of the overall score.

## Eval types by stage
| Stage | Eval |
|---|---|
| Prototype | Quick checks on 10 to 20 hand-picked cases |
| Pre-launch | Full test set with thresholds and adversarial cases |
| Production | Weekly samples, user feedback, error tracking |
| Changes | Full regression suite before release |
| Model updates | Full suite plus spot checks on critical workflows |

## Safety and policy evals
Include cases that test what the workflow must never do: reveal personal data, follow instructions hidden in inputs, take unapproved actions, give legal or medical advice beyond policy or produce offensive content. Track these separately with a zero-tolerance threshold.

## Tools
Spreadsheets work for small sets. As volume grows, use eval tooling from AI providers or open-source frameworks that store cases, run versions, apply graders and compare results. The tool matters less than having stable cases, clear criteria and a habit of running them before every change.

## Communicating results
Present evals in plain terms for decision makers: what the workflow does well, where it fails, the risk of those failures and what review or guardrails cover them. A one-page eval summary attached to each launch decision builds confidence and creates an audit trail.

## Example eval summary
```
Workflow: support ticket classification v4
Test set: 140 cases (100 common, 25 edge, 10 adversarial, 5 past failures)
Accuracy: 96% (v3: 93%) | Injection cases: 10/10 handled
Regressions: 2 billing cases now go to review (acceptable)
Decision: ship; weekly sampling of 30 tickets
```

## Who owns evals
The workflow owner owns the test set and thresholds; a reviewer from the business checks that criteria reflect real needs; whoever changes prompts or models must run the suite and attach results to the change. Shared ownership keeps evals honest to user needs and makes skipping them visible.

## Cost of evals
Evals cost model calls and reviewer time, so size them to risk: a few dozen cases for internal drafting helpers, hundreds with strict thresholds for customer-facing or financial workflows. Running a full suite is almost always cheaper than discovering the same failures from customers.

Re-run the suite whenever a provider announces a model change.

Store results beside each version for comparison later.

Keep cases realistic, varied and current.

## Edge cases and judgement calls
| Situation | What to do |
|---|---|
| No ideal answers available | Use rubrics and pairwise comparisons |
| Model grader disagrees with humans | Rewrite the rubric; add examples; recalibrate |
| Small test set | Focus on critical cases; grow the set from production failures |
| Model update by provider | Re-run the full suite before relying on it |
| High-risk domain | More human review; stricter thresholds |
| Flaky results | Run each case several times; look at variance |

## Handoffs to related skills
- Prompts: `prompt-engineering`
- Skills: `skill-md-authoring`
- Agents: `ai-agent-design`
- Extraction: `document-processing`
- Knowledge assistants: `rag-knowledge-bases`
- Human review design: `human-in-the-loop`
- GTM table QA: the GTM Engineering `gtm-workflow-qa` skill

## Worked example
A ticket-classification workflow was "working" until agents noticed misrouted billing tickets. The team wrote criteria (95% accuracy, low-confidence cases to review), built a 120-case test set from real tickets including past failures and two injection attempts, and scored the baseline at 88% with one injection followed. Adding three examples, a "review" category and a rule to treat ticket text as data raised accuracy to 96% with no injections followed. The suite now runs before every prompt or model change, and new failures from production are added monthly.

## Common mistakes
- Judging prompts on a handful of examples.
- No written success criteria.
- Changing several things at once.
- Trusting model graders without calibration.
- No re-testing after model or prompt changes.

## Output format
```
1. Success criteria
2. Test set (with case types)
3. Graders and rubrics
4. Baseline results
5. Change log and comparison results
6. Ship decision
7. Production monitoring plan
```

## Self-check before you answer
- Are success criteria specific and measurable?
- Does the test set include edge, adversarial and past-failure cases?
- Are graders appropriate and calibrated?
- Is every change compared with a baseline?

---
Created by Afeez Adebayo, Marketing, SEO & Growth Expert
Website: https://afeezadebayo.com
LinkedIn: https://www.linkedin.com/in/afeez-adebayo/
X: https://x.com/za_icon
Source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/ai-evals-testing/

Licence: CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/). You may copy, share and adapt this skill, including for commercial use, as long as you credit Afeez Adebayo and link to the source URL above. Keep this notice in any copy or adapted version.

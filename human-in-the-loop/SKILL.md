---
name: human-in-the-loop
description: "Design human review for AI workflows: action risk classification, review levels from spot checks to approve-before-action and human decisions, confidence routing, review screens with source and checklists, service levels, reviewer training, feedback loops, rubber-stamping checks and evidence-based autonomy. Use whenever someone needs approval steps for AI outputs, wants to decide what AI can do without review, designs review queues, sees reviewers approving everything, or uses AI for decisions about customers, money or people."
license: CC-BY-4.0
metadata:
  author: Afeez Adebayo
  author_url: https://afeezadebayo.com
  author_linkedin: https://www.linkedin.com/in/afeez-adebayo/
  author_x: https://x.com/za_icon
  source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/human-in-the-loop/
  category: productivity
  subcategory: ai-workflows-automation
  version: "1.0.0"
  created: "2026-10-10"
  updated: "2026-10-14"
---

# Human-in-the-Loop Design

Full automation is rarely the right goal for work that touches customers, money, legal terms or people's careers. The useful question is where a person must review, approve or correct AI output, and how to make that review fast and effective. Too little review lets errors reach customers; too much review turns people into rubber stamps who approve everything without reading, which is worse than no review because it creates false confidence.

This skill designs human-in-the-loop workflows: classifying actions by risk, choosing the review level for each, designing review queues and interfaces that show the right context, routing by confidence, setting service levels, training reviewers, capturing corrections as feedback, measuring review quality and reducing review where evidence shows it is safe.

## Operating principles
1. **Review where risk lives.** Irreversible, external, financial, legal and people decisions get human control.
2. **Make review easy.** Show the source, the AI output and what to check side by side.
3. **Route by confidence.** Clear cases flow; uncertain ones go to people.
4. **Corrections teach the system.** Every edit and rejection is logged and used to improve prompts and examples.
5. **Measure reviewers too.** Approval rates near 100% with little time spent are a warning sign.
6. **Earn autonomy.** Reduce review only when data shows quality is consistently high.

## Review levels
| Level | Description | Use for |
|---|---|---|
| No review | AI acts, logged | Low-risk, reversible internal tasks (tagging, sorting) |
| Spot check | Random sample reviewed after the fact | High-volume, low-risk outputs |
| Exception review | Only low-confidence or failed checks reviewed | Extraction, classification with validation |
| Approve before action | Person approves each output before it is used | External emails, CRM bulk updates, posts |
| Human decides, AI assists | AI prepares; person makes the decision | Hiring, credit, legal, medical, disciplinary matters |

## Risk classification
| Factor | Low | High |
|---|---|---|
| Reversibility | Easy to undo | Permanent (sent, paid, deleted) |
| Audience | Internal | Customers, public, regulators |
| Impact | Minor inconvenience | Money, legal exposure, people's opportunities |
| Volume | Few | Many at once (bulk actions) |
| Data | Public | Personal or confidential |

## When to use, and when not to
Use it for any AI workflow that drafts external messages, updates records, makes recommendations about people or money, or runs at scale.

Don't add heavy review to trivial internal tasks where errors are harmless and easy to fix.

## Inputs
- The workflow and its actions.
- Error costs and who is affected.
- Volumes and turnaround times.
- Available reviewers and their expertise.
- Current quality data, if any.

## Workflow

### Step 1. List actions
Every action the workflow takes or proposes.

### Step 2. Classify risk
Use the risk table; note legal or policy requirements.

### Step 3. Assign review levels
From the review levels table, per action.

### Step 4. Design confidence routing
Signals such as validation checks, model confidence, missing fields or category "review" send items to people.

### Step 5. Design the review screen
Source and output side by side, highlighted uncertain parts, a short checklist, quick approve, edit and reject buttons with reason codes.

### Step 6. Set service levels and owners
Who reviews, how fast, what happens when the queue grows.

### Step 7. Train reviewers
What to check, examples of good and bad outputs and when to escalate.

### Step 8. Capture feedback
Log edits and rejection reasons; review them weekly; update prompts, examples and rules.

### Step 9. Measure and adjust
Track review rate, approval rate, edit rate, time per review and errors found later; reduce or increase review based on evidence.

## Review screen checklist
```
Shown to reviewer:
- Source (email, document, record)
- AI output
- What changed or what will happen if approved
- Flags: low confidence, failed checks, sensitive content
- Checklist: facts correct? tone right? recipient right? action safe?
Buttons: Approve | Edit and approve | Reject (reason) | Escalate
```

## Warning signs of rubber-stamping
- Approval rate above 98% with average review time of a few seconds.
- Errors found later in items that were approved.
- Reviewers handling far more items than planned.
Responses: smaller batches, seeded test items with known errors, rotation, clearer checklists and feedback on misses.

## Earning autonomy
| Evidence over 4 to 8 weeks | Change |
|---|---|
| Edit rate under 2%, no serious errors | Move from approve-before-action to spot checks for that category |
| Errors concentrated in one category | Keep review for that category only |
| New model or prompt version | Return to stronger review until re-validated |

## Reason codes for rejections
| Code | Meaning |
|---|---|
| Fact | Incorrect or unsupported fact |
| Tone | Wrong tone or style |
| Policy | Breaks a rule or policy |
| Missing | Left out required information |
| Wrong target | Wrong recipient, record or category |
| Other | Explained in a note |
Reason codes turn reviewer effort into data: a weekly count by code shows which prompt rules, examples or validations to improve first.

## Writing review guidelines
A one-page guideline per workflow lists what reviewers must check, common errors with examples, what to edit versus reject, when to escalate and the target time per item. Update it whenever a new error type appears, and use real examples from the review log.

Review the guideline with reviewers monthly.

Share monthly review metrics with the team so reviewers see how their corrections improve the system.

## Designing for reviewer speed
Good review design can cut review time in half without reducing quality:
- Show only the fields that need checking, with uncertain ones highlighted.
- Pre-fill the most likely correction where possible.
- Group similar items so reviewers build rhythm.
- Use keyboard shortcuts for approve, edit and reject.
- Show the policy or source excerpt next to the claim it supports.

## Seeded checks
Insert a small share of items with known errors into the review queue, such as one in fifty. Track whether reviewers catch them. Missed seeded errors show where training, checklists or workloads need attention, without blaming individuals for real misses.

## Escalation paths
| Situation | Escalate to |
|---|---|
| Legal or contractual wording | Legal contact |
| Large financial amounts | Finance lead |
| Complaints or reputational risk | Team lead or communications |
| Personal data concerns | Data protection contact |
| AI behaving unexpectedly | Workflow owner |
Write escalation contacts into the review screen so reviewers never have to search.

## Regulatory context
Some laws and regulations require meaningful human involvement in decisions with significant effects on people, such as certain automated decisions about individuals under data protection rules, and newer AI regulations add oversight duties for higher-risk uses. Check requirements for your sector and region with qualified advisers and document how human oversight works in each workflow.

## Metrics dashboard
| Metric | Why it matters |
|---|---|
| Items sent to review | Workload and routing accuracy |
| Approval, edit and reject rates | Quality of AI outputs |
| Time per review | Reviewer effort and rubber-stamping risk |
| Errors found after approval | Review effectiveness |
| Seeded error catch rate | Attention and training needs |
| Queue age | Service levels |

## Reviewer wellbeing
Reviewing AI output all day is tiring and leads to lapses. Rotate reviewers, cap continuous review time, vary tasks and recognise good catches. Healthy reviewers catch more errors than exhausted ones.

## Review levels by workflow example
| Workflow | Action | Level |
|---|---|---|
| Ticket tagging | Apply tags | No review, weekly sample |
| Order-status replies | Send templated answers | Spot check 5% |
| Refund replies | Promise money back | Approve before send |
| CRM bulk updates | Change 500+ records | Approve batch after preview |
| Candidate shortlists | Recommend people | Human decides; AI summarises facts |
Writing the table down makes review choices visible and easy to revisit as evidence grows.

## Explaining AI involvement
Where outputs reach customers or affect people, decide what to disclose about AI involvement, and make sure people can reach a human when they need one. Clear disclosure and an easy route to a person build trust and are increasingly expected by customers and regulators.

## Rollout
Start new workflows with stronger review than you expect to need, publish the review metrics weekly and loosen review only for categories where evidence supports it. Tightening review after an incident costs far more trust than starting cautious.

Revisit review levels every quarter using the metrics dashboard.

Good review protects customers and builds trust.

## Edge cases and judgement calls
| Situation | What to do |
|---|---|
| Review queue overloaded | Prioritise by risk; tighten routing; add reviewers temporarily |
| Reviewers disagree | Clarify rules with examples; calibration sessions |
| Legal requirements for human decisions | Keep humans as decision makers; document reasons |
| Urgent actions | Fast-track queue with on-call reviewer |
| AI suggestions affecting people (hiring, performance) | Human decides; check for bias; record reasons |
| Users bypass review | Remove direct send permissions; audit logs |

## Handoffs to related skills
- Testing quality: `ai-evals-testing`
- Agents with approvals: `ai-agent-design`
- Automations with approval steps: `no-code-automation`
- Document review queues: `document-processing`
- Security and data rules: `ai-security-privacy`

## Worked example
A customer service team let AI draft replies but required approval for all of them; agents approved 99% in about four seconds each, and two incorrect refund promises still reached customers. The redesign classified replies by risk: simple order-status answers moved to spot checks, refund and complaint replies required approval with the policy and order data shown beside the draft, and low-confidence drafts were flagged. Seeded test drafts with errors checked attention. Over six weeks, review volume fell by 60%, time per review rose to about 40 seconds for the high-risk items, and no incorrect refund promises went out.

## Common mistakes
- Reviewing everything, so nothing is reviewed carefully.
- Review screens without the source.
- No logging of edits and rejections.
- Removing review because of time pressure rather than evidence.
- AI making decisions about people without human judgement.

## Output format
```
1. Actions and risk classification
2. Review level per action
3. Confidence routing rules
4. Review screen design and checklist
5. Service levels and owners
6. Feedback loop
7. Metrics and autonomy rules
```

## Self-check before you answer
- Are high-risk actions behind human approval or decision?
- Do reviewers see the source and clear checklists?
- Are edits and rejections captured to improve the system?
- Are there signs-of-rubber-stamping checks and evidence-based rules for reducing review?

---
Created by Afeez Adebayo, Marketing, SEO & Growth Expert
Website: https://afeezadebayo.com
LinkedIn: https://www.linkedin.com/in/afeez-adebayo/
X: https://x.com/za_icon
Source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/human-in-the-loop/

Licence: CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/). You may copy, share and adapt this skill, including for commercial use, as long as you credit Afeez Adebayo and link to the source URL above. Keep this notice in any copy or adapted version.

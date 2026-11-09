---
name: ai-workflow-audit
description: "Audit how a person or team uses AI and automation: a task inventory, current AI use and risks, task scoring for frequency, time, repeatability, error cost, data sensitivity and judgement, the simplest pattern per task from assistant to agent, quick wins, guardrails, baselines and a 90-day roadmap. Use whenever someone wants to adopt AI at work, find tasks to automate, plan an AI rollout for a team, decide between prompts, automations and agents, or review AI pilots that stalled."
license: CC-BY-4.0
metadata:
  author: Afeez Adebayo
  author_url: https://afeezadebayo.com
  author_linkedin: https://www.linkedin.com/in/afeez-adebayo/
  author_x: https://x.com/za_icon
  source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/ai-workflow-audit/
  category: productivity
  subcategory: ai-workflows-automation
  version: "1.0.0"
  created: "2026-10-10"
  updated: "2026-10-14"
---

# AI Workflow Audit

Most teams adopt AI in scattered ways: a few people paste work into chat tools, someone builds a clever automation that nobody else understands, a pilot never reaches production, and nobody knows which tasks AI actually improves, what it costs or what data is leaving the company. Gains stay small, risks stay hidden and enthusiasm fades.

This skill audits how a person or team uses AI and automation, then designs a practical roadmap: an inventory of repetitive work and current AI use, a scoring of tasks for automation potential, risk and value, a choice of pattern for each (assistant, workflow, agent or traditional automation), quick wins, guardrails for data and quality, measures of time saved and quality, and a 90-day plan that hands each build to a specialist skill. It is the entry point for the AI Workflows and Automation set.

## Operating principles
1. **Start from work, not tools.** List the tasks people repeat, then decide where AI helps.
2. **Simplest thing that works.** A good prompt or template often beats an agent; Anthropic's guidance on building agents recommends starting simple and adding complexity only when needed. [Reference, Anthropic, Building effective agents]
3. **Humans own outcomes.** AI drafts, sorts and checks; people approve anything risky.
4. **Measure before and after.** Time, quality and errors decide what scales.
5. **Guardrails from day one.** Data rules, review steps and logs are part of the design.

## Automation patterns
| Pattern | Description | Good for |
|---|---|---|
| Assistant (chat + skill) | A person uses an AI assistant with a skill or prompt template | Drafting, analysis, research, summaries |
| Deterministic automation | Rules-based steps in Zapier, Make, n8n or scripts | Moving data, notifications, simple routing |
| AI workflow | Fixed steps where some steps call a model | Classifying tickets, extracting fields, drafting replies |
| Agent | Model decides steps and uses tools in a loop | Open-ended tasks with many possible paths |
| Human-in-the-loop | Any of the above with approval steps | Customer-facing, financial, legal or high-risk actions |

## Task scoring
| Criterion | Question | Score 1 to 5 |
|---|---|---|
| Frequency | How often is it done? | Daily = 5 |
| Time | How long does it take each time? | Hours = 5 |
| Repeatability | Are inputs and outputs similar each time? | Very similar = 5 |
| Error cost | How bad is a mistake? | Low = 5, high = 1 |
| Data sensitivity | Does it involve personal or confidential data? | None = 5 |
| Judgement needed | How much expert judgement? | Little = 5 |
High totals are strong candidates; low error-cost and sensitivity scores mean human review is essential.

## When to use, and when not to
Use it when starting an AI programme, when pilots stall, when costs or risks are unclear, for team or department rollouts and in quarterly reviews.

Don't use it to build a specific workflow (hand off to the specialist skills) or to make legal or compliance decisions about AI use without qualified advice.

## Inputs
- Team roles and their recurring tasks.
- Tools in use: AI assistants, automation platforms, CRM, email, documents.
- Current AI use, including unofficial use.
- Data types handled and any company policies.
- Goals: time saved, quality, speed, cost.

## Workflow

### Step 1. Inventory tasks
Interview or survey people: list tasks done weekly or more, time per task, inputs, outputs and tools.

### Step 2. Map current AI use
Which tools, for what, with what data, how often and with what results.

### Step 3. Score tasks
Use the scoring table; flag tasks with high value but high risk.

### Step 4. Choose a pattern per task
Assistant, deterministic automation, AI workflow, agent, always with a human-in-the-loop level.

### Step 5. Find quick wins
Two or three tasks with high scores and low risk that can be improved within two weeks, usually with a skill or prompt template.

### Step 6. Set guardrails
Approved tools, data that must never be shared, review rules, logging and who owns each workflow.

### Step 7. Define measures
Baseline time and quality for each target task; how improvement will be measured.

### Step 8. Build the 90-day roadmap
Quick wins, then workflows, then agents where justified; owners, skills and dates.

### Step 9. Review
Monthly: adoption, time saved, quality, incidents and costs.

## Roadmap template
```
| Task | Owner | Score | Pattern | Human review | Skill | Baseline | Target | Date |
| Weekly report drafting | Ops lead | 26 | Assistant + skill | Owner edits | prompt-engineering | 3 h | 45 min | Wk 2 |
| Support ticket triage | Support lead | 24 | AI workflow | Spot checks | no-code-automation | 2 h/day | 30 min/day | Wk 6 |
| Lead research | SDRs | 22 | Agent with tools | Rep approves | ai-agent-design | 20 min/lead | 5 min | Wk 10 |
```

## Guardrails checklist
- [ ] Approved AI tools listed, with data allowed in each.
- [ ] Confidential, personal and regulated data rules written.
- [ ] Human approval required for external messages, payments, deletions and legal or HR content.
- [ ] Prompt injection risks considered for any workflow reading external content.
- [ ] Logs kept for automated actions.
- [ ] Each workflow has an owner and documentation.

## Training and adoption
Pair every rollout with short, task-based training: show people the exact skill or template for their task, a before-and-after example and the review rule. Collect feedback after two weeks, and share wins openly so adoption spreads by example rather than mandate.

## Interview guide for the task inventory
Ask each person, in 20 minutes:
1. Walk me through a normal week. Which tasks come back every week?
2. Which tasks take longest, and which feel most repetitive?
3. Where do you copy, paste or retype information between tools?
4. Which tasks involve reading lots of text to find a few facts?
5. Where do mistakes happen most often, and what do they cost?
6. Do you already use AI for any of this? Which tool, with what data?
7. What would you never want automated, and why?
Record answers in one sheet: task, person, frequency, minutes per run, tools, inputs, outputs, data types and pain notes.

## Choosing between patterns: decision questions
| Question | If yes | If no |
|---|---|---|
| Can the steps be written down in advance? | Workflow or automation | Consider an agent |
| Is the main work reading, writing or analysing text? | Assistant with a skill or an AI workflow step | Deterministic automation may be enough |
| Does the task need several tools in an unpredictable order? | Agent with tools | Workflow |
| Would a mistake reach customers, money or legal records? | Human approval before action | Spot checks may be enough |
| Does it run hundreds of times a month? | Automation with monitoring | Assistant use may be enough |

## Value calculation
```
Monthly hours saved = runs per month x (minutes before - minutes after) / 60
Monthly value = hours saved x loaded hourly cost
Net value = monthly value - (AI and tool costs + maintenance time x hourly cost)
Payback = build hours x hourly cost / net monthly value
```
Example: 80 supplier emails a month, 12 minutes each before and 4 after review: about 10.7 hours saved; at £40 an hour, about £430 a month before costs.

## Risk register
| Workflow | Risk | Likelihood | Impact | Control | Owner |
|---|---|---|---|---|---|
| Supplier email drafts | Wrong price promised | Medium | Medium | Approval before send; price pulled from system | Ops lead |
| Invoice extraction | Wrong amount posted | Low | High | Total checks; review queue | Finance lead |
| Account research agent | Acts on injected web text | Low | Medium | Read-only tools; content treated as data | Sales ops |

## Governance model for small teams
- One AI lead who owns the roadmap, approved tools and the risk register.
- An owner for every workflow, with documentation and a review date.
- A monthly 30-minute review of adoption, time saved, incidents and costs.
- A simple request process: anyone can propose a task, scored with the same table.
- A rule that new workflows go live only after evals and guardrails are in place.

## Signs the programme is working
Measured hours saved rise month on month, error rates fall or stay flat, people request new automations rather than avoiding them, unofficial tool use drops and the risk register shows no unresolved high-impact items. If adoption stalls, the cause is usually a poor fit between the tool and the real task, missing training or a review step that takes longer than the original work.

## Edge cases and judgement calls
| Situation | What to do |
|---|---|
| Unofficial AI use everywhere | Bring it into the open; approve safe tools; train |
| Leadership wants agents everywhere | Show simpler patterns first; pilot one agent with clear measures |
| Highly regulated work | Legal and compliance review; strong human review; logging |
| No baseline data | Time a sample of tasks for a week before building |
| Many small automations by one person | Document, assign owners, consolidate |
| Fear of job loss | Frame as removing drudgery; involve people in design |

## Handoffs to specialist skills
- Better prompts: `prompt-engineering`
- Reusable skills: `skill-md-authoring`
- Agents: `ai-agent-design`
- Claude Code for non-coding work: `claude-code-for-work`
- Connecting tools: `mcp-connectors`
- No-code automations: `no-code-automation`
- Documents: `document-processing`
- Knowledge bases: `rag-knowledge-bases`
- Testing quality: `ai-evals-testing`
- Review steps: `human-in-the-loop`
- Security: `ai-security-privacy`
- Costs and models: `ai-cost-model-selection`

## Worked example
A 12-person operations team used AI informally and inconsistently. The audit listed 41 recurring tasks; scoring picked weekly reporting, supplier email drafting and invoice data extraction as quick wins. Reporting moved to an assistant with a reporting skill; supplier emails used a prompt template with owner approval; invoices went into an AI extraction workflow with spot checks. Guardrails banned customer personal data in unapproved tools and required approval for external emails. After 90 days the team measured about 14 hours saved a week, fewer reporting errors and one new agent pilot for supplier research.

## Common mistakes
- Starting with tools instead of tasks.
- Building agents where a template would do.
- No baseline, so benefits cannot be shown.
- No owner or documentation for automations.
- Ignoring data and security rules.

## Output format
```
1. Task inventory
2. Current AI use and risks
3. Task scores
4. Pattern and review level per task
5. Quick wins
6. Guardrails
7. Measures and baselines
8. 90-day roadmap
```

## Self-check before you answer
- Did the audit start from real tasks?
- Is the simplest suitable pattern chosen for each?
- Are guardrails and human review defined?
- Are baselines and measures set before building?

---
Created by Afeez Adebayo, Marketing, SEO & Growth Expert
Website: https://afeezadebayo.com
LinkedIn: https://www.linkedin.com/in/afeez-adebayo/
X: https://x.com/za_icon
Source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/ai-workflow-audit/

Licence: CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/). You may copy, share and adapt this skill, including for commercial use, as long as you credit Afeez Adebayo and link to the source URL above. Keep this notice in any copy or adapted version.

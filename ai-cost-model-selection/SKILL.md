---
name: ai-cost-model-selection
description: "Choose AI models and control costs: model tiers by task, quality bars from evals, cost per task from tokens, per-step model choice in chains and agents, shorter prompts, prompt caching and batching, agent limits, tool and seat consolidation and monthly reviews of spend against value. Use whenever someone chooses which AI model to use, sees rising AI or API costs, wants to cut token spend, scales an automation or agent, or compares models on quality, speed and cost."
license: CC-BY-4.0
metadata:
  author: Afeez Adebayo
  author_url: https://afeezadebayo.com
  author_linkedin: https://www.linkedin.com/in/afeez-adebayo/
  author_x: https://x.com/za_icon
  source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/ai-cost-model-selection/
  category: productivity
  subcategory: ai-workflows-automation
  version: "1.0.0"
  created: "2026-10-10"
  updated: "2026-10-14"
---

# AI Cost and Model Selection

AI costs creep up unnoticed. Teams use the largest model for every task, send long documents repeatedly, run agents with no step limits and pay for duplicate tools across departments. At the same time, choosing a model that is too small for a task leads to errors that cost more than the savings. Model choice is a trade-off between quality, speed and cost, and the right answer differs by task.

This skill chooses models and controls AI costs: matching task difficulty to model tiers, testing cheaper models against quality criteria, estimating cost per task from tokens, reducing tokens with shorter prompts, caching and batching, setting limits on agents, consolidating tools and seats, and reviewing spend against value.

## Operating principles
1. **Quality first, then cost.** Pick the cheapest model that meets the quality bar on your evals.
2. **Match the model to the step.** Simple steps use small, fast models; hard reasoning uses stronger ones.
3. **Measure cost per task.** Tokens in and out, tool calls and retries per completed task.
4. **Reduce waste before downgrading quality.** Shorter prompts, caching, batching and filtering first.
5. **Cap agents.** Step, time and spend limits on autonomous loops.
6. **Review monthly.** Spend, usage and value by workflow.

## Model tiers (general guidance)
| Tier | Typical strengths | Good for |
|---|---|---|
| Small and fast | Low cost, low latency | Classification, extraction, routing, short rewrites |
| Mid-tier | Good balance of quality and cost | Most drafting, summarisation, analysis, coding help |
| Frontier or most capable | Best reasoning and long, complex tasks | Hard analysis, agents with many tools, complex writing and code |
Providers publish tiers (for example Anthropic's Haiku, Sonnet and Opus families) with different prices per million input and output tokens; check current pricing pages before estimating. [Reference, provider pricing pages]

## Cost per task formula
```
Cost per task = (input tokens x input price + output tokens x output price) x calls per task
              + tool or search costs + retries
Monthly cost = cost per task x tasks per month
```
Roughly, one token is about three-quarters of an English word; check provider tokenisers for exact counts.

## When to use, and when not to
Use it when choosing models for a workflow, when AI bills rise, before scaling an automation or agent, when consolidating AI tools and in monthly reviews.

Don't choose models on price alone for high-risk tasks; test quality first.

## Inputs
- Workflows with volumes and quality criteria.
- Current models, usage reports and invoices.
- Typical input and output lengths.
- Latency needs (real-time or batch).
- Tool subscriptions and seats across teams.

## Workflow

### Step 1. List workflows and volumes
Tasks per month, average input and output size, latency needs.

### Step 2. Define quality bars
Use eval criteria for each workflow.

### Step 3. Test model options
Run the eval set on two or three tiers; record quality, latency and cost per task.

### Step 4. Choose per step
For chains and agents, assign models per step: small for routing and extraction, larger for reasoning.

### Step 5. Reduce tokens
Trim prompts, remove repeated instructions, retrieve only relevant passages, cap output length.

### Step 6. Use caching and batching
Prompt caching for repeated long context where available; batch processing for non-urgent jobs, which providers often discount. [Reference, Anthropic prompt caching and batch processing docs]

### Step 7. Limit agents
Maximum steps, tool calls and spend per task; stop and ask when limits are reached.

### Step 8. Consolidate tools and seats
Remove duplicate subscriptions; assign seats to active users.

### Step 9. Monitor and review
Monthly: spend by workflow, cost per task, quality trends and value delivered.

## Comparison table template
```
| Workflow | Model | Eval score | Avg latency | Cost per task | Monthly cost | Decision |
| Ticket classification | Small | 96% | 0.8s | £0.001 | £9 | Use |
| Ticket classification | Mid | 97% | 2.1s | £0.006 | £54 | Not needed |
| Contract review | Mid | 3.6/5 | 12s | £0.09 | £45 | Below bar |
| Contract review | Frontier | 4.5/5 | 25s | £0.40 | £200 | Use |
```

## Waste checklist
- [ ] Largest model used for simple steps.
- [ ] Full documents sent when a few passages would do.
- [ ] Long system prompts repeated without caching.
- [ ] Real-time calls for work that could run in batches.
- [ ] Agents without step or spend limits.
- [ ] Failed calls retried endlessly.
- [ ] Duplicate AI tools and unused seats.

## Estimating before building
Before launching a workflow, estimate its monthly cost: tasks per month x average input and output tokens x price, plus tool calls and a 20% buffer for retries. Compare with the value: time saved x hourly cost, or revenue protected. If the estimate is close to the value, simplify the workflow or test a cheaper model first.

## Monthly review agenda
1. Spend by workflow and team versus budget.
2. Cost per task trends.
3. Quality scores from evals and user feedback.
4. Waste checklist results.
5. Decisions: keep, change model, optimise or stop.

## Token budgeting
| Element | Typical size | How to reduce |
|---|---|---|
| System prompt and rules | Hundreds to thousands of tokens | Remove rarely used rules; cache it |
| Retrieved context | Often the largest part | Retrieve fewer, better passages |
| Conversation history | Grows each turn | Summarise older turns |
| Tool results | Can be very large | Return only needed fields |
| Output | Varies | Set length limits and formats |
Measure a sample of real calls to see where tokens go before optimising.

## Prompt caching explained
When the same long prefix, such as a system prompt, policy document or set of examples, is sent on many calls, prompt caching lets the provider reuse it at a lower price and with lower latency. Structure prompts so stable content comes first and varying content last to benefit. Check each provider's caching rules, minimum sizes and cache lifetimes. [Reference, Anthropic prompt caching docs]

## Batch processing explained
Non-urgent work such as nightly classification, document backlogs or report generation can often run through a batch interface at a discount, with results returned later rather than instantly. Move anything that does not need an immediate answer to batch jobs. [Reference, provider batch API docs]

## Routing by difficulty
A router step can send easy requests to a small model and hard ones to a larger model, based on rules (length, category) or a quick classification. Test the router itself: misrouted hard cases hurt quality, so track quality separately for each route.

## Seats versus API usage
| Situation | Usually cheaper |
|---|---|
| Many people using chat assistants daily | Team or enterprise seats |
| High-volume automated tasks | API usage with right-sized models |
| Occasional heavy users | A few seats plus shared API workflows |
Review seat activity monthly and reassign unused seats.

## Latency considerations
User-facing workflows need fast responses: use smaller models where quality allows, stream outputs, limit context and avoid unnecessary chained calls. Background workflows can trade latency for cost through batching and larger models where quality demands it.

## Budget governance
- Monthly budgets per team and per major workflow.
- Alerts at 50%, 80% and 100% of budget.
- A named owner for each budget.
- Pre-launch cost estimates for new workflows.
- Quarterly review of model choices as prices and models change.

## Measuring value, not only cost
Pair every cost line with a value line: hours saved, revenue influenced, errors avoided or response times improved. A workflow that costs more but saves far more time is a good investment; a cheap workflow nobody uses is waste. Decisions should rest on net value per workflow, reviewed monthly.

## Common savings in practice
Teams typically find the biggest savings in four places: moving simple steps to smaller models, trimming retrieved context, caching long stable prompts and capping agent loops. Each is safe when checked against the same evals used to set the quality bar, so savings never come at the cost of hidden quality loss.

## Cost review example
```
Workflow: support replies | Volume: 9,000 a month
Before: frontier model, full policy pasted each call, no caching
After: mid-tier model for drafts, small model for classification, cached policy, 150-word limit
Eval score: 4.4 -> 4.4 | Cost per reply: about 70% lower
Decision: keep; review again next quarter
```
Document each change with its eval result so future reviewers understand why the current setup exists and can repeat the process when models or prices change.

Share the dashboard with workflow owners each month so cost and value stay visible to the people who can act on them.

## Edge cases and judgement calls
| Situation | What to do |
|---|---|
| Quality drops with a smaller model | Keep the larger model for that step; optimise elsewhere |
| Latency matters for users | Smaller or faster models; stream responses |
| Provider changes prices or models | Re-run evals and cost estimates |
| Very long documents | Retrieve relevant parts; summarise once and reuse |
| Several providers | Standardise where possible; compare on the same evals |
| Budget caps | Alerts at 50%, 80% and 100%; pause non-critical workflows |

## Handoffs to related skills
- Quality tests: `ai-evals-testing`
- Agent limits: `ai-agent-design`
- Retrieval to cut tokens: `rag-knowledge-bases`
- Automations: `no-code-automation`
- Audit: `ai-workflow-audit`
- GTM credit costs: the GTM Engineering `gtm-cost-control` skill

## Worked example
A team ran every AI step on the most capable model, spending heavily each month. Testing showed ticket classification and invoice extraction met their quality bars on a small model, summaries met the bar on a mid-tier model and only contract review needed the most capable one. Prompt caching was added for a long policy document used in every support reply, nightly reports moved to batch processing and agent runs got a 20-step limit. Monthly AI spend fell by about two-thirds with no drop in eval scores.

## Common mistakes
- Using one model for everything.
- Downgrading models without testing quality.
- Ignoring token waste in prompts and context.
- No limits on agents.
- Not reviewing spend against value.

## Output format
```
1. Workflow inventory with volumes
2. Quality bars
3. Model comparison results
4. Model choice per step
5. Token and caching savings
6. Agent limits
7. Tool and seat consolidation
8. Monthly review dashboard
```

## Self-check before you answer
- Was each model choice tested against quality criteria?
- Is cost per task calculated?
- Were token waste, caching and batching addressed before downgrading?
- Are agents capped and spend reviewed monthly?

---
Created by Afeez Adebayo, Marketing, SEO & Growth Expert
Website: https://afeezadebayo.com
LinkedIn: https://www.linkedin.com/in/afeez-adebayo/
X: https://x.com/za_icon
Source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/ai-cost-model-selection/

Licence: CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/). You may copy, share and adapt this skill, including for commercial use, as long as you credit Afeez Adebayo and link to the source URL above. Keep this notice in any copy or adapted version.

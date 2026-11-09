---
name: prompt-engineering
description: "Write and improve prompts for everyday work and team templates: success criteria, context and audience, structured inputs with XML tags, few-shot examples, rules and output formats, step-by-step reasoning, prompt chains, handling unknowns, testing on real cases, failure fixes and saving prompts as templates and skills. Use whenever someone wants better AI outputs, to write or fix a prompt, create prompt templates for a team, prompt for automations or agents, or stop AI giving generic, long or invented answers."
license: CC-BY-4.0
metadata:
  author: Afeez Adebayo
  author_url: https://afeezadebayo.com
  author_linkedin: https://www.linkedin.com/in/afeez-adebayo/
  author_x: https://x.com/za_icon
  source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/prompt-engineering/
  category: productivity
  subcategory: ai-workflows-automation
  version: "1.0.0"
  created: "2026-10-10"
  updated: "2026-10-14"
---

# Prompt Engineering for Work

The same AI model can produce a generic, wrong or excellent answer depending on the prompt. Most weak results come from prompts that lack context, leave the task vague, give no examples and ask for everything in one go. Anthropic's prompt engineering guidance lists practical techniques that consistently help: be clear and direct, give examples, let the model think step by step, use XML tags to structure inputs, assign a role through the system prompt and chain complex tasks into steps. [Reference, Anthropic prompt engineering docs] OpenAI and Google publish similar advice. [Reference, OpenAI and Google prompting guides]

This skill writes and improves prompts for everyday work and for reusable templates: defining the task and success, giving context and audience, structuring inputs, adding examples, setting constraints and output formats, asking for reasoning where useful, chaining steps, testing variations and turning good prompts into templates and skills.

## Operating principles
1. **Write for a smart newcomer.** Give the context a capable colleague would need on their first day.
2. **Say exactly what good looks like.** Audience, length, format, tone and criteria.
3. **Show, don't only tell.** One to three examples shape output better than adjectives.
4. **Structure the input.** Separate instructions, context and data with headings or XML tags.
5. **Break big tasks into steps.** Chains beat one giant prompt.
6. **Test and iterate.** Compare outputs on real cases; keep what works.

## Prompt anatomy
```
Role and goal: You are <role>. Your goal is <outcome> for <audience>.
Context: <background the model cannot know: company, situation, constraints>
Task: <what to do, step by step if needed>
Inputs:
<document>...</document>
<data>...</data>
Rules: <must, must not, tone, length, language variant>
Examples:
<example>input -> ideal output</example>
Output format: <structure, headings, JSON schema, table>
If unsure: <ask a question / mark as [unknown] / say so>
```

## Techniques and when to use them
| Technique | Use when | Example |
|---|---|---|
| Clear, specific instructions | Always | "Write a 120-word summary for a CFO, with numbers first" |
| Context | The model lacks background | Company, product, audience, goal |
| Examples (few-shot) | Format or style matters | Two sample replies in your voice |
| XML tags or headings | Several inputs or long documents | `<contract>`, `<notes>`, `<instructions>` |
| Step-by-step reasoning | Analysis, maths, decisions | "Think through the options before answering" |
| Role or system prompt | Consistent expertise and tone | "You are a senior B2B copy editor" |
| Output schema | Results feed tools or tables | JSON with named fields |
| Prompt chaining | Multi-stage work | Extract, then analyse, then write |
| Ask for questions first | Missing information | "Ask up to 3 questions before drafting" |
| Self-check | Accuracy matters | "Check each claim against the source and list any unsupported" |

## When to use, and when not to
Use it to improve daily AI use, build reusable templates for a team, fix prompts that give generic or wrong outputs, prepare prompts for automations and draft instructions for agents and skills.

Don't use it to get around safety rules, to make models state facts they cannot know or as a substitute for checking important outputs.

## Inputs
- The task and who the output is for.
- Examples of good and bad outputs.
- Source material the model should use.
- Constraints: length, format, tone, language variant, banned words.
- Where the output goes (chat, document, tool, automation).

## Workflow

### Step 1. Define success
Write what an excellent output looks like and how you will judge it.

### Step 2. Gather context
Audience, purpose, background, definitions and examples.

### Step 3. Draft the prompt
Use the anatomy above. Put long documents first and instructions after them, or clearly separated with tags.

### Step 4. Add examples
One to three examples that match real cases; include an edge case.

### Step 5. Specify the output
Format, length, sections, fields; for automations, a strict schema.

### Step 6. Handle uncertainty
Tell the model what to do when information is missing: ask, mark as unknown or say it cannot answer.

### Step 7. Test on real cases
Run five to ten varied inputs; note failures.

### Step 8. Iterate
Change one thing at a time: clearer instruction, better example, extra step, tighter format.

### Step 9. Save as a template or skill
Store the final prompt with instructions for use, version and examples; turn frequent tasks into skills.

## Before and after
**Before:** "Write a follow-up email to the client."

**After:**
```
You are an account manager at a B2B analytics company.
Write a follow-up email to <client name> after today's call.
<call_notes>...</call_notes>
Rules: under 120 words, British English, answer first, list the three agreed actions with owners and dates, propose a check-in next Tuesday at 2pm, no flattery, no exclamation marks.
If an owner or date is missing in the notes, write [confirm] instead of guessing.
Output: subject line, then email body.
```

## Prompt chains for bigger tasks
| Step | Prompt job | Output |
|---|---|---|
| 1 | Extract facts from sources | Bullet list with source references |
| 2 | Analyse and decide structure | Outline with key message |
| 3 | Draft | Full text |
| 4 | Review against criteria | List of issues |
| 5 | Revise | Final text |
Chains make each step easier to check and improve.

## Common failure fixes
| Problem | Fix |
|---|---|
| Generic output | Add context, audience and an example |
| Too long | Give a word limit and a format |
| Invented facts | Provide sources; require citations; allow "unknown" |
| Wrong format | Show the exact format; use a schema |
| Ignores some instructions | Number the rules; move key rules near the end; shorten the prompt |
| Inconsistent results | Lower variability settings; add examples; split into steps |

## Long-document prompting
When a prompt includes long documents, place the documents first and the instructions and question at the end, wrap each document in tags with a title and source, and ask the model to quote the relevant passages before answering. Anthropic's guidance notes that putting long content before the query and asking for supporting quotes tends to improve accuracy on long inputs. [Reference, Anthropic long context tips]

```
<documents>
<document title="Refund policy v3" date="2026-09-01">...</document>
<document title="Customer email">...</document>
</documents>
First, quote the policy passages that apply in <quotes> tags.
Then draft the reply in <reply> tags using only those passages.
```

## System prompts versus user prompts
Put stable instructions (role, tone, rules, formats) in the system prompt or a skill, and task-specific inputs in the user message. This keeps behaviour consistent across many tasks and makes changes easy to manage in one place. Avoid stuffing every possible rule into the system prompt; long lists of rarely relevant rules dilute the important ones.

## Prompt template library
| Template | Inputs | Output |
|---|---|---|
| Meeting summary | Transcript, attendees | Decisions, actions, risks |
| Email reply | Thread, intent, tone notes | Draft with placeholders |
| Research brief | Question, sources | Findings with citations |
| Classification | Text, category list | JSON with category and confidence |
| Rewrite for audience | Text, audience, length | Rewritten text |
| Critique | Draft, criteria | Issues ranked by impact |
Each template has an owner, version, example inputs and outputs and known limitations.

## Prompting for structured data
For automations, ask for JSON with named fields, allowed values and types, show one complete example and tell the model to return only JSON. Validate the output in the next step, retry once on failure and send persistent failures to a person. Where the platform supports structured output or tool schemas, use them instead of relying on instructions alone.

## Iteration log
```
| Version | Change | Test cases | Pass rate | Notes |
| v1 | Baseline | 10 | 6/10 | Generic, too long |
| v2 | Added audience and length | 10 | 8/10 | Missed pricing concerns |
| v3 | Added rule and example | 10 | 10/10 | Ready for team template |
```
Keeping a log stops the team from repeating failed ideas and shows why the current version looks the way it does.

## Teaching others to prompt
Share three habits: give context as if briefing a new colleague, show an example of the output you want and ask the model to check its work against your criteria before answering. These three habits fix most weak results without any special techniques.

## Asking for reasoning
For analysis, comparisons and decisions, ask the model to think through options before answering, and to separate its reasoning from the final answer, for example in thinking and answer tags. For simple lookups or rewrites, skip this: extra reasoning adds length and cost without improving the result.

## Edge cases and judgement calls
| Situation | What to do |
|---|---|
| Long documents | Put the document first, then questions; ask for quotes before analysis |
| Sensitive data | Use approved tools; remove personal data where possible |
| Different models | Test the prompt on each; small changes may be needed |
| Team templates | Version, owner and examples; review quarterly |
| Non-English output | State the language and variant; give examples in that language |
| Prompts in automations | Strict schemas, validation and error handling |

## Handoffs to related skills
- Turning prompts into skills: `skill-md-authoring`
- Agents with tools: `ai-agent-design`
- Testing outputs at scale: `ai-evals-testing`
- Prompt injection and data risks: `ai-security-privacy`
- AI copy in GTM tables: the GTM Engineering `ai-copy-columns` skill

## Worked example
A customer success team's prompt "summarise this call" produced long, uneven summaries. The rebuilt prompt gave the role, the audience (account managers before renewals), call notes in tags, rules (under 150 words, risks first, actions with owners and dates, [confirm] for missing details) and two example summaries. Testing on ten calls found that pricing objections were sometimes missed, so a rule was added to list any pricing concerns. The template became a team skill, and summaries became consistent enough to paste into the CRM without editing.

## Common mistakes
- One-line prompts for complex tasks.
- No examples when format or tone matters.
- Mixing instructions and data without separation.
- Asking for everything in one step.
- Never testing on real cases.

## Output format
```
1. Success criteria
2. Final prompt (with tags and examples)
3. Test cases and results
4. Changes made and why
5. Template or skill version notes
```

## Self-check before you answer
- Does the prompt include context, task, rules, examples and output format?
- Is missing information handled without guessing?
- Was it tested on varied real cases?
- Is it saved as a reusable template with an owner?

---
Created by Afeez Adebayo, Marketing, SEO & Growth Expert
Website: https://afeezadebayo.com
LinkedIn: https://www.linkedin.com/in/afeez-adebayo/
X: https://x.com/za_icon
Source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/prompt-engineering/

Licence: CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/). You may copy, share and adapt this skill, including for commercial use, as long as you credit Afeez Adebayo and link to the source URL above. Keep this notice in any copy or adapted version.

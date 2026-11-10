---
name: skill-md-authoring
description: "Write and improve Agent Skills: SKILL.md anatomy and frontmatter, descriptions that trigger on real requests, focused jobs, principles, workflows, templates, worked examples, edge cases, handoffs, output formats and self-checks, progressive disclosure with supporting files, white-labelling, trigger tests and versioning. Use whenever someone wants to create a Claude skill or Agent Skill, write or improve a SKILL.md, turn a playbook into a skill, fix a skill that does not trigger, or publish a private skill safely."
license: CC-BY-4.0
metadata:
  author: Afeez Adebayo
  author_url: https://afeezadebayo.com
  author_linkedin: https://www.linkedin.com/in/afeez-adebayo/
  author_x: https://x.com/za_icon
  source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/skill-md-authoring/
  category: productivity
  subcategory: ai-workflows-automation
  version: "1.0.0"
  created: "2026-10-10"
  updated: "2026-10-14"
---

# Writing SKILL.md Files

Agent Skills package know-how so an AI agent can do a task well every time: a folder with a SKILL.md file containing a name, a description and instructions, plus optional scripts, templates and reference files. Anthropic introduced Agent Skills for Claude in October 2025, and the format has since been adopted as an open standard across many agent tools. [Confirmed, Anthropic Agent Skills; agentskills.io] Skills load through progressive disclosure: the agent first sees only each skill's name and description, reads the full SKILL.md when a task matches, and opens extra files only when needed. [Reference, Anthropic skills documentation] Weak skills fail in predictable ways: vague descriptions that never trigger, instructions so long the important rules get lost, no examples, no edge cases and no way to check the output.

This skill writes and improves SKILL.md files: a description that triggers on the right requests, clear operating principles, inputs, a step-by-step workflow, templates and examples, edge cases, handoffs to other skills, an output format and a self-check, kept focused and tested on real tasks.

## Operating principles
1. **The description is the trigger.** It must say what the skill does and when to use it, in the words users actually type.
2. **One skill, one job.** Focused skills trigger and perform better than giant ones.
3. **Write for a capable model without your context.** Explain the why behind rules, not only the rules.
4. **Show the output.** Templates and worked examples beat abstract instructions.
5. **Keep the core lean.** Put long reference material in separate files the skill points to.
6. **Test with real prompts.** Check that it triggers, follows the workflow and produces good output.

## Anatomy of a SKILL.md
```markdown
---
name: weekly-review
description: Run a 30 to 45-minute weekly review... Use whenever someone wants to plan next week, clean up their task list or restart after a holiday.
---

# Weekly Review
Why this matters (2 to 3 short paragraphs, with sources where useful)

## Operating principles
## Inputs
## When to use, and when not to
## Workflow (numbered steps)
## Templates and examples
## Edge cases and judgement calls
## Handoffs to related skills
## Worked example
## Common mistakes
## Output format
## Self-check before you answer
```
Name rules in the open standard: lowercase letters, numbers and hyphens, matching the folder name. [Reference, agentskills.io specification]

## Writing the description
| Weak | Strong |
|---|---|
| "Helps with emails." | "Draft short, answer-first email replies in the user's voice... Use whenever someone needs to reply to an email, decline politely, schedule a meeting by email or chase a reply." |
| "SEO skill." | "Audit and fix Largest Contentful Paint... Use whenever Search Console flags poor LCP, a hero image is slow or someone wants faster loading on WordPress." |
A good description names the outcome, the main methods and several trigger phrases. Agents tend to under-trigger skills, so descriptions should be specific and a little generous with trigger situations.

## When to use, and when not to
Use it to turn a repeated task, team playbook or expert method into a skill; to improve a skill that triggers poorly or gives uneven results; to white-label a private skill for public use; or to review skills from others.

Don't use it for one-off tasks a simple prompt can handle, or to package instructions that bypass safety policies.

## Inputs
- The task, who does it and how often.
- The best existing method: playbooks, examples, checklists, expert interviews.
- Typical user requests that should trigger the skill.
- Tools, files or scripts the skill needs.
- Examples of excellent and poor outputs.

## Workflow

### Step 1. Define the job
One sentence: the outcome, for whom, in what situation.

### Step 2. Collect the method
Interview experts or extract from playbooks: steps, rules, checks, common mistakes and examples.

### Step 3. Write the description
Outcome, key methods and trigger phrases; test it against ten realistic requests (should trigger) and five near misses (should not).

### Step 4. Write the body
Principles, inputs, workflow steps, templates, edge cases, handoffs, worked example, mistakes, output format and self-check.

### Step 5. Add supporting files if needed
Scripts for deterministic work, templates, and reference documents for long detail; link them from SKILL.md with when to read each.

### Step 6. Remove personal or private details
For public skills, replace names, clients, numbers and internal URLs with placeholders or generic examples.

### Step 7. Test
Run real prompts with and without the skill; compare outputs; check triggering, adherence to the workflow and quality.

### Step 8. Iterate and version
Fix failures, record changes, version the skill and review it when tools or methods change.

## Quality checklist
- [ ] Description states what and when, with realistic trigger phrases.
- [ ] Workflow steps are numbered and actionable.
- [ ] At least one template and one worked example.
- [ ] Edge cases and judgement calls covered.
- [ ] Output format defined.
- [ ] Self-check at the end.
- [ ] No secrets, personal data or private client details.
- [ ] Tested on at least five real requests.

## Where skills live
| Tool | Location |
|---|---|
| Claude apps | Upload a zip of the skill folder in skill settings |
| Claude Code | `~/.claude/skills/<name>/SKILL.md` or `.claude/skills/` in a project |
| Codex and other Agent Skills tools | The tool's skills folder, often `.agents/skills/` |
Keep one master copy in version control and publish from it, so every tool gets the same version.

## Description formula
```
<Verb> <outcome> <for whom or what>: <key methods, separated by commas>.
Use whenever someone <trigger situation 1>, <trigger situation 2>, <trigger situation 3> or <trigger situation 4>, even if they do not say <skill name>.
```
Example: "Run row-by-row QA on Clay tables against a written spec: field checks, copy checks and a go or no-go report. Use whenever someone builds outbound tables, wants to QA AI copy before launch or validate records before a CRM sync, even if they do not say QA."

## Writing instructions models follow
- Explain why a rule exists; models apply reasons to new cases better than bare commands.
- Prefer positive instructions ("write in plain British English") over long lists of prohibitions.
- Put the most important rules in the workflow and self-check, not only in a long list.
- Use tables for options and decisions; they are easier to scan than paragraphs.
- Give one excellent example rather than many mediocre ones.

## Progressive disclosure in practice
Keep SKILL.md focused on what the agent needs on every run. Put long material in referenced files with clear instructions on when to read them, for example "Read references/schema-types.md only when the user asks about Product or Event schema." This keeps the agent's working context small and avoids drowning key instructions. Anthropic's skill guidance recommends keeping the main file reasonably short and splitting detail into referenced files as it grows. [Reference, Anthropic skill authoring best practices]

## Bundling scripts
Use scripts for anything that must be exact or repeatable: calculations, format conversions, validations, API calls. In SKILL.md, say when to run the script, what arguments it takes and how to interpret its output. Scripts make skills more reliable and cheaper because the model does not have to reproduce logic token by token.

## Testing protocol
| Test | How | Pass |
|---|---|---|
| Trigger | 10 realistic requests that should use the skill | 9 or more trigger |
| Non-trigger | 5 near-miss requests | 4 or more do not trigger |
| Workflow | Check outputs follow the steps | All key steps present |
| Quality | Compare with and without the skill on 5 tasks | Skill version clearly better |
| Edge cases | Run 3 hard cases from the edge case table | Handled as written |

## Versioning and maintenance
Add a version and changelog to every published skill, review it when tools, laws or methods change and collect user feedback in one place. Retire skills that overlap or are no longer used, and merge near-duplicates so agents are not confused about which to load.

## Library organisation
Group skills by domain, give each a start-here skill that routes to specialists, use consistent section headings across skills and keep naming predictable. A well-organised library helps both people browsing and agents choosing the right skill.

## Edge cases and judgement calls
| Situation | What to do |
|---|---|
| Skill too long | Move reference detail into separate files; keep SKILL.md focused |
| Overlapping skills | Sharpen descriptions; add handoffs between them |
| Skill never triggers | Add trigger phrases users actually say; make the description more specific |
| Skill triggers too often | Narrow the description; add "don't use for" guidance |
| Deterministic steps (calculations, file conversion) | Bundle a script and tell the agent to run it |
| Team-specific rules | Keep a private version; publish a white-labelled one |

## Handoffs to related skills
- Prompt techniques used inside skills: `prompt-engineering`
- Agents that use skills: `ai-agent-design`
- Testing skill outputs: `ai-evals-testing`
- Claude Code workflows: `claude-code-for-work`
- Documentation of workflows: the Workplace Writing `sops-process-docs` skill

## Worked example
A recruiter had a 2,500-line private CV-writing skill full of personal details, which triggered unreliably. The rewrite produced a focused public skill: a description listing the outcome and phrases such as "tailor my CV" and "write a cover letter for this job", a workflow from reading the job description to ATS checks, templates, edge cases and a self-check. Personal identifiers were replaced with placeholders, and long reference material moved to separate files. Testing on ten requests showed it triggered on nine (the miss led to a description tweak) and produced consistent CVs.

## Common mistakes
- Vague descriptions that never trigger.
- Giant skills covering many jobs.
- Rules without reasons or examples.
- No output format or self-check.
- Publishing private details.

## Output format
```
1. Job definition
2. SKILL.md with frontmatter (name, description)
3. Supporting files list (if any)
4. Trigger tests (should and should not trigger)
5. Output tests and changes made
6. Version notes
```

## Self-check before you answer
- Does the description say what the skill does and when to use it?
- Is the skill focused on one job with a clear workflow?
- Are templates, examples, edge cases and a self-check included?
- Was it tested on real requests?

---
Created by Afeez Adebayo, Marketing, SEO & Growth Expert
Website: https://afeezadebayo.com
LinkedIn: https://www.linkedin.com/in/afeez-adebayo/
X: https://x.com/za_icon
Source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/skill-md-authoring/

Licence: CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/). You may copy, share and adapt this skill, including for commercial use, as long as you credit Afeez Adebayo and link to the source URL above. Keep this notice in any copy or adapted version.

---
name: rag-knowledge-bases
description: "Design knowledge bases and retrieval-augmented generation for teams: real question inventories, source audits and clean-up, choosing between project files, connectors, enterprise search and custom RAG, structure and metadata, answer prompts that cite or decline, permissions, evaluation scorecards and maintenance. Use whenever someone wants an AI assistant that answers from company documents, builds a knowledge base or RAG pipeline, fixes wrong or outdated AI answers, or sets up Claude Projects or custom GPTs with knowledge files."
license: CC-BY-4.0
metadata:
  author: Afeez Adebayo
  author_url: https://afeezadebayo.com
  author_linkedin: https://www.linkedin.com/in/afeez-adebayo/
  author_x: https://x.com/za_icon
  source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/rag-knowledge-bases/
  category: productivity
  subcategory: ai-workflows-automation
  version: "1.0.0"
  created: "2026-10-10"
  updated: "2026-10-14"
---

# RAG and Knowledge Bases

AI assistants answer better when they can look up the right information instead of relying on memory: company policies, product documentation, past proposals, support articles, research notes. Retrieval-augmented generation (RAG) does this by searching a knowledge base for relevant passages and giving them to the model with the question. Done well, answers become accurate, current and cited. Done badly, the assistant retrieves the wrong passages, mixes outdated and current documents, invents answers when nothing relevant exists or exposes documents to people who should not see them.

This skill designs knowledge bases and RAG for teams: choosing the approach (project files, built-in knowledge features, connectors or a custom RAG pipeline), curating and structuring sources, chunking and metadata, retrieval settings, answer prompts that require citations and "I don't know", access control, evaluation and maintenance.

## Operating principles
1. **Curate before you index.** Garbage in, confident garbage out.
2. **One source of truth per topic.** Remove or archive outdated duplicates.
3. **Structure helps retrieval.** Clear titles, headings, short sections and metadata.
4. **Cite or decline.** Answers quote sources; when nothing relevant is found, the assistant says so.
5. **Respect permissions.** Users only retrieve what they are allowed to see.
6. **Measure answer quality.** Test with real questions and fix gaps.

## Approaches
| Approach | When it fits | Examples |
|---|---|---|
| Project knowledge or uploaded files | Small, stable sets of documents for a team | Claude Projects, custom GPT knowledge |
| Connectors to live sources | Documents change often in existing tools | Drive, Notion, Confluence connectors |
| Built-in enterprise search | Company-wide knowledge with permissions | Workspace search tools with AI |
| Custom RAG pipeline | Large volumes, products, special needs | Vector database plus retrieval code |
| Long context only | A few long documents per task | Paste or attach documents directly |
Start with the simplest approach that covers your documents and permissions.

## When to use, and when not to
Use it for internal help desks, sales and support knowledge, policy and process questions, onboarding, research libraries and product documentation assistants.

Don't use it to answer questions from sources nobody maintains, or to give access to confidential documents without permission controls.

## Inputs
- The questions people ask (from tickets, chat, email, interviews).
- Candidate sources and their owners.
- Permissions and sensitivity of each source.
- Tools available (assistant features, connectors, developers).
- Update frequency of the content.

## Workflow

### Step 1. Collect real questions
Gather 50 to 100 questions people actually ask; group by topic.

### Step 2. Audit sources
For each topic: which document answers it, is it current, who owns it, are there duplicates or conflicts?

### Step 3. Fix the content
Update, merge or archive; write missing answers; add clear titles, headings and dates.

### Step 4. Choose the approach
From the table above, based on size, change rate, permissions and resources.

### Step 5. Structure for retrieval
Short sections with headings; metadata such as owner, date, product, region and audience; for custom pipelines, chunk by section (often a few hundred words) with some overlap.

### Step 6. Write the answer prompt
Answer only from retrieved sources, cite titles and sections, say "I couldn't find this" when sources do not cover it, and flag conflicting sources.

### Step 7. Set permissions
Mirror source permissions; separate knowledge bases for sensitive areas if needed.

### Step 8. Evaluate
Run the real questions; score correctness, citation quality and "I don't know" behaviour; fix content or retrieval.

### Step 9. Maintain
Owners review content on a schedule; log unanswered questions and add content for them.

## Answer prompt example
```
Answer the question using only the sources provided.
- Cite the source title and section for each key point.
- If the sources do not contain the answer, say: "I couldn't find this in our documents" and suggest who to ask.
- If sources conflict, show both and say which is newer.
- Keep answers under 150 words unless asked for more.
<sources>...</sources>
Question: ...
```

## Evaluation scorecard
| Measure | Target |
|---|---|
| Correct answers on test questions | 90%+ |
| Answers with correct citations | 95%+ |
| Correct "I don't know" when no source exists | 95%+ |
| Answers using outdated documents | 0 |
| Permission leaks | 0 |

## Writing content that retrieves well
- One topic per page or section, with a descriptive title.
- Put the answer in the first sentence of each section.
- Spell out acronyms once and use consistent terms.
- Add dates, owners and audience to each document.
- Prefer text over images of text; describe tables in words where possible.

## Custom pipeline notes
For custom RAG, combine keyword and semantic search (hybrid retrieval), filter by metadata such as product or region, rerank results before passing them to the model and log which chunks were used for each answer. Logs show whether bad answers come from missing content, poor retrieval or the answer prompt.

## Logging unanswered questions
Record every question where the assistant said it could not find an answer. Review the list weekly with content owners; most improvements come from writing the missing answers rather than tuning retrieval.

## Rollout
Launch to a small group first, with a visible way to rate answers and report problems. Review ratings and unanswered questions weekly for the first month, fix the top issues, then widen access. Tell users clearly what the assistant knows, what it does not cover and who to ask when it cannot help, so trust builds on accurate expectations.

Revisit the question inventory every quarter as new topics appear.

Measure ratings monthly.

## Chunking and metadata in detail
| Content type | Chunking approach | Useful metadata |
|---|---|---|
| Policies | One section per chunk, keep headings | Owner, effective date, region, audience |
| Help articles | One article or major section | Product, feature, version, last updated |
| Contracts | Clause by clause | Party, contract type, dates |
| Meeting notes | One meeting per chunk | Date, team, project |
| Spreadsheets | Convert rows to sentences or query directly | Sheet, column definitions |
Include the document title and section heading in each chunk so retrieved passages make sense on their own.

## Retrieval quality checks
For each test question, record which passages were retrieved and whether the right one was among the top results. If the right passage is often missing, the problem is retrieval (chunking, metadata, search settings); if it is retrieved but the answer is wrong, the problem is the answer prompt or conflicting content. Separating these saves time.

## Freshness rules
- Every document shows an owner and last reviewed date.
- Answers mention the date of the source when policies change often.
- Outdated documents are archived, not left searchable.
- Connectors to live systems are preferred for fast-changing content.
- A monthly report lists documents past their review date.

## Access control patterns
| Pattern | Use when |
|---|---|
| One knowledge base per audience | Clear audience boundaries (sales, support, HR) |
| Permission-aware connectors | Sources already have good permissions |
| Metadata filters by role | Custom pipelines with role-based access |
| Restricted assistant | Sensitive HR, legal or finance content |
Never rely on the model to keep secrets it can retrieve; enforce permissions before retrieval.

## Assistant answer style
Short answers with the key fact first, citations to titles and sections, a link to the full document and a note when the answer depends on region, plan or date. For procedures, numbered steps; for policies, the rule, exceptions and who to ask. Consistent style builds trust and makes answers easy to check.

## Common failure patterns
| Symptom | Likely cause | Fix |
|---|---|---|
| Confident wrong answers | Outdated or conflicting sources | Clean content; one owner per topic |
| "I couldn't find this" too often | Missing content or poor retrieval | Write content; improve chunking and metadata |
| Long, vague answers | Prompt allows rambling | Length limits; key fact first |
| Answers from the wrong region or product | Missing metadata filters | Add and use metadata |

## Question routing
Not every question should be answered by the assistant. Route questions about individual cases (a specific customer, a personal HR matter), approvals and anything requiring judgement to people, and say so politely with the right contact. Log these routed questions too; patterns show where new content or processes would help.

## Measuring value
Track questions answered, correct-answer rate from sampling, unanswered questions, time saved compared with searching or asking colleagues and user ratings. Share results monthly with content owners so they see the impact of keeping documents current.

## Ownership
Every topic area has a named content owner who reviews documents on a schedule, answers flagged gaps and approves changes. Without owners, knowledge bases decay within months.

Review owners and gaps every quarter.

## Edge cases and judgement calls
| Situation | What to do |
|---|---|
| Conflicting documents | Fix at the source; one owner decides |
| Content changes daily | Use live connectors rather than uploaded copies |
| Tables and spreadsheets | Convert to clear text or use tools that query them |
| Very large libraries | Custom pipeline with metadata filters and hybrid search |
| Sensitive HR or legal content | Separate restricted knowledge base; strict permissions |
| Questions outside scope | Polite decline and route to a person |

## Handoffs to related skills
- Prompts: `prompt-engineering`
- Connectors: `mcp-connectors`
- Testing answers: `ai-evals-testing`
- Security and permissions: `ai-security-privacy`
- Knowledge management practices: the Knowledge Management skills

## Worked example
A support team's internal assistant gave confident but wrong answers about refund rules. An audit of 80 real questions found three conflicting refund documents and no answers for 12 common questions. The team merged the documents with one owner, wrote the missing answers, added dates and headings, connected the help centre through a live connector and changed the prompt to cite sources and say when it could not find an answer. Evaluation on the 80 questions rose from 61% to 93% correct, with no answers drawn from outdated policies.

## Common mistakes
- Indexing everything without curation.
- Outdated duplicates in the knowledge base.
- Prompts that let the model answer without sources.
- Ignoring permissions.
- No evaluation or maintenance.

## Output format
```
1. Question inventory by topic
2. Source audit and fixes
3. Chosen approach
4. Structure and metadata plan
5. Answer prompt
6. Permissions model
7. Evaluation results
8. Maintenance schedule
```

## Self-check before you answer
- Was content curated and deduplicated before indexing?
- Does the assistant cite sources and decline when it cannot find an answer?
- Are permissions respected?
- Was it evaluated on real questions?

---
Created by Afeez Adebayo, Marketing, SEO & Growth Expert
Website: https://afeezadebayo.com
LinkedIn: https://www.linkedin.com/in/afeez-adebayo/
X: https://x.com/za_icon
Source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/rag-knowledge-bases/

Licence: CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/). You may copy, share and adapt this skill, including for commercial use, as long as you credit Afeez Adebayo and link to the source URL above. Keep this notice in any copy or adapted version.

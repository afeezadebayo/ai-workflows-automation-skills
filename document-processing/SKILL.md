---
name: document-processing
description: "Extract and summarise documents with AI: field schemas, document preparation, extraction prompts with JSON output and no guessing, automatic validation of totals, dates and duplicates, confidence-based review routing, accuracy testing, integration and monitoring for invoices, contracts, forms, CVs and reports. Use whenever someone wants to extract data from invoices, receipts, PDFs, contracts, forms or CVs with AI, automate data entry, summarise or compare long documents, or check the accuracy of AI extraction."
license: CC-BY-4.0
metadata:
  author: Afeez Adebayo
  author_url: https://afeezadebayo.com
  author_linkedin: https://www.linkedin.com/in/afeez-adebayo/
  author_x: https://x.com/za_icon
  source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/document-processing/
  category: productivity
  subcategory: ai-workflows-automation
  version: "1.0.0"
  created: "2026-10-10"
  updated: "2026-10-14"
---

# Document Processing with AI

Teams spend hours retyping data from invoices, receipts, contracts, forms, CVs, purchase orders and reports. Modern AI models can read PDFs, scans and images and extract structured data far faster, but accuracy varies with document quality, layout and the clarity of instructions. Errors in extracted amounts, dates or names can flow into accounting, CRM or legal systems unnoticed.

This skill designs AI document processing: defining the fields and schema, preparing documents, writing extraction prompts with rules and examples, validating outputs with checks, routing low-confidence results to people, handling different document types, summarising and comparing long documents and integrating results into spreadsheets, databases or workflows.

## Operating principles
1. **Schema first.** Define exactly which fields, formats and allowed values you need.
2. **Source-grounded.** Every extracted value should come from the document, with page or quote where useful.
3. **Validate automatically.** Totals, dates, formats and cross-field rules catch many errors.
4. **Confidence routes work.** Unclear or failed checks go to a person.
5. **Test on real samples.** Measure accuracy per field before scaling.

## Common document tasks
| Task | Output |
|---|---|
| Invoice and receipt extraction | Supplier, number, date, currency, net, tax, total, line items |
| Contract review | Parties, dates, term, renewal, termination, liability caps, key clauses |
| CV screening support | Name, roles, years, skills, education (for human review) |
| Form processing | Fields mapped to a database |
| Report summarisation | Key findings, numbers, actions |
| Document comparison | Differences between versions |
| Classification | Document type and routing |

## When to use, and when not to
Use it for repeated document types with consistent fields, high volumes of manual data entry, contract and report review support and document routing.

Don't use it to make final legal, financial or hiring decisions without human review, or on sensitive documents in unapproved tools.

## Inputs
- Sample documents (20 to 50 across suppliers, layouts and quality).
- The fields needed and where they go.
- Validation rules (totals, date ranges, allowed values).
- Volume and turnaround needs.
- Data sensitivity and retention rules.

## Workflow

### Step 1. Define the schema
Field name, description, type, format, required or optional, allowed values.

### Step 2. Prepare documents
Prefer digital PDFs; for scans, ensure readable resolution; split multi-document files; record file names as IDs.

### Step 3. Write the extraction prompt
Role, task, schema, rules (use only the document, return null if missing, no guessing), output as JSON, examples.

### Step 4. Add validation
Numeric checks (net + tax = total, line items sum), date logic, formats (VAT numbers, IBANs), lookups against supplier lists.

### Step 5. Score confidence
Flag missing required fields, failed checks and low-quality scans for review.

### Step 6. Test accuracy
Compare extracted values with a hand-checked sample; calculate accuracy per field.

### Step 7. Integrate
Write validated results to the spreadsheet, database or system; keep the source file link.

### Step 8. Monitor
Weekly sample checks, review queue size, error types and new layouts.

## Extraction prompt example
```
Extract invoice data from the document below.
Return JSON only with these fields:
supplier_name (string), invoice_number (string), invoice_date (YYYY-MM-DD),
currency (ISO code), net_amount (number), tax_amount (number), total_amount (number),
line_items (list of {description, quantity, unit_price, amount})
Rules:
- Use only information in the document. If a field is missing, return null.
- Do not calculate missing values; extract what is written.
- Dates in the document may be day-first; convert to YYYY-MM-DD.
<document>...</document>
```

## Validation rules example
| Check | Rule | On failure |
|---|---|---|
| Total | net + tax = total (within 0.01) | Review |
| Line items | sum of amounts = net | Review |
| Date | Not in the future, not over a year old | Review |
| Supplier | Matches supplier list | Review or add supplier |
| Duplicate | Same supplier and invoice number already exists | Block |

## Long document summaries
For contracts and reports, ask for structured outputs with references: "For each item, quote the clause and give the page". Use a checklist of clauses or findings so nothing important is skipped, and keep the summary as a guide rather than a replacement for reading key sections.

## Measuring accuracy per field
```
| Field | Checked | Correct | Accuracy |
| supplier_name | 50 | 50 | 100% |
| invoice_date | 50 | 48 | 96% |
| total_amount | 50 | 49 | 98% |
| line_items | 50 | 44 | 88% |
```
Set a minimum accuracy per field before automation; weaker fields stay in review until improved.

## Classification and routing
Before extraction, classify each document by type (invoice, credit note, receipt, contract, other) and route it to the right schema. Misclassified documents are a common source of errors, so include "other" and "unclear" categories that go to a person.

## Keeping the link to the source
Store the file name or link, page numbers and, for contracts, the quoted clause with every extracted value. Reviewers can then check values in seconds, auditors can trace any figure and corrections can be fed back as new examples in the prompt.

## Using Claude Code for batches
For one-off backlogs, put documents in a project folder and ask Claude Code to extract a sample of 20, show results, then process the rest into a spreadsheet with a validation report. Check totals and a random sample before importing anywhere.

## Retention and privacy
Decide how long source documents and extracted data are kept, who can access them and where they are stored. Remove personal data that is not needed for the task, use approved tools for sensitive documents and record where each document was processed. For CVs and other personal documents, extract facts for human reviewers rather than ranking people automatically, and check employment and data protection rules in each country.

Review accuracy monthly per field.

## Pipeline design
```
1. Intake: email inbox, upload folder or scanner drop
2. Classify: document type and language
3. Extract: schema per type, JSON output
4. Validate: totals, dates, formats, duplicates, lookups
5. Route: pass -> system; fail -> review queue
6. Review: person checks source beside extracted fields
7. Post: write to accounting, CRM or database with source link
8. Learn: add corrected examples to the prompt monthly
```

## Tool options
| Need | Options |
|---|---|
| Occasional batches | Claude Code or an assistant with file upload |
| Ongoing intake | Automation platform with an AI step and storage |
| High volume or regulated | Dedicated document AI platforms with audit trails |
| Spreadsheets and tables | Ask for table extraction to CSV, then validate totals |
Choose by volume, sensitivity and the systems results must reach.

## Handling tables and line items
Tables are the hardest part of many documents. Ask the model to extract each row as an object with fixed fields, keep the original order, mark merged or unclear cells and check that row totals and column sums match the document's totals. For multi-page tables, process each page, then merge and re-check totals.

## Contract review checklist example
| Item | Extract |
|---|---|
| Parties | Legal names and roles |
| Term | Start, end, renewal and notice period |
| Fees | Amounts, payment terms, increases |
| Liability | Caps, exclusions, indemnities |
| Termination | Rights, notice, consequences |
| Data | Processing terms, locations, sub-processors |
| Unusual clauses | Anything outside the standard template |
Each item includes the clause text and page; the summary supports, but never replaces, legal review.

## Prompts for summaries
For reports and long documents, ask for: the main conclusion, key numbers with page references, risks, recommendations and open questions, under a word limit, followed by a list of sections the summary did not cover. That last list tells readers what to check themselves.

## Common failure causes
| Failure | Cause | Fix |
|---|---|---|
| Wrong dates | Day-first and month-first formats | State expected formats per country |
| Missing line items | Multi-page tables | Page-by-page extraction and merging |
| Wrong supplier | Logo text versus legal name | Use legal name and VAT number lookup |
| Swapped amounts | Net and gross confused | Validate net plus tax equals total |

## Measuring business value
Track documents processed, the share passing automatically, review time per document, errors found after posting and hours saved each month. Report these alongside accuracy per field so finance and operations leaders see both the savings and the quality, and so decisions about expanding to new document types rest on evidence.

## Prompt improvement loop
Each month, collect corrected review items, add two or three representative corrections as examples in the extraction prompt, re-run the accuracy test and keep the change only if accuracy rises without new errors elsewhere.

## Volume planning
Estimate monthly document counts, peak days and pages per document before choosing tools, since cost and processing time scale with pages, and plan review capacity for the share that will fail checks.

## Edge cases and judgement calls
| Situation | What to do |
|---|---|
| Poor scans or handwriting | Higher review rate; request better copies |
| Many languages | State expected languages; validate formats per country |
| New layouts | Add examples; monitor accuracy for that supplier |
| Multi-page tables | Process page by page; merge with checks |
| Sensitive personal data | Minimise fields; approved tools; retention rules |
| CV screening | Extract facts only; avoid scoring people on protected characteristics; human decisions |

## Handoffs to related skills
- Prompts: `prompt-engineering`
- Automation around extraction: `no-code-automation`
- Testing accuracy: `ai-evals-testing`
- Review queues: `human-in-the-loop`
- Privacy: `ai-security-privacy`
- Claude Code batch processing: `claude-code-for-work`

## Worked example
A finance team typed 600 supplier invoices a month into its accounting system. The new workflow extracted fields with a JSON schema, validated totals, line items, dates and supplier names, blocked duplicates and sent failures to a review queue. Testing on 50 invoices showed 97% field accuracy, with errors mostly on poor scans. In production, about 85% of invoices passed automatically, the rest took a quick review and data entry time fell from around 40 hours to under 10 a month.

## Common mistakes
- No schema, so outputs vary.
- Letting the model calculate or guess missing values.
- No validation checks.
- No accuracy testing before scaling.
- Final decisions without human review.

## Output format
```
1. Field schema
2. Extraction prompt
3. Validation rules
4. Review routing rules
5. Accuracy test results
6. Integration and monitoring plan
```

## Self-check before you answer
- Is there a strict schema with null for missing fields?
- Are automatic validation checks defined?
- Do failures go to human review?
- Was accuracy measured on real samples?

---
Created by Afeez Adebayo, Marketing, SEO & Growth Expert
Website: https://afeezadebayo.com
LinkedIn: https://www.linkedin.com/in/afeez-adebayo/
X: https://x.com/za_icon
Source: https://afeezadebayo.com/skills-md/productivity/ai-workflows-automation/document-processing/

Licence: CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/). You may copy, share and adapt this skill, including for commercial use, as long as you credit Afeez Adebayo and link to the source URL above. Keep this notice in any copy or adapted version.

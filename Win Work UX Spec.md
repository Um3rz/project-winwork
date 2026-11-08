# Win Work UX Spec

## Design principles

Win Work feels like a CRM for tenders. Bids are written in the client's own Word and Excel files; Win Work tracks, drafts, checks and reports around them and connects through mail and drive connectors instead of a new editor.

1. **One card per tender.** Everything about a tender (documents, quotes, draft, decisions) lives on its card.
2. **Work where people already work.** Supplier talk stays in email, bids stay in the client's Word file, prices stay in Excel; connectors bring Win Work to them.
3. **Don't rebuild Word or Excel.** We build the pipeline, checklists, quotes, departments, evidence and the agent; documents and spreadsheets stay in their own tools.
4. **Show the source.** Every AI answer shows the document it came from; anything without evidence is a visible blank, never invented.
5. **Human presses send.** The agent drafts emails, answers and exports; a person approves anything that leaves the company.
6. **Get better in layers.** The app works from the tender alone; each extra piece of company data visibly improves the bid.
7. **Deadlines first.** Every screen shows what is due next and what is blocking it.

## Initial customer and focused product boundary

Win Work starts with **Saudi electrical contractors bidding on equipment-heavy government and utility tenders**. Typical work includes cables, switchgear, transformers, substations and related electrical works. The first users are small bid teams that still coordinate tender documents, supplier prices and company evidence through Word, Excel, email and shared folders.

The first product has one promise:

> Turn the buyer's tender files, supplier prices, Saudi local-content requirements and the contractor's approved company evidence into a checked submission package.

The first product is not a general proposal tool, a tender-discovery marketplace or a CRM for every type of contractor. All examples, templates, rules, terminology and tests are for this electrical-contractor workflow until it is proven with paying customers.

### MVP user journey

1. **Upload the tender pack:** the bid manager uploads the tender booklet, bill of quantities and buyer forms.
2. **Confirm what was extracted:** Win Work shows requirements, deadlines, priced lines and required documents. A person corrects or confirms them before drafting starts.
3. **Add proof and prices:** the user uploads approved company evidence and supplier quotes or connects the chosen mailbox and shared drive. Win Work drafts quote requests, reads supplier replies and keeps quote revisions linked to the tender; a person sends messages and approves prices.
4. **Check the bid:** Win Work links evidence to requirements, checks certificate dates, flags local-content and mandatory-product gaps, and compares supplier quote lines.
5. **Draft selected answers:** the user chooses which technical answers to draft. Every factual claim points to an exact source passage; unsupported points remain visible gaps.
6. **Create and control the submission package:** Win Work produces the confirmed requirements matrix, priced schedule, selected draft answers, missing-items list and Etimad-oriented submission checklist. Shared-folder versions are tracked, and approval is tied to the exact file version reviewed.

### MVP surfaces

The MVP has seven main product surfaces rather than treating every item in the full catalogue as a separate product:

1. **Today:** deadlines, approvals, missing quotes, expiring certificates and brief actions.
2. **Tenders:** a deadline-focused list and pipeline with status and blockers.
3. **Tender workspace:** Summary, Requirements, Quotes and pricing, Bid view and Package tabs, including supplier threads and quote revisions.
4. **Company brain:** approved projects, certificates, policies, people, products, past bids and prices, with confirmation and access controls.
5. **Departments and team work:** assignments, asks, reminders, reviewer links and progress across tenders.
6. **Insights and chat:** confirmed bid-history metrics, sourced findings and questions over company evidence and predefined metrics.
7. **Review and export:** unresolved gaps, source checks, price approval, document versions and downloadable submission files.

The full screen catalogue below remains the long-term product design. Screens not represented by these seven surfaces are post-MVP.

## What the UI resembles

Win Work is a CRM plus a read-only bid viewer, not a document editor and not a canvas.

| Part | Closest to |
| --- | --- |
| Tenders pipeline | Pipedrive or HubSpot deals board |
| Tender card with tabs | A CRM record page, like a Salesforce opportunity |
| Bid view | A view-only Google Docs link with comments, plus a checklist side panel |
| Departments | CRM accounts and contacts |
| Email and drive connections, Excel connector | Streak-style email linking and shared-folder sync |

### Map view (later)

A canvas works as one view of the data, never as the main UI: bids are long, structured, deadline-driven documents that need lists, tables, status and export.

- **Toggle:** Board, Table and Map on the pipeline, the tender card and the company brain.
- **Tender map:** requirements, departments, suppliers, quotes and answers as linked nodes, showing who owes what at a glance.
- **Brain map:** projects, people, certificates and products as a graph, with gaps highlighted.
- **Rule:** the map is a view, not a separate document; clicking a node opens the real item and nothing lives only on the canvas.
- **Order:** read-only auto-layout first, then drag to reassign owners. Build after the core flow works.

## App map

&#91;embedded content: app map · 8 sidebar areas, 6 card tabs, 5 connections\]

The sidebar holds eight areas; five of them (pipeline, brain, suppliers, departments, packs) feed the tender card, and every connection writes into a card rather than keeping its own copy.

## User flows

&#91;embedded content: main user flow · 1 decision, 1 learning loop\]

Quotes and drafting start together after Go; prices flow into the bid, and every result feeds the company brain that the next bid draws on.

### F1 First run

1. Sign up, pick country and industry packs.
2. Drop the first tender (or try the sample).
3. See the summary, requirements and go/no-go score within minutes.
4. Optional: connect email and drive, upload past bids.

### F2 New tender

1. Add it: upload, forward email, Chrome extension or tender alert.
2. Watch it read: requirements, deadlines, priced items found.
3. Decide Go or No-go (reason saved).
4. Card moves to Quotes and Drafting at once.

### F3 Supplier quotes

1. Priced items grouped into packages.
2. Pick suppliers per package (suggested from history).
3. Agent drafts requests; the user sends them from their own mailbox.
4. Replies are linked automatically; prices, lead times and exclusions read in.
5. Comparison and negotiation brief; the user negotiates and chooses.
6. Chosen prices flow into the price schedule.

### F4 Draft the bid

1. Press **Draft all** on the tender card, or redraft one answer at a time; the draft DOCX lands in the shared folder in the client's template.
2. Fill blanks through layer prompts; assign questions to departments.
3. Edit in Word; Win Work checks in on the file and updates status and bid strength.
4. Send to review.

### F5 Review

1. Reviewer sees red and amber answers first.
2. Approve or request changes per section.
3. Final approval unlocks export.

### F6 Export and submit

1. Use the final Word file, export PDF or XLSX, or fill the buyer's own forms (written into a copy).
2. Add the AI-use statement if the buyer asks.
3. Follow the submission checklist; the client uploads to the portal.
4. Mark as submitted with receipt.

### F7 Outcome

1. Record win or loss and value.
2. Upload evaluator feedback; lessons are saved to the brain.
3. Reports update; card is archived.

## Screens in the web app

Twenty-one screens; the tender card (S5) with its bid view (S9) and quotes (S7) is the heart of the product.

### S1 Onboarding wizard

- **Three ways to start** on the first screen:
  - **Start blank:** drop a tender; the AI works from the tender alone (layer 0).
  - **Start from template:** pick a country and industry pack; get starter answers, checklists and a suggested list of departments.
  - **Import past work:** connect folders and a mailbox or upload past bids, tenders, quotes and certificates; the history import fills the company brain and produces the Bid history report (S19) within a day.
- All three end on the first tender card; users can mix them later, nothing is locked.
- **Optional setup**, each step with **Skip for now**: add departments and their points of contact (S18), import suppliers (CSV or email history), add references (past projects), connect email and drive.
- Ends on S4 (tender intake) so the first value comes in minutes.

### S2 Home (Today)

- **Left column, "Due soon":** tenders sorted by deadline, each with days left and what blocks it ("2 quotes missing", "review pending").
- **Middle, "Needs you":** approvals waiting, supplier replies to read, emails drafted and ready to send, gaps to fill.
- **Right, "Alerts":** certificates expiring, new matching tenders, law or pack updates.
- Top bar: global search, **+ New tender**, notifications, workspace switcher.

### S3 Tenders pipeline

- **Board view (default):** columns Found → Go/No-go → Quotes → Drafting → Review → Submitted → Won / Lost.
- **Card shows:** buyer, title, value, deadline chip (red under 3 days), owner avatar, bid strength %, quotes received x/y.
- Cards **move by themselves** when events happen (all quotes in → Drafting; reviewer approves → ready to submit); a small "moved automatically" note with undo.
- **Table view toggle:** sortable, filters by country, industry, owner, stage; export CSV/XLSX.

### S4 Tender intake

- **Ways in:** drag and drop files or a zip, paste a portal link, forward an email to a personal inbox address (tenders@…), Chrome extension, or pick from tender alerts.
- **Choose where to start:** Full pipeline (selection → pricing → compliance → bid), **Pricing only**, **Compliance check only** or **Bid draft only**. The app asks only for the inputs that stage needs (e.g. a bill of quantities for pricing); other stages can be added later on the same tender card.
- **Reading progress:** "Reading 214 pages… found 86 requirements, 3 deadlines, 12 priced items."
- Lands on S5 with the summary ready, or straight on the chosen stage.

### S5 Tender card (overview)

- **Header:** buyer, title, reference, deadline countdown, stage dropdown, owner, bid strength meter, **Export** button.
- **Tabs:** Summary · Requirements · Quotes · Bid view · Documents · Activity.
- **Summary tab:** one-paragraph brief, key dates (clarification deadline, submission deadline), evaluation weighting (price vs quality), mandatory documents, eligibility checks ("local content certificate required: you have it / missing").
- **Go/No-go panel:** fit score with reasons (experience match, certificates, capacity, deadline risk) and buttons **Go**, **No-go** (with reason, saved for learning), **Ask a question** (drafts a clarification question to the buyer for the client to send).

* **Departments strip** under the header: each department's progress on this tender (e.g. Engineering 3 of 5 done, HSE 1 overdue); a click opens that department's asks.

### S6 Requirements checklist

- Every requirement extracted from the tender: ID, text, section, type (mandatory / scored / pricing / document), page link.
- **Status per row:** answered, partly, blank, not applicable; owner; linked answer.
- Filters: show only mandatory, only blanks, only mine.
- Doubles as the **compliance table** exported with the bid.

### S7 Quotes workspace

- **Items to quote:** lines pulled from the bill of quantities or specs (item, spec, quantity, unit, delivery date), grouped into packages (cables, transformers, civil works).
- **Suppliers per package:** suggested from the supplier list and past quotes; tick who to ask.
- **Request status table:** supplier, sent, opened, replied, price, lead time, validity, exclusions, spec compliance (met / partly / not met), chasers sent.
- **Comparison view:** side-by-side quotes per package, cheapest and fastest highlighted, non-compliant items flagged.
- **Negotiation brief** per supplier: past prices, best alternative, suggested points to push.
- **Choose** a quote per package → feeds the price schedule.

### S8 Email drafts (in the app and in the user's own mailbox)

- Agent-drafted quote requests, chasers, clarification questions and negotiation replies.
- Shows what it will attach (spec extract, drawing, quantities) and which tender card it links to.
- **Send** is always a human click from the client's own mailbox; drafts are created there through the mail connector and can be edited freely.

### S9 Bid view and draft check

Bids are written in the client's own Word template, with Excel for prices; Win Work does not ship a document editor. S9 is a read-only view of the latest file plus a side panel that explains and improves each answer.

- **Layout:** left, the outline in the buyer's order with status dots; middle, the bid rendered read-only from the latest file, each answer with a status chip, source chips and a word count; right, the side panel for the selected answer.
- **Blanks** show as yellow placeholders in the draft; the panel lists exactly what proof would fill them.
- **Bid strength meter:** e.g. 62%, with the top 3 things that would raise it ("add 2 references: +15%").
- **Last checked** time with a **Check now** button; version compare shows what changed since the last check.
- **Quick draft box:** for a single answer before any file exists, a plain text box with the agent and no formatting engine; the text flows into the Word draft.

**How the draft and the file stay in sync (check-in model)**

1. The agent writes the draft DOCX into the tender's shared folder (Drive, OneDrive or SharePoint) in the client's template. Each answer carries a hidden requirement ID (a bookmark or content control).
2. From then on Word is the source of truth. Win Work never writes over the client's edits.
3. When the file changes, Win Work re-reads it, matches text to requirements by those IDs (falling back to headings and wording if the IDs are removed) and updates each status: answered, blank, over limit, compliance gap.
4. **Regenerate section** gives a suggestion in the panel or a separate file; the user pastes it into Word. Nothing is overwritten.
5. The final file is what the system learns from.

**Side panel (opens for the selected answer)**

| Tab | Shows |
| --- | --- |
| Requirement | Tender text, source page link, scoring weight, word or page limit, mandatory flag |
| Evidence | Sources found in the draft, suggested sources from the company brain, a search box, and **Add source** for missing proof |
| Agent | **Suggest redraft**, **Improve for scoring**, **Shorten**, **Translate**, custom instruction box; says what data it used and what is missing |
| Quotes and products | Supplier quote lines and spec-compliance rows linked to this answer |
| Comments and owner | Assignee, department, due date, comments, status (blank, drafted, reviewed, approved) |
| File history | Check-ins, who changed what, and what changed since the last check |

**Reviewers and directors**

- Open a read-only share link; no Word needed.
- Comment, approve or request changes per section; comments post to the tender card while edits stay in Word.
- Works on a phone.

**Behaviours that matter**

- The panel is **contextual**: select a different answer and every tab changes with it.
- **Source chips** under each answer open the original document at the right page.
- **Live limits:** word and page counts read from the file turn red when over the buyer's limit.
- A real Word side panel is built later, and only if users ask for it.

### S10 Review mode

- Reviewer sees only what needs eyes: low-confidence answers, blanks, compliance failures, pricing totals.
- **Approve / request change** per section; final **Approve bid** unlocks export.
- Checklist: all mandatory requirements met, page limits, signatures needed, attachments present.

### S11 Export and submit

- **Formats:** the draft DOCX in the client's own template, plus PDF, XLSX and CSV on demand, and **fill the buyer's own forms** (their Word and Excel files; answers are written into a copy, never over the original).
- Optional AI-use disclosure statement where the buyer asks.
- **Submission checklist** for the portal (files, names, sizes, order), then **Mark as submitted** with date and receipt upload. Win Work never submits.

### S12 Outcome and debrief

- **Won / Lost / Withdrawn** with contract value and award date.
- Upload evaluator feedback or scores; the agent turns them into lessons ("lost 12 points on mobilisation plan").
- Lessons attach to the company brain and to the matching pack question.

### S13 Company brain (library)

- **Sections:** Documents · Projects (references) · People (CVs) · Certificates (with expiry dates) · Policies · Products and datasheets · Past bids · Prices and quotes.
- **Brain strength** per section ("References: 4 of 10 recommended") with **Add** prompts.
- Each item shows where it was used and how bids scored with it.
- Connected sources (Drive, SharePoint, email) with sync status and folder picker.
- Every item shows its **original source, source version and brain status:** confirmed, inferred, needs review, restricted or superseded. The original system remains the source of truth.

* **Always processing, never automatically trusted:** anything that enters Win Work (uploads, connected folders, forwarded emails, supplier replies, drafts, final bids, award letters, chat attachments) is parsed into candidate facts and links. Confirmed information becomes reusable evidence; uncertain information stays out of metrics and drafting until reviewed.
* **Stable core, learned extensions:** tenders, requirements, projects, people, certificates, products, suppliers, quotes and outcomes use the fixed electrical-tender ontology. New categories, aliases or relationships found in client data appear as ontology suggestions for an admin to approve, merge or reject.
* **Please check** lists uncertain entity matches, conflicting facts and ontology suggestions, with a weekly **What the brain learned** panel.
* **Controls:** source permissions carry into the brain; exclude a folder, label or file; mark items restricted; deleting or disconnecting a source removes its searchable text, embeddings, derived facts and links; newer versions supersede rather than silently overwrite older ones.

### S14 Suppliers

- Supplier list with categories, countries, contacts, approved status.
- **Supplier profile:** quote history, average lead time, reply rate, prices over time, compliance issues, notes.
- Import from CSV or email history.

### S15 Templates and packs

- **Country packs:** law and rule references (each linked to the official source, dated, versioned), standard forms, submission rules.
- **Industry packs:** common questions with model answer structures, expected certificates, bid/no-bid checklist.
- **My templates:** the client's own bid templates, boilerplate and branded cover pages.
- "Updated" badges when a pack or rule changes.

### S16 Reports

- Win rate by industry, buyer and country; pipeline value by stage; time saved per bid; quote response rates; common loss reasons.

### S17 Settings

- **Team and roles,** connections (mail, drive and shared folders, Excel and Sheets, Chrome, MCP), data region (EU, UK, KSA), language, billing, AI-use disclosure default, data export and delete.

### S18 Departments

Departments are tracking pages the tender manager sets up for the internal teams they depend on; contacts need no login.

- **Departments list:** every department with open asks, overdue count and next deadline.
- **Setup:** add a department (name, colour) and its points of contact (name, role, email, phone). Templates suggest the usual list per industry: Engineering, Estimating, Procurement, HSE, Legal, HR, Finance.
- **Assigning:** on any requirement, section or document request in a tender, **Assign to department** with a due date; it appears on that department's page.
- **Department page:**
  - **Work:** all asks across all tenders (item, tender, status, due date).
  - **Deadlines:** soonest first, overdue in red.
  - **Data:** files and answers the department provided, saved to the company brain for reuse.
  - **Correspondence:** emails with its contacts, linked automatically by the email add-in when a contact's address matches.
- **Quick actions:** **Request input** (drafts an email to the contact with the questions, files and due date; a human sends it), **Chase**, **Mark received**, **Attach file**.

### S19 Insights (bid intelligence)

The first screen a new client values: what their own bid history says, before any bid is drafted.

- **Bid history report:** after the history import, 5–10 headline findings in plain words (e.g. which buyers they win with, which suppliers answer, where margins differ between won and lost bids), each with its sources and a confidence label.
- **Dashboards (tabs):** Outcomes · Buyers · Pricing and margin · Suppliers · Compliance · Capability · Effort · Loss reasons · Opportunities (recompete radar).
- **Filters:** date range, buyer, sector, tender size, region; every chart opens the tenders behind it.
- **Confirm list:** uncertain links from the import ("is this quote for that tender?").
- Margin is labelled **estimated** until accounting data is connected.

### S20 Chat and modes

- **Chat** with the bid intelligence agent from any screen (side panel) or full page: "Which buyers do we win with?", "What did we quote for 132kV cable last year?", "Which certificates expire before the SEC tender?", "Where do we lose points?". Answers cite sources and can include a chart.
- **Mode switch** on every tender and in settings:
  - **Chat:** answers only.
  - **Plan:** the agent shows a step-by-step plan with what each step will do and use; the user approves, edits or removes steps before it runs.
  - **Auto:** runs selection, pricing, compliance and bid on its own and stops at the gates.
- A **plan card** on the tender shows steps, status and approvals; the activity log records every step.

### S21 Briefs

- **Daily brief:** deadlines this week, quotes received, approvals waiting, certificates expiring, new matching tenders.
- **Weekly brief:** pipeline value, bids submitted, wins and losses with reasons, supplier response rates, what to fix.
- **Settings:** time, days, recipients, sections; delivered in the app and by email (WhatsApp later); each item has a one-tap action (approve, open, chase).

## Connections and add-ins

Win Work connects to the tools clients already use, mostly from the server through connectors (MCP or the vendor's API) instead of building panels inside each app. Everything writes into the same tender cards; nothing is a copy of the web app.

| Connection | How it works | What it does | Priority |
| --- | --- | --- | --- |
| Mail connector (Gmail, Microsoft 365) | Server-side through MCP or the vendor API; no panel to install | Reads supplier threads and links them to the right tender and supplier by address and subject; labels each thread per tender; reads price, lead time and validity into Quotes; creates quote requests, chasers and negotiation replies as drafts in the user's own mailbox, and the human sends | 1st |
| Drive connector (Google Drive, OneDrive, SharePoint) | One shared folder per tender | Writes the draft DOCX in the client's template; watches the folder and reads the file back at each check-in; imports past bids and templates | 1st |
| Read-only bid view | Web link (S9) | Shows the latest file with status, sources and gaps; reviewers comment and approve | 1st |
| Excel and Sheets connector | API on the shared price file | Fills unit prices from chosen quotes plus the client's margin; flags missing lines; reads totals back to the tender card | 2nd |
| Win Work MCP server | Added by the client's admin to Copilot, Claude or ChatGPT | Exposes tools such as get requirements, get evidence, get quote comparison and list gaps, so a user can say "fill section 3.2 from Win Work" inside their own AI tool | 2nd, optional |
| Chrome extension | Popup on a tender portal page | **Save tender** with its files and deadlines from portals such as Etimad or Find a Tender; shows fit score; never submits or fills portal forms | 2nd |
| Mobile (PWA) | Phone home screen | Deadline alerts, approve or reject sections and emails, read supplier replies, mark submitted | 3rd |
| Word side panel | A real Word add-in | Requirement list and gap flags inside Word | Only if users ask |

**Limits to plan for**

- Microsoft 365 and Google Workspace often need admin consent for these permissions, which adds sales friction and security review.
- Word offers little API for editing content in place, so Win Work writes whole files and reads them back instead of editing inside them; check current API limits before committing.
- Without a live panel, make up for it with a per-tender mail label, a daily digest and the read-only view.
- The MCP server depends on the client's admin enabling it and on the host AI's output quality, so it is a bonus channel, not a core one.

## Architecture

&#91;embedded content: architecture · 4 layers, 3 outside systems\]

Four layers sit inside Win Work: clients, an API gateway, core services and data. The client's AI tools, AI models and mail, drive and sheet accounts connect from outside, and everything is scoped to one client.

- **Clients:** web app, read-only bid view link, Chrome extension and mobile PWA. A client's own AI tools reach Win Work through the MCP server.
- **API gateway:** sign-in, tenant isolation, the REST API and the Win Work MCP server in one place.
- **Core services:**
  - **Tender intake** reads files and extracts requirements, deadlines and priced items.
  - **Quotes and suppliers** handles requests, replies and comparison.
  - **Draft agent** writes answers from the client's evidence and drafts the DOCX.
  - **File check-in** reads the client's file back and updates status.
- **Connectors:** mail, drives and sheets through MCP or the vendor API, using the user's own accounts.
- **Data:** Postgres (client data, graph tables, vector search), document storage, country and industry packs, and the audit log.
- **AI models:** language models, OCR and embeddings, called by intake, the draft agent and check-in; no client's data trains anything used for another client.
- **Rules for every client:** separate tenant data, Saudi region hosting, and a human approves anything before it is sent or added to the final package.
- **Stack:** Next.js front end, FastAPI backend, Pydantic-validated AI steps, a Postgres job queue, Postgres with pgvector in Dammam, and Better Auth. Temporal and the fuller agent runtime arrive only in the post-MVP agentic phase; Langflow and n8n are for experiments only.

### Agent runtime (agent substrate)

Each agent job (intake, draft, check-in) runs in its own isolated sandbox, so one client's files and credentials never share a machine process with another's.

1. **MVP:** bounded parsing, checking, quote-reading, drafting and file-check-in jobs run from a Postgres queue in separate Cloud Run job executions.
2. **Agentic phase:** Temporal coordinates multi-day workflows only after timers, approvals and recovery outgrow the queue.
3. **Scale:** GKE Agent Sandbox provides one gVisor-isolated sandbox per job when isolation or volume requires it.
4. **Density later:** Agent Substrate may sit on top when idle agents become a measured cost problem.

Agents never see credentials: an egress proxy adds the client's mail and drive tokens to outgoing calls. Full detail is in the technical plan.

## Agent workflows (Langflow)

**Stack note:** in production these five flows run as Pydantic AI agents inside Temporal workflows (see the technical plan); Langflow is used to sketch and test them first.

Langflow runs the agent work as five flows; the FastAPI backend stays in charge of state, approvals and which client a request belongs to, and calls each flow through its webhook.

| Flow | Trigger | What it does | Writes |
| --- | --- | --- | --- |
| 1. Intake | New tender files | Parses PDFs with page numbers, extracts requirements, deadlines, scoring rules and priced items | Requirements and checklist on the card; tender text indexed for search |
| 2. Quotes | Go decision, or a new supplier email | Drafts one quote request per package; reads replies into price, lead time, validity, exclusions | Mail drafts (never sent); quote rows |
| 3. Draft | **Draft all** or a single redraft | Answers each requirement from the client's evidence and builds the DOCX | Draft file in the shared folder; statuses and bid strength |
| 4. Check-in | Draft file changed | Reads the file back, matches answers to requirement IDs, checks limits and gaps | Status per requirement; gap list |
| 5. Learn | Outcome recorded | Turns win/loss and evaluator feedback into lessons | Lessons in the company brain |

### Draft flow in detail

&#91;embedded content: Langflow draft flow · 1 loop, 3 tools, 4 finishing steps\]

The agent runs once per requirement and returns structured data; sorting by status happens after the loop, because Langflow's If-Else component cannot sit inside a Loop.

1. **Webhook** receives tender ID and client ID (API-key protected).
2. **Get requirements** (API Request) pulls the checklist from Win Work.
3. **Loop** sends one requirement at a time to the agent.
4. **Answer agent** (Agent component) has three tools:
   - **Search brain:** vector search over the client's documents, filtered to that client only.
   - **Quotes lookup:** chosen supplier prices and spec compliance for the tender.
   - **Pack rules:** country and industry pack guidance, via a Run Flow sub-flow.
5. The agent's **Structured Response** returns: answer text, sources (document and page), blanks to fill, confidence, word count. It goes back to the Loop's Looping port.
6. **Split by status** (Data Operations) separates answered, partly answered and blank items after the loop is done.
7. **DOCX writer** (custom Python component using python-docx) fills the client's template and adds a hidden requirement ID to each answer.
8. **Save to drive** (MCP Tools, drive connector) uploads the file to the tender's shared folder.
9. **Update card** (API Request) posts statuses, bid strength and the file link back to Win Work.

### Guardrails built into the flows

- **No send tool exists.** The mail connector exposes only "create draft", so no flow can send an email.
- **Client-scoped search.** Every vector search and API call carries the client ID; no flow can read another client's data.
- **Evidence or blank.** The agent's output schema requires a source for every claim; anything without one comes back as a blank.
- **Approval gates.** Human-in-the-loop approval can gate drive writes during the pilot.
- **Hosting.** Langflow is self-hosted per region (EU, UK, KSA) next to the data, with webhook authentication on.
- **Swappable engine.** Flows are versioned and called through one internal API, so any flow can later move to plain Python if Langflow limits it.

## Agent behaviour and trust patterns

The agent can do almost any step, but the UI always shows what it used, what it guessed, and what waits for a human.

| Pattern | How it looks | Why |
| --- | --- | --- |
| Source chips | Small chips under each answer naming the document, page or project used; click opens it | Reviewers check any claim in one click |
| Visible blanks | Yellow placeholder like \[add ISO 45001 certificate\] instead of invented text | A false claim can get a bidder excluded |
| Confidence colour | Green (well sourced), amber (partly), red (no evidence); review mode shows amber and red first | Review time goes where risk is |
| Approve before send | Every email, export and stage change to Submitted needs a human click | Client stays the bidder; GCC rules ban intermediaries |
| Agent activity log | Activity tab lists every agent action with time, inputs and result; undo where possible | Trust and audit trail |
| Agent mode switch | Per client and per tender: Chat (answers only), Plan (proposes a plan and asks permission), Auto (runs every stage, stops at the approval gates) | Users pick their comfort level |
| Rule citations | Country-pack rules show the law or guidance name, date and link, labelled guidance, not legal advice | No invented rules |
| Data boundary note | "Uses only your company's data" badge in the agent panel | Supplier prices and bids never cross clients |

## Roles, empty states and layer prompts

### Roles

| Role | Can do |
| --- | --- |
| Owner / director | Go/No-go, final approval, pricing margin, billing |
| Bid manager | Everything on tenders, assign work, send emails |
| Contributor (engineer, estimator) | Answer assigned questions, add documents, comment |
| Reviewer (internal or Win Work reviewer) | Review mode, comments, approve sections |
| Viewer | Read only |

### Empty states teach the next step

- **No tenders:** big drop zone, "Drop a tender PDF or forward one to tenders@…" plus a sample tender to try.
- **No suppliers:** "Import from email" and "Upload CSV".
- **Empty brain section:** shows what good looks like ("Most winning bids include 3 to 5 references") and an **Add** button.

### Layer prompts (the brain grows bid by bid)

Prompts appear inside the bid view at the moment data would improve the current bid, never as a long onboarding form.

1. **Layer 0, tender only:** draft with blanks; prompt "Upload 3 past bids to write in your own voice."
2. **Layer 1, past bids:** tone and best past answers used; prompt "Add CVs and certificates to fill 14 blanks."
3. **Layer 2, proof:** blanks filled with evidence; prompt "Connect email to collect supplier quotes automatically."
4. **Layer 3, products and suppliers:** spec compliance and quotes; prompt "Record the result to learn what wins."
5. **Layer 4, results:** lessons from wins and losses shape future drafts.

Each prompt shows the gain ("+18% bid strength") and a **Not now** option.

## MVP and post-MVP build order

The product grows toward the complete screen catalogue without changing customer type. Every stage continues to serve Saudi electrical contractors bidding on equipment-heavy government and utility tenders.

### Phase 0: paid concierge proof

- Run real electrical tenders with two or three pilot contractors using internal tools and manual document handling.
- Validate the smallest repeatable package: confirmed requirements matrix, checked supplier prices, evidence gaps, selected drafted answers and submission checklist.
- Record time spent, corrections required, document failures and what the client is willing to pay per tender.
- Do not build a connector or autonomous agent until the same need repeats across pilots.

**Exit gate:** at least two contractors pay for the package, use it on a live tender and say they would purchase it again.

### Phase 1: MVP — connected tender, team and intelligence product

- Build the seven MVP surfaces: Today, Tenders, Tender workspace, Company brain, Departments, Insights and chat, and Review and export.
- Support direct upload of PDF, DOCX and XLSX tender files, supplier quotes and company evidence.
- Extract requirements, deadlines, priced lines and document obligations, but require confirmation before they affect the package.
- Provide electrical-sector and Saudi local-content checks, selected-answer drafting with exact source passages, visible gaps and human price approval.
- Export a requirements matrix, priced schedule, draft DOCX and submission checklist. The customer remains responsible for final Word formatting and Etimad upload.
- Use Arabic and English from the start, including mixed right-to-left and left-to-right content in the tested export templates.
- Include S7 Quotes, one mail connector and one drive connector based on pilot usage.
- Create quote-request drafts, read supplier replies, compare revisions and feed approved prices into the schedule.
- Add shared-folder versions, read-only bid view and approval tied to an exact file version.
- Add Excel/Sheets price write-back for the chosen price file.
- Add S12 Outcomes so wins, losses and evaluator feedback can be recorded.
- Add the fuller S13 Company brain as a source-linked, rebuildable projection with approval, inferred, needs-review, restricted and superseded states; use a stable core ontology plus human-approved suggestions from client data.
- Add S18 Departments, assignments, reminders, reviewer links and S2 Today.
- Add packs for the electrical products and tender types seen in paid customer work.
- Add history import, confirmed metrics, S19 Insights and sourced Chat mode.
- Add daily and weekly briefs after the underlying workflow data is reliable.

**Explicitly not in the MVP:** Plan and Auto modes, tender discovery, Chrome extension, MCP, ERP/CRM integrations, map view, mobile PWA, WhatsApp Business API, buyer-form automation and a Word add-in.

**Exit gate:** three paying contractors complete at least five live tenders; the product supports their complete bid teams; the exported package is usable without founder reconstruction; every factual draft claim is supported by an exact passage or marked for review; most supplier quotes and bid versions are captured without manual re-entry; there are no silent price or approved-version mismatches; Insights and chat use confirmed data with visible sources; briefs and assignments work from the same tender state; and the team knows the time and model cost per tender.

### Phase 2: agentic full product

- Expand Chat with agent tools, then add Plan, and only then Auto mode for workflows that have measured accuracy and safe approval gates.
- Add form filling, the Etimad Chrome extension, WhatsApp Business API and the supplier directory.
- Add the public API, MCP server and requested business-system connectors after repeated customer demand.
- Add mobile review, Word side panel, reports and map views only when usage evidence justifies them.

**Stop condition:** features for other contractor types, general-purpose proposal writing and new countries stay outside this roadmap. Revisit that boundary only after the Saudi electrical-contractor product has repeatable acquisition, retention and healthy per-tender margins.

**Future, department collaboration:** department members log in or answer through magic links, a "My asks" view per person, requirements routed to departments automatically by type (technical, safety, pricing, legal, CVs), and an assignment matrix per tender (sections by departments).

**Open questions**

- Which electrical tender subtype repeats most across the first pilots: supply and installation, maintenance, or project/EPC work?
- Which file cloud do pilot clients use, Microsoft 365 or Google Workspace? Build only that mail-and-drive connector in the MVP.
- Which two or three Arabic and bilingual Word/Excel template patterns cover most pilot submissions?

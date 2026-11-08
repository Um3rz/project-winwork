# Win Work Technical Plan

## Summary

Win Work starts as a focused submission-package product for **Saudi electrical contractors bidding on equipment-heavy government and utility tenders**. It turns tender requirements, supplier prices, Saudi local-content rules and approved company evidence into a checked package for human review and Etimad submission.

The complete agentic product described in this plan remains the destination, but it is no longer the MVP. Automation, connectors, Insights, departments and Auto mode are added only after the narrow workflow works repeatedly for paying electrical contractors.

- **One initial customer:** Saudi electrical contractors working on cables, switchgear, transformers, substations and related electrical works.
- **One MVP outcome:** a confirmed requirements matrix, checked prices, compliance and evidence gaps, selected drafted answers and a submission checklist.
- **Lean delivery:** start with paid concierge bids and direct file uploads; build connectors only after the workflow repeats.
- **One region and language pair:** Dammam hosting, Arabic and English, including mixed right-to-left and left-to-right documents.
- **Expansion boundary:** later stages deepen this customer's workflow. Other contractor types, general proposal writing and new countries are outside the roadmap until this segment is repeatable and profitable.

## Lean MVP

### Inputs and output

| Input | MVP handling |
| --- | --- |
| Tender booklet and appendices | Direct PDF or DOCX upload; extract requirements, dates, scoring rules and required documents |
| Bill of quantities or price schedule | Direct XLSX or PDF upload; extract priced lines and preserve the original file |
| Supplier prices | Upload quote PDFs, spreadsheets or email exports; a person confirms matched lines and revisions |
| Company evidence | Upload approved projects, certificates, policies, CVs and product datasheets into a small evidence library |
| Saudi rules | Versioned electrical-sector rules, required documents, local-content checks and mandatory-product references with official sources |
| Output | Confirmed requirements matrix, checked priced schedule, evidence and compliance gaps, selected draft answers, source report and Etimad-oriented submission checklist |

The system never submits a tender, sends supplier communication or silently changes the buyer's original files. The bid manager confirms extracted requirements, supplier-price matches and final package contents.

### MVP workflow

1. Create a tender and upload the tender files.
2. Parse the files and show requirements, deadlines, priced lines and required documents for correction and confirmation.
3. Upload company evidence and supplier quotes; match them to requirements and bill-of-quantity lines.
4. Run certificate-expiry, product-specification, local-content and missing-document checks.
5. Draft only the answers the user selects, using exact supporting passages and visible unsupported gaps.
6. Approve prices and export the submission package for final formatting and Etimad upload by the contractor.

### Lean MVP stack

| Area | Choice |
| --- | --- |
| Hosting | One Google Cloud project in Dammam: Cloud Run, Cloud SQL Postgres with pgvector and Cloud Storage |
| App | Next.js web app and FastAPI backend; four surfaces: Tenders, Tender workspace, Evidence library, Review and export |
| Jobs | A simple Postgres-backed job queue for parsing, extraction, checks and drafting; no multi-day autonomous workflow |
| Documents | Docling and Arabic OCR for reading; openpyxl for spreadsheets; docxtpl/python-docx for a small set of tested exports |
| AI | Pydantic-validated extraction and drafting steps behind LiteLLM; no general tender agent or Auto mode |
| Evidence | Hybrid search over approved tenant-scoped evidence; drafts store exact passage references, not only document names |
| Safety | Tenant isolation, encrypted storage, audit events, malware scanning, human confirmation and no send or submit capability |
| Operations | Automated deploys, database backups with restore tests, failed-job alerts, connector-free support and model-cost tracking per tender |

### Explicit non-goals

The lean MVP does not include history import, dashboards, Chat/Plan/Auto modes, mail or drive synchronization, automatic quote requests, departments, scheduled briefs, Chrome or Word add-ins, buyer-form automation, MCP, ERP/CRM connections, mobile apps, map views, tender discovery or expansion outside Saudi electrical contractors.

### MVP acceptance and stop condition

The MVP is complete when:

- Three paying Saudi electrical contractors use it across at least five live electrical tenders.
- Each user can correct and confirm extracted requirements before any drafting or compliance result is treated as final.
- The package contains the confirmed requirements matrix, approved price schedule, gap report, selected answer drafts and submission checklist.
- Every factual draft claim is linked to an exact supporting passage or is visibly marked for review.
- No supplier price enters the final schedule without human confirmation, and quote revisions remain traceable.
- Arabic, English and mixed-direction exports work on the limited template set agreed with pilots.
- A package is usable without founders rebuilding it manually, and time, human-review effort and model cost per tender are known.

Once these conditions pass, stop adding MVP scope and move to the post-MVP stages in the build plan.

## Post-MVP target: full Saudi agentic product

The full product covers the bid in four agent stages in this order: selection, pricing, compliance, bid. A tender agent moves each tender through them automatically and stops where a person must decide. These stages are introduced gradually after the lean MVP, not shipped together as the first release.

&#91;embedded content: full Saudi product pipeline · 4 agent stages, approval gates\]

In the full pipeline each stage starts as soon as the one before finishes or its gate is approved; any stage can also be started on its own. All four draw on the same company brain, supplier prices and Saudi pack.

### What each agent does

| Stage | Runs automatically | Saudi-specific | Human gate |
| --- | --- | --- | --- |
| 1. Selection | Reads the tender booklet (Arabic PDF and Excel); extracts requirements, deadlines, evaluation weights and qualification criteria; scores fit against the company brain (experience, certificates, capacity, deadline); recommends go or no-go with reasons | Contractor classification, local content mechanisms and weighting, mandatory national products, SME preferences | **Go / no-go** |
| 2. Pricing | Reads the bill of quantities; groups lines into packages; matches suppliers and past prices; drafts quote requests; reads replies; compares quotes; proposes a price build-up with margin; fills the priced bill of quantities | Prefers local manufacturers for mandatory-list items; SAR and 15% VAT; Arabic and English suppliers; WhatsApp as a common channel | **Send quote requests** (a person sends) and **approve prices** |
| 3. Compliance | Checks required documents and expiry dates; checks offered products against specs; checks mandatory-list items; estimates the local content score; lists gaps with fixes | Commercial registration, Zakat and tax certificate, GOSI, Saudization (Nitaqat), chamber membership, contractor classification, local content certificate, bid bond | None (flags only) |
| 4. Bid | Drafts the technical proposal in Arabic (English when asked) in the client's template, every claim sourced; fills financial forms from approved prices; builds the compliance table; builds the Etimad submission checklist | Arabic right-to-left documents; Etimad file rules | **Final approval**; the client uploads to Etimad |

### Start at any stage

Every stage is also a standalone product: a client can run all four in sequence, start in the middle, or use one stage on its own (only compliance, only the bid draft). Each stage has a typed input and output contract, so it does not care whether its inputs came from an earlier stage or from the client.

| Stage | Needs to start | If entered directly |
| --- | --- | --- |
| Selection | Tender files | Normal start |
| Pricing | Bill of quantities or price schedule (Excel or PDF); tender files optional | Reads the bill of quantities directly; asks only for missing delivery terms or currency |
| Compliance | Tender files or a requirement list, plus offered products and company documents | Runs a light requirement extraction first (no fit score, no go/no-go gate) |
| Bid | Tender files; approved prices optional | Builds the requirement list itself; leaves price fields as visible blanks if pricing was not done |

- **Light passes, not skipped gates:** when an earlier output is missing, the stage creates just what it needs (for example a requirement list) without that earlier stage's gate.
- **Own gates still apply:** a stage started on its own keeps its own gates (prices still need approval, the final bid still needs approval).
- **Join later:** a client who starts with compliance can add pricing or the bid later on the same tender card; nothing is redone.
- **Modes per stage:** Chat, Plan or Auto apply to whichever stages are switched on.
- **Sell stages separately (to test):** Fit Check, Pricing desk, Compliance check and Bid draft, each priced on its own, with the full pipeline as the bundle.

### Modes and gates

- **Three modes,** set per client and per tender:
  - **Chat:** answers questions from the brain and tenders; read-only.
  - **Plan:** the tender agent proposes a typed step-by-step plan ("read booklet, score fit, request 6 quotes, …") and asks permission before running it.
  - **Auto:** runs selection, pricing, compliance and bid on its own until the next gate.
- **Tender agent:** a state machine per tender; it starts each stage, schedules supplier chasers (e.g. after 2 days) and deadline alerts, and records every step in the audit log.
- **Gates in every mode:** go/no-go, sending quote requests, approving prices, final approval. Nothing is sent, priced or submitted without a person.

### Post-MVP agentic stack (one region)

| Area | First agentic choice | Later |
| --- | --- | --- |
| Hosting | One Google Cloud project in Dammam: Cloud Run (web, API, agent jobs), Cloud SQL Postgres with pgvector and Cloud Storage | GKE Agent Sandbox only if isolation or volume requires it; no additional regions in this roadmap |
| Agents | Pydantic AI: one agent per stage plus the tender agent | Same |
| Orchestration | Postgres job queue (Procrastinate) with retries and scheduled jobs; tender state machine in code | Temporal |
| Models | LiteLLM gateway; a frontier model under pilot agreements; evaluate in-Kingdom options such as Humain's Arabic-first ALLaM | In-Kingdom model for production data |
| Arabic | Docling plus OCR with Arabic support; multilingual embeddings (BGE-M3, self-hosted); right-to-left web UI (next-intl); Arabic Word templates | Arabic evaluation set grows with pilots |
| Documents | docxtpl and python-docx (right-to-left), openpyxl for the bill of quantities, LibreOffice for PDF | Fill buyers' own forms |
| Supplier channels | Email drafts in Gmail or Microsoft 365 (whichever pilots use); WhatsApp click-to-send links; replies read from email, uploads or forwarded messages | WhatsApp Business API |
| Tender intake | Upload, per-client email address | Chrome extension on Etimad |
| App | Next.js, FastAPI, Better Auth | SSO |
| Monitoring | Sentry; Langfuse self-hosted | OpenTelemetry, alerts |
| Saudi pack | Required-document list, local content rules, mandatory national products list loaded from LCGPA's published list, evaluation habits | Updated monthly; lawyer-reviewed |

**Not required before the agentic stages prove demand:** Temporal, GKE, Jev, the MCP server, other regions and native ERP or CRM connectors.

### Pilot safety baseline

- One region and one database are acceptable, but automated backups, tested restore, failed-job alerts and repeatable deployments are required before live tender use.
- Focused tests plus a growing Arabic evaluation set on real electrical tenders.
- Pilot clients sign a pilot agreement covering AI use and data; government-classified documents stay out until in-Kingdom models are in place.
- Security basics stay on from day one: row-level security, encryption, audit log, human gates, nothing sent without a person.

### Full agentic product is ready when

- A client connects a folder and mailbox and supplier quotes and bid versions are linked without silent mismatches.
- A real electrical Etimad tender runs end to end in Auto mode, stopping at the defined human gates, and produces an Arabic draft, priced bill of quantities and Etimad checklist.
- Every claim in a draft has a source or a visible blank, and nothing leaves the system without a person.
- The automated workflow performs better than the lean manual-assisted path on measured time, correction rate and cost.

## Post-MVP: Bid intelligence (Insights)

Insights is added after customers have enough clean tenders, quotes and outcomes to support useful analysis. It provides an always-on company brain, chat, briefs and dashboards over the electrical contractor's own bid history; the same approved information can then feed the bid agents.

### Always-on brain

- **Seeded at signup:** core types and links plus Saudi and industry pack fields exist before the first file arrives.
- **Everything flows in:** uploads, connected folders, forwarded emails, supplier replies, tenders, drafts, final bids, award letters and chat attachments all trigger the same pipeline (parse, classify, index, extract, match, link).
- **Cheap first, deep later:** every item is parsed and indexed at once; key types (certificates, quotes, award letters, bills of quantities) get full extraction immediately, bulky old tenders on demand; duplicates are skipped by fingerprint.
- **Controls:** exclude a folder, label or file; mark items private (kept for the tender, hidden from search and chat); deleting a file removes its facts, text and links; newer versions supersede older ones.
- **Visible:** an "Added to brain" note on each item, a "please check" list for uncertain matches, and a weekly "what the brain learned".

### History import and Bid history report

1. The client picks sources and a date range (e.g. the last 2–3 years): folders, mailboxes, Excel files.
2. Items are classified (tender, bid, bill of quantities, quote, award letter, rejection, certificate) and email is limited to tender and supplier threads.
3. Facts are extracted and linked: tender, bid, quotes, outcome, buyer, suppliers.
4. Metrics are computed and the client gets a report of 5–10 headline findings with sources, live dashboards and a short confirm list.

### Insights catalogue

| Area | Examples |
| --- | --- |
| Outcomes | Bids per month; win rate by buyer, sector, size and region; total won value; no-bid rate |
| Buyers | Top buyers by bids and wins; buyers never won; repeat buyers; time to award |
| Pricing and margin | Estimated margin per bid (bid price vs supplier cost); margin on won vs lost bids; price position vs the winner where award values are published |
| Suppliers | Top suppliers by quotes and wins; response rate and speed; price trends per item; lead times; single-supplier risk; local vs imported share |
| Compliance | Certificate expiry calendar; documents most often missing; local content score history |
| Capability | Sectors without references; staff skills from CVs; strongest past projects |
| Effort | Days per bid; contributors by department; where bids stall |
| Loss reasons | Technical vs price losses; repeated weak sections |
| Opportunities | Recompete radar for contracts ending soon; new tenders similar to past wins |

Real profit needs accounting data (an ERP connection or Excel import); until then the product shows estimated bid margin and labels it as such. Every figure shows its sources and how sure it is.

### Chat, briefs and dashboards

- **Chat agent:** Pydantic AI with tools for evidence search and **predefined metric queries**; no free-form SQL, so numbers stay correct and row-level security holds. Answers can include a chart.
- **Metric layer:** metrics defined once in Python over SQL views (win rate, margin, response rate, pipeline value, …) and used by chat, dashboards, briefs and the report alike.
- **Briefs:** scheduled jobs on the queue; daily (deadlines, quotes received, approvals waiting, expiring certificates, new matching tenders) and weekly (pipeline, results, supplier response, what to fix); delivered in the app and by email after Phase 3, WhatsApp later.
- **Dashboards:** Next.js with Recharts or Tremor, reading the metric layer.

### Packaging by product stage (prices to test)

| Offer | Includes | Available |
| --- | --- | --- |
| Concierge package | Founders and electrical bid expert produce the checked package with internal tools | Phase 0 |
| Submission package | Lean MVP upload, confirmed requirements, quote and evidence checks, selected drafting and package export; priced per tender | Phase 1 |
| Workflow | Mail/drive automation, quote workflow, document versions and outcomes | Phase 2 |
| Team and Insights | Departments, reusable knowledge, history metrics, chat and briefs | Phase 3 |
| Agentic bids | Plan and Auto modes for proven selection, pricing, compliance and bid steps | Phase 4 |

## Tech stack

This is the target stack for the full product. The lean MVP uses only the rows needed for its bounded upload-to-package path; later components are introduced at their roadmap gate. Langflow and n8n stay for quick experiments only.

| Layer | Choice | Why |
| --- | --- | --- |
| Web app | Next.js, TypeScript, shadcn/ui, TanStack Table and Query | Fast to build boards, tables and forms |
| Short-text editing | TipTap | Per-answer text boxes and comments only, no full document editor |
| Bid view (read-only) | DOCX rendered to HTML (mammoth) plus PDF preview | Shows the client's real file without building Word |
| API | FastAPI (Python), the only backend | All AI and document tools live in Python |
| Web to API link | OpenAPI schema → generated TypeScript client | No hand-written API calls |
| Agents | Pydantic AI (code-first) | Typed outputs (answer, sources, blanks), testable, versioned in git |
| Workflows | Postgres queue first; Temporal in Phase 4 if needed | Multi-day timers, approvals and crash recovery are added only after the bounded MVP workflow proves demand |
| Database | Cloud SQL Postgres in Dammam, pgvector, full-text search | One Saudi data plane for the committed roadmap |
| Graph | Postgres edge tables | Enough for years; no separate graph database |
| Auth | Better Auth (inside the app, data in our Postgres), SSO plugin later | Login data stays in-region |
| Documents | Docling (read), docxtpl and python-docx (write), LibreOffice headless (PDF) | Best open tools; client templates kept intact |
| Models | LiteLLM gateway: a strong model for drafting and a cheaper one for extraction; Jev remains an optional later bake-off | Swap approved models per task; spend limits per client and tender |
| Sandboxes | Separate Cloud Run job executions first, then GKE Agent Sandbox if required | Bounded jobs without early cluster operations |
| Connectors | Gmail API and Microsoft Graph directly; FastMCP for the Win Work MCP server | Production-grade connections |
| Observability | Langfuse, Sentry and product analytics configured for the approved Saudi boundary | AI inputs, traces and operational data stay in the approved boundary |
| Infrastructure | Google Cloud Dammam, Terraform, GitHub Actions | One Saudi region and repeatable environments |
| Email and billing | Resend; Polar or Stripe, whichever supports the legal entity | Simple |
| Repository | Monorepo: pnpm for the web app, uv for Python | One place, fast builds |
| Experiments only | Langflow, n8n | Sketch a flow or a connector quickly, then rebuild it in code |

### Why Pydantic AI and Temporal together

They do different jobs: Pydantic AI makes one AI step correct, and Temporal makes the whole multi-day bid process reliable.

|  | Pydantic AI | Temporal |
| --- | --- | --- |
| Job | Runs one agent step: calls the model, uses tools, returns a checked, typed result | Runs the whole process: which step comes next, waits, timers, retries, human approvals |
| Time span | Seconds to minutes | Minutes to weeks |
| Remembers | Only the current step | Exactly where every tender's process stands, even after a crash or deploy |
| Example in Win Work | "Answer requirement 3.2 from the client's evidence and return answer, sources, blanks" | "Draft all answers, wait for review, chase supplier B after 3 days, remind 48 hours before the deadline" |
| Without it | Hand-written glue for model calls, tool use and output validation | Cron jobs, status flags and retry code that break when a server restarts mid-bid |

Pydantic AI has built-in support for running agents inside Temporal workflows, so each agent step becomes a retried, logged activity with no extra glue.

## Agent runtime and agent substrate

Every agent step (intake, quotes, draft, check-in, learn) runs in its own isolated sandbox that holds no credentials, so a bad file or a confused agent cannot reach another client or a mailbox directly.

&#91;embedded content: agent job path · 1 sandbox, 3 outbound links\]

In the full agentic phase, the tender agent starts a job, an isolated execution runs the Pydantic AI step, and traffic leaves through the model gateway, results API or egress proxy. The lean MVP has no mail or drive tokens and runs bounded Cloud Run jobs from the Postgres queue; warm-pool sandbox claiming is a later GKE concern.

| Phase | When | Runtime | Why |
| --- | --- | --- | --- |
| Lean MVP | First pilots | Bounded jobs on a Postgres queue in Cloud Run, one job per execution | Simple to run with two people and no long-lived autonomous agent |
| Scale | Tens of clients, many jobs a day | GKE Agent Sandbox: one gVisor-isolated sandbox per job, claimed from a warm pool, default-deny network policy | Stable (v1.0 since August 2026, generally available on GKE); claims usually in about 200 ms |
| Density | Many long-lived, mostly idle agents (e.g. one watching each tender's mailbox) | Agent Substrate on top of Agent Sandbox: snapshots idle agents and packs many onto few machines | Pre-1.0 and in the CNCF Sandbox since October 2026; adopt only when idle agents cost real money |

**Rules that hold in every phase**

- One sandbox per job, destroyed or snapshotted after; no shared disk between clients.
- No secrets inside the sandbox; the egress proxy adds tokens and allows only approved hosts (model gateway, Win Work API, the client's mail and drive APIs).
- The mail tools exposed to agents can create drafts but cannot send.
- Every job writes an audit event: who started it, inputs, tools called, outputs.

Sources: [Agent Sandbox on GKE and Agent Substrate, Google Cloud](https://cloud.google.com/blog/products/containers-kubernetes/bringing-you-agent-sandbox-on-gke-and-agent-substrate) · [Running AI agents on Kubernetes, Signadot](https://www.signadot.com/blog/running-ai-agents-on-kubernetes/)

## Data model

Every row carries a `tenant_id` and Postgres row-level security enforces it, so one client can never read another's data. The company brain is these tables plus an edges table linking them, with embeddings stored beside each document chunk.

| Entity | Key fields | Links to |
| --- | --- | --- |
| Tenant | name, region, plan, packs enabled | everything |
| User | email, role (owner, bid manager, contributor, reviewer, viewer) | tenant |
| Department | name, colour | contacts, asks |
| Contact | name, role, email, phone | department or supplier |
| Tender | buyer, title, reference, value, deadlines, stage, bid strength | requirements, documents, quotes, asks |
| Requirement | text, section, type (mandatory, scored, pricing, document), weight, limit, page ref, status | tender, answer, department |
| Answer | text, sources, blanks, confidence, word count, version | requirement, evidence |
| Document | file, kind (tender, past bid, CV, certificate, policy, datasheet, draft), expiry date | tender or brain |
| Chunk | text, page, embedding | document |
| Edge | from, to, type (used\_in, proves, supersedes, equivalent\_to) | any two entities |
| Supplier | name, categories, countries, approved | contacts, quotes |
| Quote request | package, items, sent, chasers, status | tender, supplier, mail thread |
| Quote | price, currency, lead time, validity, exclusions, compliance | quote request |
| Ask | item, due date, status | department, tender |
| Pack rule | country or industry, text, source link, version date | pack |
| Lesson | text, outcome, score lost or gained | tender, requirement type |
| Audit event | actor (person or agent), action, inputs, time | any entity |

**Added for Insights and modes:**

- **Outcome:** award or rejection letter, winner, award value, contract start and end (feeds win rates, price position and the recompete radar).
- **Plan:** typed steps, status per step, who approved and when.
- **Brief:** schedule, recipients, sections, delivery channel.
- **Chat thread:** questions, answers, sources used and charts returned.
- **Ingestion event:** item, source, step reached, confidence, what was linked (powers "Added to brain" and the confirm list).

## AI layer

The AI never answers from memory: every claim in a bid must point to a client document, and anything without a source becomes a visible blank.

- **Models:** a strong model for drafting and compliance checks, a cheaper one for extraction and email reading, both behind the LiteLLM gateway so models can be swapped per task and per region. Use model endpoints hosted in the same region as the client's data where available, and check each provider's regional and no-training terms before each country launch.
- **Parsing:** Docling turns tender PDFs into text, tables and headings with page numbers; scans go through OCR. Bills of quantities in Excel are read directly.
- **Retrieval:** hybrid search (keywords plus pgvector) over the client's chunks, always filtered by `tenant_id`, then a reranker. The edges table adds related items (the project behind a CV, the certificate behind a claim).
- **Structured outputs:** every agent step returns a fixed schema (answer, sources, blanks, confidence), validated by Pydantic before it is saved.
- **Prompts and packs:** prompts are versioned in Langfuse; country and industry pack rules are stored as data with source links and dates, never baked into prompts.
- **Evaluation:** a test set of real, public tenders with known good answers runs on every prompt or model change. Checks:
  - every claim has a source;
  - no invented project, certificate or number;
  - limits respected;
  - requirement coverage;
  - reviewer edit rate. A change that fails any check does not ship.
- **Cost control:** spend limits per client and per tender in the gateway; cache parsed tenders and embeddings; batch email reading.

### Decision model layer (Jev)

Fast yes/no and pick-one decisions go to a decision model, Jev from TypeSafe AI, which returns typed answers from options we define plus a calibrated confidence score; drafting and free-text extraction stay with language models through Pydantic AI.

| Decision | Options | What happens with confidence |
| --- | --- | --- |
| Document type | CV, certificate, past bid, datasheet, quote, tender, policy, other | Low confidence: ask the user |
| Same entity? | yes, no | High: merge automatically; low: "please check" list |
| Supplier email type | quote, question, decline, out-of-office, other | Low: show in the inbox for a person |
| Requirement routing | engineering, estimating, procurement, HSE, legal, HR, finance | Low: bid manager assigns |
| Requirement type | mandatory, scored, pricing, document | Low: flag in the checklist |
| Source type | proof, claim, unclear | Unclear: treated as claim |
| Spec compliance per line | met, partly, not met | Low: reviewer checks |
| Unsourced claim guardrail | yes, no | Yes or low: block from export until reviewed |

- **Interface:** every decision goes through our own `decide(schema, input)` function, so Jev and a language-model fallback (structured output) are interchangeable per decision.
- **Thresholds:** one auto-accept threshold per decision, tuned on labelled data; below it, a person decides.
- **Bake-off before use:** about 200 labelled real files and emails per decision, Jev vs a cheap language model, comparing accuracy, calibration, speed and cost; keep the winner per decision.
- **Claims to verify:** TypeSafe reports 70 to 500 ms per call and $0.042 per million input tokens with free output; these are vendor figures from its launch post (15 September 2026, early access).
- **Risks:**
  - Its service is currently based on the US West Coast, which conflicts with region hosting for EU and Saudi data. Until an EU or self-hosted option and a data processing agreement exist, use it only on non-sensitive data (public tender text, email type).
  - Early-access vendor; pricing may be subsidised.
  - Up to 255 options per decision; larger choices need a two-step setup.

Source: [Introducing System One Models & Jev, TypeSafe AI](https://typesafe.ai/blog/introducing-system-one-models-and-jev)

## Integrations

After the upload-based lean MVP, Win Work connects from the server to the client's own accounts. Nothing is installed inside Word or Outlook in the first connector phase.

| Integration | Through | Permissions asked | Used for |
| --- | --- | --- | --- |
| Gmail | Gmail API (MCP client where useful) | read mail, create drafts, labels; never send | supplier threads, quote reading, drafted requests |
| Outlook mail | Microsoft Graph | read mail, create drafts, categories; never send | same as Gmail |
| Google Drive | Drive API | access to one Win Work folder per tender | write draft DOCX, watch for changes, read back |
| OneDrive and SharePoint | Microsoft Graph | access to chosen folders only | same as Drive |
| Google Sheets and Excel | Sheets API, Graph Excel API | edit the chosen price file | fill prices from chosen quotes |
| Tender portals | Chrome extension (later); email alerts | none on the portal | save tenders; never submit |
| Win Work MCP server | FastMCP over Streamable HTTP, OAuth | client's admin adds it to Copilot, Claude or ChatGPT | requirements, evidence, quotes and gaps inside their AI tools |
| Billing and email | Polar, Resend | account billing only | plans, invoices, notifications |

- **Least access:** ask only for drafts (never send) and only for chosen folders; tokens live in a secrets store and are added by the egress proxy, never seen by agents.
- **Admin consent:** Microsoft 365 and Google Workspace often require an admin to approve these permissions. Plan for a one-page security sheet and a short consent guide in sales.
- **Change detection:** use push notifications (Drive changes, Graph webhooks) with a polling fallback.

### Business systems (CRM, ERP, HR, project tools)

Everything from outside systems maps into the same brain entities (a CRM account becomes a Buyer, an ERP vendor becomes a Supplier, an HR employee becomes a Person), so a new system adds data instead of a new silo.

**Lean MVP: manual exchange that works on day one**

- Direct PDF, DOCX, XLSX and CSV upload for tenders, quotes and company evidence.
- Downloadable DOCX, XLSX and CSV package outputs.
- Mapping previews and human confirmation before imported prices or facts are accepted.
- No mailbox, shared-folder or business-system authorization.

**Post-MVP, in this order**

1. **One mail and one drive connector** selected from paid pilot usage in Phase 2.
2. **Public REST API and webhooks** when electrical contractors request repeatable integration.
3. **Win Work MCP server** after the public authorization model is proven.
4. **Zapier, Make or a native CRM/ERP connector** only when three to five paying electrical contractors request the same system.
5. **Unified API providers** only after verifying that all relevant processing and support meet the approved Saudi boundary.

**Rules:** read first; writes are drafts or opportunities that need approval in Win Work; the client's system stays the source of truth (an expired certificate in HR wins over our copy); every synced record is logged.

### Win Work MCP server

A standard MCP server lets the client's own AI tools (Copilot, Claude, ChatGPT or their in-house agents) work with Win Work data, so users get help inside Word or chat without us building add-ins.

| Tool | What it returns or does |
| --- | --- |
| list\_tenders | Open tenders with stage, deadline and bid strength |
| get\_requirements | Requirement checklist for a tender, with status and owner |
| get\_gaps | Blanks, over-limit answers and compliance gaps |
| search\_evidence | Matching passages from the client's brain, with document and page |
| get\_answer\_draft | The current draft text for one requirement, with sources |
| get\_quote\_comparison | Supplier quotes for a package, side by side |
| add\_comment | Adds a comment to a requirement (write) |
| request\_redraft | Starts a redraft of one answer (write; result arrives as a suggestion) |

- **Built with:** FastMCP in Python, served over Streamable HTTP from each region next to the API.
- **Access:** OAuth sign-in as the user; the server sees only that user's tenant and their role's permissions.
- **Safety:** mostly read tools; the two write tools never send, submit or overwrite a file; every call lands in the audit log.
- **Setup:** the client's admin adds the server URL in their AI tool; Win Work shows a one-page guide per tool.
- **When:** in Phase 4 after the public API and authorization model are proven; it is not pulled forward for a single pilot request.

## Security, compliance and regions

Saudi Arabia is the only committed deployment region in this roadmap. Saudi client data and operational telemetry stay in the approved Saudi boundary. The regional pattern below is retained as an architectural reference, but UK or EU deployment is not scheduled while the product remains focused on Saudi electrical contractors.

| Region | Cloud region | Database | Notes |
| --- | --- | --- | --- |
| EU | Google Cloud, EU region (e.g. Frankfurt or Belgium) | Cloud SQL Postgres in the EU region | GDPR; data processing agreement with every client |
| UK | Google Cloud London | Cloud SQL Postgres in London | UK GDPR |
| Saudi Arabia | Google Cloud Dammam | Cloud SQL Postgres in Dammam (self-managed Postgres if a service is not offered there) | PDPL and government data rules; check model hosting in-Kingdom before launch |

- **Tenant isolation:** row-level security in Postgres, a `tenant_id` filter on every vector search, one sandbox per agent job, separate storage paths per client.
- **Secrets:** Google Secret Manager; client OAuth tokens encrypted and only used by the egress proxy.
- **Encryption:** in transit (TLS) and at rest (cloud default plus encrypted token columns).
- **No cross-client training:** stated in the contract and enforced in code; model providers used only under no-training terms.
- **Audit log:** every human and agent action, with inputs, stored per tenant.
- **Compliance path:** start SOC 2 Type I with a tool such as Vanta or Drata once the first paying clients sign; ISO 27001 when GCC or enterprise buyers ask for it.
- **Procurement-specific:** human sends every email and submits every bid; AI-use disclosure available per bid; conflict check before serving two bidders on the same tender.

## DevOps and observability

One repository, one pipeline and one Saudi production region. Infrastructure modules remain reusable without paying the operational cost of additional regions.

- **Repository:** a monorepo with `web` (Next.js), `api` (FastAPI), `agents` (Pydantic AI agents and Temporal workflows), `docs-tools` (parsing and DOCX writing) and `infra` (Terraform).
- **CI/CD:** GitHub Actions runs tests, the AI evaluation set and type checks on every pull request; preview deployments for the web app; promotion to each region after it passes.
- **Environments:** local (Docker Compose with Postgres and a fake file/quote inbox), Saudi staging and Saudi production; add Temporal locally only when Phase 4 introduces it.
- **Infrastructure as code:** Terraform modules applied to the Saudi staging and production environments.
- **Observability:**
  - Langfuse traces every agent step (inputs, tools, cost, time).
  - Temporal's own UI shows every workflow's history and current state.
  - Sentry catches errors in web and API; PostHog tracks product analytics.
- **Alerts:** failed workflows, a connector token expired, a deadline within 48 hours with blockers, daily AI spend over budget.
- **Backups:** daily database backups with point-in-time recovery per region; restore tested monthly.

## Build phases, team and risks

&#91;embedded content: build phases · concierge proof, lean MVP, workflow automation, team knowledge, agentic product\]

Each phase has an observable exit gate. A new service, connector or runtime is added only when the next gate requires it.

### Phase 0: paid concierge proof

1. Recruit two or three Saudi electrical contractors with live government or utility tenders.
2. Produce the proposed package manually with internal parsing and drafting tools.
3. Test real Arabic, English and mixed-direction tender packs, bills of quantities, supplier quotes and company evidence.
4. Record extraction corrections, quote-matching errors, unsupported claims, document-format failures, delivery time and customer willingness to pay.
5. Select the two or three Word/Excel template patterns the software will support first.

**Exit gate:** at least two contractors pay, use the package on a live tender and commit to using it again. If they do not, change the package before building the application.

### Phase 1: lean MVP

1. **Core:** tenant, users and simple roles, authentication, storage, audit events, malware scanning, Arabic/English shell, backups and failed-job alerts.
2. **Tender intake:** upload PDF, DOCX and XLSX; parse requirements, dates, priced lines and required documents; require user confirmation.
3. **Evidence library:** approved projects, certificates, policies, CVs and product datasheets with provenance, expiry, approval and superseded states.
4. **Manual quote intake:** upload supplier quote files, map revisions and lines to the bill of quantities, and require price confirmation.
5. **Checks:** electrical product/specification checks, certificate expiry, Saudi local-content and mandatory-product gaps, missing documents and unanswered requirements.
6. **Selected drafting:** draft user-selected technical answers with exact supporting passages and visible unsupported gaps.
7. **Package export:** confirmed requirements matrix, approved priced schedule, draft answers, source report, gap report and submission checklist.
8. **Measurement:** processing time, human correction time, model/document cost, package completion and user reuse per tender.

**Exit gate:** the Lean MVP acceptance and stop condition above passes across three paying contractors and at least five live tenders.

### Phase 2: workflow automation

1. Build one mail connector and one drive connector chosen from pilot usage.
2. Draft quote requests and chasers; read replies and attachments; preserve quote revisions and require price approval.
3. Add shared-folder file versions, change detection and review approval tied to an exact file hash.
4. Add fuller pricing build-up, package comparison and Excel/Sheets write-back for the electrical bill of quantities.
5. Record submitted, won, lost and withdrawn outcomes plus evaluator feedback.

**Exit gate:** the majority of pilot quote traffic and document versions are captured without manual re-entry, and reconciliation tests show no silent price or approved-version mismatch.

### Phase 3: team and reusable knowledge

1. Add department assignments, asks, reminders, reviewer links and deadline-focused home screen.
2. Expand the company brain with controlled automatic ingestion, confirmation queues, role restrictions and deletion/supersession behavior.
3. Build reusable packs only for electrical products and tender types observed in paid work.
4. Add history import, predefined metrics, Insights and chat after enough clean tenders and outcomes exist.
5. Add daily and weekly briefs after the underlying workflow data is reliable.

**Exit gate:** repeat customers run their whole electrical bid team through Win Work and show a measured reduction in preparation and review time without a higher correction rate.

### Phase 4: agentic full product

1. Add the selection, pricing, compliance and bid agents one workflow at a time, comparing each with the measured Phase 3 baseline.
2. Release Chat first, Plan second and Auto only for steps that meet accuracy, cost and human-override thresholds.
3. Introduce Temporal only when multi-day timers, approvals and crash recovery outgrow the Postgres queue; introduce GKE Agent Sandbox only when isolation or volume requires it.
4. Add buyer-form filling, Etimad Chrome extension, WhatsApp Business API, public API, MCP and business-system connectors only after repeated demand from electrical contractors.
5. Pursue SOC 2 or ISO 27001 when required by the target customers' procurement process.

**Exit gate:** real electrical tenders complete end to end with safe human gates, lower time and correction cost than Phase 3, and no unsupported claim, unapproved price or stale document version silently reaches the package.

**Roadmap boundary:** other contractor segments, new countries and a separate Agent-Ready product graph are not post-MVP stages. They require a future strategy decision after the Saudi electrical-contractor product has repeatable acquisition, retention and healthy margins.

### Team

- **Founder 1:** product engineering, document pipeline, AI checks and Saudi infrastructure.
- **Founder 2:** pilot sales, workflow discovery, product design and delivery ownership with the contractors.
- **First outside help:** a Saudi electrical estimator/bid reviewer who validates bills of quantities, product compliance, local-content checks and Arabic packages.
- **First hire:** a full-stack or integrations engineer after the lean MVP gate, when connector work begins and revenue can support the role.

### Risks

| Risk | Mitigation |
| --- | --- |
| Requirement extraction misses or misclassifies an obligation | Require confirmation before checks or drafting; measure misses on real electrical tenders |
| Supplier price is matched to the wrong item or revision | Preserve quote files and versions; show line-level provenance; require price approval |
| A citation does not support the drafted claim | Store exact passages, check claims individually and route uncertain support to review |
| Draft files lose the client's Word or Arabic formatting | Limit the first template set; test it in Phase 0; make final formatting a stated customer step |
| Saudi rules or mandatory-product lists change | Store rules as dated, sourced data; review updates with the electrical bid expert |
| Admin consent slows Phase 2 connectors | Keep Phase 1 upload-based; build only the connector used by most pilots; provide a security sheet and consent guide |
| Deadline-critical jobs fail | Backups, restore tests, idempotent jobs, failed-job alerts and deadline-aware support exist before live use |
| Model or telemetry data leaves the approved Saudi boundary | Approve every subprocesser and endpoint; block classified tenders until hosting and contracts are verified |
| Founders rebuild every package manually | Track intervention per tender; the MVP gate fails if exports require founder reconstruction |
| Scope expands back into a general bid platform | Enforce the roadmap boundary and require paid electrical-contractor evidence for additions |
| Model costs per tender erase margin | Record cost by job and tender, cap spend, cache parsing and use cheaper models only after quality tests |

### Open decisions

- Which electrical tender subtype comes first: supply and installation, maintenance, or project/EPC work?
- Which electrical product families and official Saudi rules must the first pack cover?
- Which two or three buyer Word/Excel template patterns cover most pilot submissions?
- Which model and OCR endpoints can process pilot data inside the approved Saudi boundary?
- What price per tender covers document/model cost, expert review and support while retaining healthy margin?
- For Phase 2, do most paying pilots use Microsoft 365 or Google Workspace?

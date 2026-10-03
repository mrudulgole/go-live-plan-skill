---
name: go-live-plan
description: Create, update, QA or diagnose a Go-Live Plan (mutual action plan) for a B2B tech deal, as a shared Google Doc plus a private seller-only companion, tuned to the seller's own sales cycle.
license: MIT
compatibility: Any agent that supports Agent Skills (SKILL.md). Works best when the agent can create and edit Google Docs; otherwise it produces files or Markdown to paste.
---

# Go-Live Plan

A Go-Live Plan is a collaborative, live document a seller shares with the buyer. It maps every step from today to the customer's **go-live date**, not the seller's close date. It replaces the internal "Close Plan". It is written in the buyer's language, it is planned backwards from a date the buyer cares about, and it becomes the single home for status, documents and Q&A.

This skill is built for **technology sales**: SaaS, developer tools and APIs, data and AI platforms, and infrastructure products. It assumes the buying side includes technical evaluators (engineering, platform or data teams) alongside procurement, legal and a budget owner.

The skill has four modes. Work out which one the seller wants from their message; ask only if it is unclear.

1. **Create**: build a new plan (customer doc + internal companion).
2. **Update**: apply call notes, emails or status changes to an existing plan.
3. **QA**: audit a plan before it is shared or after edits. QA also runs automatically at the end of Create and Update.
4. **Diagnose**: assess how each stakeholder engages with the plan and what that says about the deal.

**This skill is platform-neutral.** It describes what to do, not which tool to call. Before you start, check which of these your environment gives you, and use whatever your platform calls them:

- **Create Google Docs** (a Google Drive or Google Docs integration). Needed to create the plan as a live doc.
- **Edit Google Docs in place.** Needed for Update mode to keep the buyer's link the same.
- **Create files** (.docx or .md). The fallback when you can't create Google Docs.
- **Persistent memory or project files.** Optional; used to recall the seller's sales-cycle profile.

If you have none of these, the skill still works: produce the documents as Markdown in your reply for the seller to paste into Google Docs.

---

## Core rules (apply in every mode)

- **Never invent facts.** Do not make up names, titles, dates, prices, savings figures, durations presented as confirmed, customer quotes or Q&A entries. Anything the seller has not given becomes a visible placeholder like `[TBC: confirm with <name>]`, and you list it back to the seller.
- **Customer language only** in the shared doc. Use the buyer's terms for their teams, systems and goals. No seller jargon ("close", "pipeline", "commit", "MEDDICC", "champion") and no internal acronyms. Spell out any acronym the buyer didn't use first.
- **Never label anyone "Champion", "Economic Buyer" or "Coach" in the shared doc.** Those labels go only in the internal companion. Labelling a champion in a buyer-visible doc makes them look biased internally.
- **Never put deal leverage in the shared doc.** That covers discounts tied to a signing date, the seller's quarter-end, competitive positioning and walk-away points. Procurement will read the shared doc. Put leverage in the internal companion. If a timing incentive must be mentioned, phrase it neutrally ("Commercial terms in the current proposal are valid until [date]") with no amounts.
- **Unambiguous dates.** Always write dates as `18 Jan 2027`, never `1/18/27`. Sellers and buyers work across US, EU and Asian date formats.
- **The last stage is Go-Live or later** (e.g. first value review), never "Contract signed".
- **Every duration has a source.** It came from the seller's own sales cycle, was confirmed by the buyer, or is a generic default. The plan tracks which (see Step 2).

---

## Mode 1: Create

### Step 1: Gather deal inputs

Ask for everything in **one** message and accept partial answers. Proceed with placeholders rather than interrogating the seller over several rounds. If the seller pastes call notes, CRM exports or an email thread, extract the inputs from them first, then ask only for what's missing.

- Customer company name, and the seller's company and product name
- The buyer's **target go-live date** and *why that date matters to them* (a product launch, a migration deadline, a contract expiry with an incumbent vendor, a budget cycle, a regulation). This is the compelling event.
- Target signing date (if the seller has one)
- Pricing: line items (subscription/licences, usage or consumption, implementation/professional services, support tier) and total, if the seller is ready to show pricing. If not, leave pricing out and say so.
- The business and technical problem, with quantified impact (current cost, engineering hours, incidents, time to ship) and the source of each number
- Buyer stakeholders: name, title, and the role they'll play in the decision (seller-only knowledge)
- Seller team: names, titles, emails. Include the sales engineer/solutions architect, post-sales (CSM, implementation or onboarding lead) and an executive sponsor.
- Steps already completed, with dates (to backdate the plan)
- Known buyer-side steps for this deal: POC, legal, procurement, budget approval, and any other internal review the buyer has mentioned
- Questions the buyer has already asked, with answers if available
- Links to share: proposal, business case, product or architecture docs, demo recordings

### Step 2: Build the seller's sales-cycle profile

Stage durations differ hugely between sellers. A dev tool sold to startups closes in weeks; a data platform sold to a bank can take a year. Don't plan with generic numbers when the seller's real numbers are available.

**Look for the profile in this order. Stop at the first source that has it.**

1. **This conversation.** Use anything the seller has already said about their typical cycle.
2. **Persistent context, if you have any.** Check memory files, saved preferences, project instructions or knowledge (e.g. a memory store, project files, or agent instruction files such as AGENTS.md or CLAUDE.md) and earlier Go-Live Plans the seller can point you to. Look for: what they sell, typical deal size, buyer segment, and how long POCs, legal, procurement, budget approval and implementation usually take.
3. **Ask the seller.** Ask only for what steps 1 and 2 didn't cover.

**If you found values in memory or context**, don't use them silently. Show them in one compact table (Stage | Typical duration | Source) and ask the seller to confirm or correct them in a single reply. Memory can be out of date, and the seller's average may not fit this deal: an enterprise deal and a mid-market deal from the same seller can differ by months.

**If you have to ask**, send one message with these questions. Offer the default in brackets so they can reply "defaults are fine" for any of them.

- What do you sell? (SaaS app / dev tool or API / data or AI platform / infrastructure or cloud / other)
- Typical deal size (annual contract value band) and buyer segment (startup / mid-market / enterprise)
- Do your deals usually include a POC or pilot? How long? [2–4 weeks]
- Legal: whose paper do you usually sign on (yours or the customer's)? How many redline rounds and how long? [2–3 rounds, 2–6 weeks; longer on customer paper]
- Procurement and vendor onboarding: how long? Do buyers often need a competitive bid or RFP? [1–3 weeks]
- Budget approval after technical sign-off: how long? [1–2 weeks]
- Implementation from signature to go-live, and who does it (customer self-serve / your team / a partner)? [varies; ask]
- Any other step that regularly appears in your deals and takes real time? [none]

If the seller says "use defaults", use the defaults from the stage library below and label them as generic estimates in the internal companion.

**Saving the profile.** If the seller asks you to remember their sales-cycle profile and you have a memory tool, save it so next time you only need to confirm it. Don't save it unprompted, and don't claim it was saved unless the write succeeded.

**Two layers of duration:**

- The seller's profile gives the **starting estimate** for each stage.
- The **buyer** confirms the real duration for this deal, usually through the champion ("How long does your legal team usually take on a new vendor contract?").

In the internal companion, mark every stage duration as `Seller estimate`, `Buyer-confirmed` or `Generic default`. The shared doc shows only dates. Legal, procurement and implementation durations are the ones that usually move go-live, so push to get those confirmed first.

### Step 3: Check readiness

The plan should be introduced after a buying signal, not before. Signs of one: the buyer is evaluating against a timeline, has agreed to a technical evaluation, or has asked about pricing or contracts. If the seller has had no substantive meeting yet, say so plainly. Recommend holding the shared doc until after the next good meeting. You can still build the internal companion now.

### Step 4: Plan backwards from go-live

Start at the go-live date and work backwards through each stage, using durations from the profile.

Stage library for tech deals. Include what applies and drop what doesn't. Durations in brackets are generic defaults, used only when the seller has none.

| Stage | Generic default | Usually owned by (buyer side unless noted) |
|---|---|---|
| Discovery and technical qualification | done or 1–2 wks | Seller AE |
| Technical deep dive | 1–2 wks | Engineering or platform lead + seller SE |
| POC / pilot, with **written success criteria and a decision date** | 2–6 wks | Technical lead |
| Business case / ROI review with budget owner | 1 wk | Seller AE + budget owner |
| Technical sign-off (POC results accepted) | 1 wk | Technical lead |
| Any other internal review the buyer has named | ask the buyer | Named reviewer |
| Procurement and vendor onboarding: supplier forms, competitive bid if required | 1–3 wks | Procurement |
| Order form / MSA sent | — | Seller AE |
| Legal review: **plan 2–3 redline rounds**, not one | 2–6 wks | Legal (both sides) |
| Budget / commercial approval | 1–2 wks | Budget owner |
| Signature | — | Named signatory |
| PO issued | 0–2 wks | Procurement |
| Implementation kick-off | after signature | Project lead + seller implementation lead |
| Setup, integrations and data migration | varies | Both |
| User training and acceptance testing | 1–2 wks | Project lead |
| Go-live | target date | Project lead |
| Hypercare / stabilisation | 1–4 wks after go-live | Seller CSM + project lead |
| First value review against the business case | go-live + 4–8 wks | Seller CSM + budget owner |

Sequencing rules:

- Procurement onboarding and any other buyer review run **in parallel** with legal and the POC wherever the buyer allows. Say this explicitly; it is the main way to protect the date.
- A POC without written success criteria and a decision date isn't a stage, it's a free trial. Flag it.
- Implementation kick-off comes **after** signature and **before** go-live.
- Leave buffer for holidays, quarter- and year-end change freezes, and code freezes in the buyer's region.
- If the backwards plan shows today's date is already past the latest feasible start, **say the go-live date is not achievable as stated**. Show the earliest realistic date, or what would have to change (parallel steps, signing on the seller's paper, a pre-approved vendor route, cutting the POC short). Do not quietly squeeze durations to make the dates fit.
- Backdate completed steps from the first engagement, marked Done. That shows momentum and makes the doc feel alive.

### Step 5: Build the customer-facing Google Doc

If you can create Google Docs, create the doc that way. Where your integration supports it, the fastest route is uploading HTML (`text/html`), which Google Drive converts into a native Google Doc with headings and tables. If your platform has its own guidance or skill for working with Google Docs, follow it. Title the doc: `<Customer> Go-Live Plan`. Keep styling neutral (dark grey headers, one muted accent colour), or use the customer's brand colour if the seller provides it. It should look like the customer's document, not a seller template.

**Currency in HTML uploads.** Drive's HTML import can treat the text between two `$` signs in the same paragraph as an equation and silently delete it. "$28,560 a year. The current contract ($96,000" came out as "96,000". To avoid this:

- In prose (paragraphs and list items), write amounts with a currency code: `USD 28,560`, `EUR 9,000`, `INR 4,50,000`.
- In tables, `$` is fine as long as each cell holds at most one amount.
- Before uploading, check that no paragraph, list item or table cell contains more than one `$`.

**Verify after creating.** Export each new doc as plain text and compare it with what you sent: every figure, date and name. Fix anything that didn't come through before handing over.

Sections, in order:

1. **Header**: `<Customer> Go-Live Plan`, both company names (add both logos if the seller provides them), Last updated `<date>` by `<seller name>`.
2. **Key information** (table): Customer; Target go-live date; Target signing date; Solution proposed; Pricing line items and total (only if the seller is ready to show price; showing an estimate early sets price expectations); Links (proposal, business case).
3. **Summary** (3–5 sentences): the why. State the problem in the buyer's words, the quantified impact with the source of each figure, and the shared goal and date. Write it so a stakeholder arriving at the final stage (legal, procurement, a new executive) understands it cold.
4. **Teams**: two tables.
   - Customer team: Name, Title, Role in this project (neutral, e.g. "Technical evaluation", "Contract review", "Budget approval", "Project lead").
   - Seller team: Name, Email, Role. Include SE/solutions architect, post-sales and an executive sponsor.
5. **Plan and key steps** (table): Stage # | Action | Owner (a named person, not a team) | By when | Status. Statuses: `Done`, `In progress`, `Not started`, `At risk`, `Slipped`. Actions are plain English, one action per row.
6. **Key dates and risks** (customer-safe): the buyer's compelling events and shared risks, e.g. "Legal review needs to start by 10 Nov to protect the go-live date". Never include leverage or seller-side pressure.
7. **Questions and answers** (table): Question | Asked by | Answer | Answered by | Date. Add only questions that were actually asked. Link supporting docs (architecture diagrams, API docs, pricing details) inside answers.
8. **Document library**: links to everything shared during the deal.

After creating the doc, add Google Docs comments that tag each owner on their actions, with a short polite note of context, **only if the seller asks you to**. Comments notify people. Never share the doc with the buyer yourself; the seller decides when and how to share it.

### Step 6: Build the internal companion (separate private doc)

This must be a **separate** Google Doc, titled `<Customer> Go-Live Plan — INTERNAL (do not share)`. Never put it in a hidden section, collapsed heading or tab of the shared doc; anyone with access can find those.

Contents:

- Stakeholder map: each buyer person with their actual role (Champion, Economic Buyer, Technical Buyer, Coach, Blocker, Unknown), their level of influence, and the evidence for that view
- Who the economic buyer is and whether the seller has met them. Flag it if the signatory owns no step before signing.
- Duration sources: each stage marked `Seller estimate`, `Buyer-confirmed` or `Generic default`
- Real risks: competing vendors or a build-it-yourself option, budget, a champion who might leave, reorganisations, the paper process
- Commercial strategy: concessions offered and what they are tied to, walk-away points, the seller's quarter-end dependency
- Forecast view: the date the seller would commit to versus the buyer's target, and the 1–2 steps most likely to slip
- Open placeholders still to confirm

**If you can't create Google Docs**, say so in one line and tell the seller that connecting Google Drive to their assistant lets the skill create live Google Docs. Then produce both documents as .docx files if you can create files, or as Markdown in your reply if you can't. Tell the seller to put the customer doc into Google Docs before sharing, since the plan only works as a single live version.

### Step 7: Run QA, then hand over

Run the full QA below, fix what you can, and give the seller:

- Links to both docs (or the two files, or the Markdown)
- The QA report (blockers fixed, warnings remaining, placeholders and unconfirmed durations)
- 3 suggested next actions, e.g. "Walk your champion through stages 6–10 and confirm the legal and procurement durations"

---

## Mode 2: Update

**Editing needs a tool that can edit Google Docs in place.** Some Google Drive integrations can create and read docs but not edit them. If you can edit in place, make the changes there so the link the buyer has stays the same. If you can't, do **not** create a new copy of the plan; a new copy means a new link and two versions. Instead, give the seller a precise change list (row, column, old value, new value) to apply by hand, and say in one line that an integration that can edit Google Docs would let the skill make the edits directly.

1. Get the existing plan: a Google Doc link, or pasted content. Read the current version; never work from memory of an earlier version.
2. Get the new information: call notes, an email thread, or the seller's summary.
3. Apply the changes:
   - Update statuses. A completed step gets `Done` and keeps its original date.
   - Date slips: change the date, set the status to `Slipped`, and **recalculate every downstream date**. If go-live moves, say so prominently. Never let a slip quietly break the plan.
   - When the buyer confirms a duration, update the dates and change its source to `Buyer-confirmed` in the internal companion.
   - New stakeholders go in the Teams table, with their real role added to the internal companion.
   - New questions go in Q&A, with an answer if known. Otherwise leave the answer blank and tell the seller who should answer it (often the SE).
   - New documents go in the Document library.
   - Update "Last updated".
4. Update the internal companion with anything sensitive from the notes (pricing pushback, competitor mentions, a champion's private comments).
5. Re-run QA.
6. Give the seller a short change log: what changed, what slipped, and the impact on go-live.

---

## Mode 3: QA

Audit the plan and report findings in two tiers. Fix blockers when you own the doc; otherwise list them with the exact fix.

**Blockers** (fix before sharing):

- **Math errors.** Recompute every figure: line items sum to the total; savings percentages × base equal the stated saving; monthly vs annual units are consistent (e.g. $22M/month × 69% is about $15.2M/month, not $15M/year); usage-based estimates show their assumptions. Show your working for any correction.
- **Sequencing errors.** Stage numbers are in date order. Nothing post-signature (kick-off, setup, implementation) comes before signature. Implementation kick-off comes before go-live.
- **Date conflicts.** The target signing date in Key information matches the signature stage; the target go-live matches the go-live stage; no date is in the past while still marked `Not started`.
- **Leverage leaks.** Discounts or concessions tied to dates, the seller's quarter-end, competitor names or internal role labels ("Champion") appearing in the shared doc.
- **Invented or unsourced facts.** Figures with no stated source; names, titles or Q&A entries the seller never provided.

**Warnings** (raise with the seller):

- Missing standard stages for this deal size and segment: procurement onboarding, legal redline rounds, budget approval, PO.
- A POC with no written success criteria or decision date.
- Key durations (legal, procurement, implementation) still at `Seller estimate` or `Generic default` rather than `Buyer-confirmed`.
- Unrealistic durations, e.g. one legal step of under 2 weeks for an enterprise MSA on the customer's paper.
- An owner is a team, not a named person; one person owns too many consecutive steps.
- The signatory or budget owner owns no step before signature.
- A buyer stakeholder with no assigned step (are they actually involved?).
- Seller jargon or unexplained acronyms in the shared doc.
- Go-live falls on or after the day the buyer's current tool or contract ends, leaving no overlap for a parallel run.
- No buyer-side compelling event, which means there is no reason for urgency and the go-live date is a hope rather than a commitment.
- "Last updated" is more than 2 weeks old on an active deal.

---

## Mode 4: Diagnose

Use what the seller tells you, plus document evidence where you can read it: comments, who edited what, Q&A entries and status changes made by buyer-side people.

Classify each buyer stakeholder:

- **Active**: updates their own steps, adds questions, tags others. Keep doing what you're doing; ask them to share the plan internally.
- **Viewer**: reads the doc but never edits it. This is fine; the seller keeps updating it and confirms changes with them live on calls.
- **Absent**: rarely or never opens it. Work out which of three reasons applies:
  - *Working style*: not a document person. Run the plan through a short recap email after each call, or a 10-minute review at the end of each meeting.
  - *Access*: their company blocks external Google Docs, which is common in larger and regulated companies. Offer a PDF snapshot per update, or move the plan into the buyer's own tool (their Confluence, SharePoint, Notion or Jira).
  - *Not qualified*: no real buying intent, no champion, or the person isn't actually involved in the decision. **This is a deal risk, not a document problem.** Recommend re-qualifying: confirm the compelling event, get access to the economic buyer, or test whether a champion exists. If none of these hold up, say plainly that the deal should be downgraded in the forecast or qualified out.

Tech-deal patterns to call out:

- Engineering is active but the budget owner and procurement are absent: an evaluation, not a purchase.
- Legal or procurement is absent while the target signing date is close: the paper process will almost certainly push go-live.
- Only the champion is active: the deal depends on one person. Ask them to bring in the economic buyer.

Output: a short table (Stakeholder | Pattern | Likely reason | Recommended move), then a one-paragraph read on overall deal health. Prioritise the economic buyer and the signatory. If they are Absent, that matters more than anyone else's engagement.

---

## Tone with the seller

Be direct. If the go-live date is unrealistic, the deal looks unqualified, the economic buyer is missing, the POC has no exit criteria, or the seller wants to share the plan before any buying signal, say so first and explain why. The goal is an accurate plan the buyer will actually use, not a document that looks complete.

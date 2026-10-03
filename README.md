# Go-Live Plan skill

An AI agent skill that helps tech sellers build, maintain and pressure-test **Go-Live Plans**: shared plans that map every step from today to the customer's go-live date. It is the buyer-facing version of a mutual action plan, as opposed to an internal close plan.

Built for people selling SaaS, developer tools, APIs, data/AI platforms and infrastructure to technical buyers.

It follows the open [Agent Skills](https://agentskills.io) standard (`SKILL.md`), so it works with any assistant or agent that supports skills, such as ChatGPT/Codex, Claude, Cursor and Gemini CLI. Assistants that don't support skills can still use it as pasted instructions (see [Installing](#installing)).

## What it does

| Mode | What you say | What you get |
|---|---|---|
| **Create** | "Build a go-live plan for Acme, target go-live 15 March" | A customer-facing plan and a private internal companion, planned backwards from the go-live date |
| **Update** | "Update the Acme plan with these call notes" | Updated statuses, recalculated dates if anything slipped, new Q&A, and a short change log |
| **QA** | "Check this plan before I send it" | Blockers (math errors, stages out of order, date conflicts, leverage leaks, invented facts) and warnings |
| **Diagnose** | "Legal hasn't opened the doc in two weeks, what does that mean?" | A read on each stakeholder's engagement and what it says about the deal |

Each plan has two documents:

- **Customer doc**: key information, summary, both teams, the step-by-step plan with owners and dates, key dates and risks, Q&A, and a document library. It is written in the buyer's language, with no seller jargon and no deal leverage.
- **Internal companion** (never shared): stakeholder roles, real risks, commercial strategy, forecast view, and where each stage duration came from.

## Requirements

### Google Docs access (strongly recommended)

The skill is designed to produce **Google Docs**, because a Go-Live Plan works best as one live document that you and the buyer both edit and comment on. Connect Google Drive / Google Docs to your assistant if it supports that. What the skill can do depends on what that integration allows:

| Your assistant can… | What the skill does |
|---|---|
| **Create and edit Google Docs** | Creates the plan and the internal companion as Google Docs, and updates them in place so the buyer's link stays the same. |
| **Create Google Docs but not edit them** | Creates both docs. In Update mode it gives you a list of exact changes to make by hand, rather than making a new copy with a new link. |
| **Create files only** | Produces both documents as .docx files. Upload the customer doc to Google Docs yourself before sharing. |
| **None of the above** | Writes both documents as Markdown in the chat for you to paste into Google Docs. |

The skill never shares a doc with your buyer. You decide when and how to share it.

### Memory (optional)

Stage durations differ a lot between sellers, so the skill tunes the plan to your own sales cycle. It looks for that information in this order:

1. What you've said in the current conversation
2. Your assistant's memory or your project files, if it has them
3. If neither has it, the skill asks you once (POC length, legal, procurement, budget approval, implementation), with defaults you can accept

If it finds your numbers in memory, it shows them to you to confirm before using them. Without memory, it simply asks. If you ask it to remember your answers and memory is available, it saves them, so next time you only need to confirm.

## Installing

The skill lives in the [`go-live-plan`](go-live-plan) folder. You can also download it as `go-live-plan.zip` from the [latest release](../../releases/latest).

- **Assistants with a skills upload (for example the Claude apps):** upload `go-live-plan.zip` in the assistant's skills settings.
- **Coding agents that read skills from disk:** clone the repo and copy the folder into the agent's skills directory.

  ```bash
  git clone https://github.com/mrudulgole/go-live-plan-skill.git
  # Shared location used by Codex and other Agent Skills tools
  cp -r go-live-plan-skill/go-live-plan ~/.agents/skills/
  # Claude Code
  cp -r go-live-plan-skill/go-live-plan ~/.claude/skills/
  ```

  Other agents use their own folder; check your tool's docs for where it loads skills from.
- **Assistants without skills support:** paste the contents of [`SKILL.md`](go-live-plan/SKILL.md) into a custom assistant's instructions, a project's instructions, or the start of a chat.

## Example prompts

- "Create a go-live plan for Northwind. Their target go-live is 1 Feb because their current vendor contract expires then. Here are my call notes: …"
- "Here's the Northwind plan link. Update it: legal pushed their review by a week, and the CFO asked about usage overages."
- "QA this plan before I send it to procurement."
- "Only my champion ever edits the plan. Diagnose this deal."

## What it doesn't do (yet)

- It doesn't include stages for security, compliance or data-protection reviews by default. If your buyer needs one, tell the skill and it will add it as a step owned by the buyer's named reviewer.
- It doesn't connect to your CRM. Paste notes or exports into the conversation instead.

## License

[MIT](LICENSE)

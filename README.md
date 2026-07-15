# Sapia.ai — AI Sales Agent Team
## Outbound GTM Lead Generation Platform on Claude Code

---

## What This Is

This folder contains everything your team needs to run an autonomous, AI-powered outbound GTM system. The system runs 8 specialist AI agents, coordinated by a Sales Director orchestrator, to research prospects, score them against the ICP, draft personalised outreach, manage contacts in SalesLoft, and handle replies.

**No email ever auto-sends.** Every outreach batch requires human approval.

---

## Get the Repo

Two steps, no git commands to memorise.

**Step 1: open Claude Code once, anywhere.** Terminal → `claude` from your home folder or Documents. Already have a session open? Skip to Step 2.

**Step 2: prompt it to clone the repo for you:**

> *"Clone https://github.com/brendanreid-droid/Sales-Agent.git into my Documents folder, then tell me exactly where it landed."*

Claude runs the clone and confirms the folder path. **One thing this can't skip:** a Claude Code session is tied to the folder it started in, so this session won't automatically become the Sales Director. Close it, then reopen Claude Code from inside the new folder, either double-click `start.command` there, or type `claude` in a terminal opened to that folder. That second launch is what boots the Sales Director and wires up the 8 specialist agents.

This is a private repo. If the clone fails on a permission error, ask Brendan to add you as a collaborator first (GitHub → repo → Settings → Collaborators).

---

## Runs on Claude Code

This stack runs on **Claude Code**, not Claude Desktop. That's not a preference, it's a requirement: the agents are wired as native Claude Code subagents (`.claude/agents/`) with `CLAUDE.md` auto-loading the Sales Director identity every session, that's what lets one orchestrator dispatch 8 specialists in parallel automatically. Claude Desktop has no equivalent, it would mean manually pasting each agent's prompt into a separate Project and copying between them by hand, a fundamentally weaker, manual version of this system. See "Why not Claude Desktop?" at the bottom if you want the full reasoning.

- `CLAUDE.md` — loads the Sales Director identity + all standards automatically every session.
- `.claude/agents/` — the 7 specialists, dispatchable by name (`company-researcher`, `copywriter`, etc.).
- `agent_prompts/` — the full role prompts each agent reads (single source of truth).

**Quickstart:** open this folder in Claude Code (or double-click `start.command`, see below) and say *"You're the Sales Director. Research my top 3 Tier 1 accounts, then draft outreach."* Claude boots as the orchestrator and routes to the specialists.

**Engine vs data (important for sharing):**
- **Engine (shared):** `CLAUDE.md`, `.claude/agents/`, `agent_prompts/`, `.agents/AGENTS.md`, ICP rubric, product, case studies, `.mcp.json.example` (server definitions only, no secrets).
- **Data (yours):** target list, signals, performance, Voice Profile, MCP credentials, your real `.mcp.json`.
- New teammates: clone the repo, copy `vault-template/` into their own vault, copy `.mcp.json.example` to `.mcp.json` and fill in their own keys (gitignored), and go. See `vault-template/README.md`.

---

## Folder Structure

```
Claude Sale Agent/
├── README.md                          ← You are here
├── start.command                      ← Double-click to launch Claude Code (Mac). No terminal typing needed.
├── .mcp.json.example                  ← MCP server template. No secrets, safe to commit.
├── .mcp.json                          ← Your copy, with real keys pasted in. Gitignored, never committed. (You create this.)
│
├── agent_prompts/                     ← The 8 agent system prompts, single source of truth
│   ├── 00_sales_director.md
│   ├── 01_research_analyst.md
│   ├── 02_icp_scorer.md
│   ├── 03_copywriter.md
│   ├── 04_prospect_hunter.md
│   ├── 05_reply_handler.md
│   ├── 06_company_researcher.md
│   └── 07_gtm_action_thinker.md
│
├── .claude/agents/                    ← Same 7 specialists, wired as native Claude Code subagents
│
└── Sapia-Sales-Vault/                 ← Knowledge base
    ├── 00-ICP/                        ← ICP definitions, scoring rubric, persona maps, target account list
    ├── 01-Product/                    ← Product overview, differentiators, ROI data
    ├── 02-Accounts/                   ← Account briefs + email drafts, one pair per company
    ├── 02-Case_Studies/                ← Customer case studies
    ├── 03-Outreach/                   ← Email sequences, subject lines, objection library
    ├── 04-Brand_Voice/                ← Brand guidelines, individual voice profiles
    ├── 05-Signals/                    ← Job movers log, newsletter engagers, trigger events
    └── 06-Performance/                ← Campaign results, learnings, A/B test log
```

---

## Quick Setup Guide

### Step 1: Pre-populated Central Vault (Done ✅)
The core business assets are pre-populated and consistent across the organisation:
* `00-ICP/ICP_Master_Profile.md` — Verified customer sectors, target ICP, and exclusions.
* `00-ICP/Target_Account_Analysis.md` / `Target_Account_List.csv` — currently Brendan's own 155-account territory list, **not** shared master data, see Step 1b.
* `01-Product/Product_Overview.md` — Approved product suite and unified SAIGE scoring engine.
* `01-Product/ROI_Data_Points.md` — Verified statistics database across all case studies.
* `02-Case_Studies/` — Sector-specific customer briefs.

### Step 1b: Replace the Target List With Your Own (Action Required, every rep)
The 155-account list currently in the vault is one rep's personal territory, not a company-wide master list. Before you run the system:
1. Replace `00-ICP/Target_Account_Analysis.md` and `00-ICP/Target_Account_List.csv` with your own territory's accounts, same file format, your own companies.
2. Leave the ICP Score/Tier columns from any old spreadsheet in there if you want a historical reference, but don't rely on them, see the note below.

> **On scoring: ignore any legacy ICP score in your spreadsheet from here on.** The only score that counts is whatever the ICP Scorer agent produces against `00-ICP/ICP_Scoring_Rubric.md`. This keeps every account's priority traceable to one consistent rubric instead of mixing old spreadsheet math with the current one. An account with no ICP Scorer pass yet is unscored, not "whatever tier the old sheet said."
* `04-Brand_Voice/Sapia_Brand_Guidelines.md` — Active guidelines and prohibited terms.

### Step 2: Individual AE Setup (Action Required)
Each Account Executive (AE) must complete their personal configuration files:
- [ ] `03-Outreach/Email_Winners/Cold_Winners.md` — Add your 3–5 best-performing personal cold emails.
- [ ] `04-Brand_Voice/Sender_Voice_Profiles/` — Duplicate the template and complete your own Voice Profile (save as `[FirstName]_Voice.md`).

> **Note:** The target account list (`00-ICP/Target_Account_Analysis.md`) is pre-populated for the team. The Research Analyst will re-score accounts using the ICP Scoring Rubric as it works through them, and writes any new lookalike company it finds back into the same file so it's never re-discovered later.

### Step 3: Connect Your MCP Servers (no terminal needed)

1. Find `.mcp.json.example` in the repo root. Duplicate it and rename the copy to `.mcp.json` (same folder). Any text editor works, TextEdit, Notepad, VS Code, whatever you're comfortable with.
2. Open `.mcp.json` and replace each `"..."` with your real value, using the table below for where to find each one.
3. Save the file.
4. Open Claude Code (double-click `start.command`, or open a terminal in this folder and type `claude`) and send this message:
   > *"I've filled in my MCP credentials in .mcp.json. Please confirm which servers connected and test each one."*
5. I'll check each connector and tell you plainly if anything's missing or wrong, no guesswork on your end.

`.mcp.json` (your real, filled-in copy) is gitignored, it never gets committed or shared. `.mcp.json.example` (the template with no secrets) is what's checked into git for the rest of the team.

**API Key Sources:**
| Service | Where to get it | Notes |
|---------|----------------|-------|
| SalesLoft | Admin enables Agentic package (Settings → Agentic) first, org-wide, one-time. Then Settings → API → Create API Key. | Ask your SalesLoft admin before generating your key, it won't work until they've enabled this. |
| HubSpot | Settings → Integrations → Private Apps → Create a private app → copy the Access Token | Needs private-app creation rights |
| Lusha | Account Settings → API → Manage API Keys | 200 credits/week/rep budget, enforced by the Prospect Hunter agent |
| Gong | Company Settings → API → Create API Key (gives you an Access Key and a Secret, you need both) | Optional, only used for voice calibration |
| Brave Search | brave.com/search/api | Optional, web search still works without it |
| Slack | No key needed | OAuth prompt appears automatically the first time an agent tries to use it |
| Filesystem | The absolute path to your local `Sapia-Sales-Vault` folder | Right-click the folder → Get Info (Mac) / Properties (Windows) → copy the path |

### Step 4: Fill in Your Voice Profile
Duplicate `04-Brand_Voice/Sender_Voice_Profiles/Voice_Profile_Template.md`, complete it, save as `[FirstName]_Voice.md`. The Copywriter reads this before drafting anything in your name.

### Step 5: Share with Your Team
Just share the git repo, `.mcp.json.example` is checked in and holds no secrets, cloning is the whole install. Each teammate then repeats Steps 3-4 above with their own keys and Voice Profile.

---

## Weekly Cadence Summary

> **None of this runs on its own.** There's no scheduler or background job, every row below happens because you open Claude Code and prompt it. Treat the days as a suggested rhythm, not a timer. See `Build_Walkthrough.html`'s "Tuesday & Thursday Cadence Schedule" for the exact prompt to send at each step.

| Day | What Happens | You trigger it with |
|-----|-------------|---------------------|
| **Monday** (& Wednesday, optional) | Sales Director: new research (lookalikes + trigger events), account prioritisation, week plan | A planning prompt, e.g. *"Let's kick off new research..."* |
| **Tuesday** | Copywriter drafts batch → Sales Director builds digest → **Human approves → SalesLoft sends** | A drafting prompt, then a separate "check approvals and stage" prompt after you approve in Slack |
| **Thursday** | Same as Tuesday | Same as Tuesday |
| **Friday** | Sales Director: weekly performance review, learnings update | A review prompt, e.g. *"Pull this week's SalesLoft stats..."* |
| **Fortnightly/Monthly** | Research Analyst: HubSpot newsletter engagement pull, filtered to your own territory | A HubSpot pull prompt, lower priority, doesn't block Tue/Thu sends |
| **Monthly** | LinkedIn Sales Nav CSV upload → Prospect Hunter processes → Champion Movers flagged | A CSV-processing prompt once you've dropped the export in, lower priority |

---

## The 3 Trigger Workflows

| Signal | Source | Action | Priority |
|--------|--------|--------|----------|
| Newsletter engagement | HubSpot MCP | Warm outreach email drafted | Same week |
| Job move (champion mover) | LinkedIn Sales Nav CSV + Lusha | Personalised congratulations sequence | Within 48 hours |
| Lookalike company discovery | Web search / Lusha MCP | Enrich, score, stage for approval, and permanently logged so it's never re-discovered | Next available batch |

---

## Human Approval Gates

You must always approve:
1. **Prospect queue** — new lookalike accounts before they enter the outreach pipeline
2. **Morning Digest** — all drafted emails, reply `APPROVE` in Slack before anything is enrolled
3. **Positive reply responses** — drafted by Reply Handler, you send
4. **Objection responses** — drafted by Reply Handler, you approve

**Two gates before an email actually reaches a prospect, not one:**
1. You reply `APPROVE` in Slack for the batch. Once you do, and you next prompt Claude to check ("Check Slack approvals and stage"), Prospect Hunter automatically stages the contacts and enrols them into their SalesLoft cadence, no further prompt needed for that part.
2. **You still start/send the cadence yourself, inside SalesLoft.** No agent ever calls a "send" action, that stays a manual click in the SalesLoft UI. This is intentional, Slack approval and SalesLoft send are two separate human checkpoints.

> **Before relying on the auto-enrol step:** confirm your SalesLoft cadence's email steps are set to **Manual** send type, not **Automatic**. On an Automatic-type step, SalesLoft sends the moment a contact is enrolled, which would collapse the two gates above into one. This is a one-time check in your own SalesLoft cadence settings.

The system **auto-handles** (no approval needed):
- OOO detection and cadence pausing
- Unsubscribe processing (immediately removes from all cadences)

Full guardrail list (anti-spam cooldowns, Lusha budget protection, copywriting standards, and more): see `Build_Walkthrough.html`.

---

## Tips for Best Results

1. **Populate the vault first.** The agents are only as good as their reference material. Spend 2–3 hours populating the case studies, email winners, and voice profiles before running your first batch.

2. **Start small.** Run the system with 5–10 emails in the first batch. Review every output carefully. Iterate the system prompts and vault documents before scaling.

3. **Trust the quality gate.** If the Copywriter flags that it can't write a compelling email due to insufficient research, don't override it. Pause the account. Generic emails hurt your domain reputation.

4. **Update Campaign_Learnings.md every week.** This is the compounding learning loop. Skip it and the system stagnates.

5. **Calibrate the ICP Scorer.** After 4–6 weeks, look at which accounts converted and adjust the rubric weights. If every converted account was in Retail, increase the weight for industry fit.

---

## Why not Claude Desktop?

Claude Desktop can technically hold static copies of each agent's prompt in separate Projects, and it does have a nicer point-and-click Connectors panel for MCP setup with zero terminal use at all. If someone on your team genuinely cannot use a terminal, even once, that's the honest tradeoff to weigh.

But Desktop can't run this system as designed. There's no equivalent to `.claude/agents/` or `CLAUDE.md`, so there's no orchestrator automatically dispatching specialists in parallel, no shared task tracking, no single Sales Director coordinating a Monday plan into a Tuesday digest. A rep on Desktop would be manually copying context between Projects by hand, a materially different, slower, more error-prone process, not the same stack running elsewhere. For a team that needs everyone working the same way, this matters more than the small one-time terminal step Claude Code asks for.

If a rep is uncomfortable opening a terminal: `start.command` reduces that to a single double-click, and the whole rest of the setup (Step 3-4 above) is plain file-editing, no commands to type at all.

---

## Support & Questions

For questions about this setup, contact: [Your name / Slack handle]
For issues with individual MCP servers: check the vendor's help documentation

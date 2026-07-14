# Sapia.ai — AI Sales Agent Team
## Outbound GTM Lead Generation Platform on Claude Desktop

---

## What This Is

This folder contains everything your team needs to run an autonomous, AI-powered outbound GTM system using **Claude Desktop** and **Claude Projects**. The system runs 7 specialist AI agents, coordinated by a Sales Director orchestrator, to research prospects, score them against the ICP, draft personalised outreach, manage contacts in SalesLoft, and handle replies.

**No email ever auto-sends.** Every outreach batch requires human approval.

---

## Two ways to run this

This stack now supports two deployment models. Pick one.

### A. Claude Code (recommended, wired and ready)
The agents are wired as native Claude Code subagents. No manual Project setup.
- `CLAUDE.md` — loads the Sales Director identity + all standards automatically every session.
- `.claude/agents/` — the 7 specialists, dispatchable by name (`company-researcher`, `copywriter`, etc.).
- `agent_prompts/` — the full role prompts each agent reads (single source of truth).

**Quickstart:** open this folder in Claude Code and say *"You're the Sales Director. Research my top 3 Tier 1 accounts, then draft outreach."* Claude boots as the orchestrator and routes to the specialists.

**Engine vs data (important for sharing):**
- **Engine (shared):** `CLAUDE.md`, `.claude/agents/`, `agent_prompts/`, `.agents/AGENTS.md`, ICP rubric, product, case studies.
- **Data (yours):** target list, signals, performance, Voice Profile, MCP credentials.
- New teammates: clone the repo, copy `vault-template/` into their own vault, add their `claude_desktop_config.json` (gitignored), and go. See `vault-template/README.md`.

### B. Claude Desktop + Claude Projects (original method)
Paste each `agent_prompts/*.md` into a Claude Project's Custom Instructions. Full steps below.

---

## Folder Structure

```
Claude Sale Agent/
├── README.md                          ← You are here
├── claude_desktop_config_template.json ← MCP server config (fill in credentials)
│
├── agent_prompts/                     ← Paste these into each Claude Project's Custom Instructions
│   ├── 00_sales_director.md           → SAPIA-SD Claude Project
│   ├── 01_research_analyst.md         → SAPIA-RA Claude Project
│   ├── 02_icp_scorer.md               → SAPIA-ICP Claude Project
│   ├── 03_copywriter.md               → SAPIA-CW Claude Project
│   ├── 06_company_researcher.md       → SAPIA-CR Claude Project
│   ├── 04_prospect_hunter.md          → SAPIA-PH Claude Project
│   └── 05_reply_handler.md            → SAPIA-RH Claude Project
│
└── Sapia-Sales-Vault/                 ← Knowledge base (upload to Claude Projects + mount via Filesystem MCP)
    ├── 00-ICP/                        ← ICP definitions, scoring rubric, persona maps
    ├── 01-Product/                    ← Product overview, differentiators, ROI data
    ├── 02-Case_Studies/               ← Customer case studies (add yours)
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
* `00-ICP/Target_Account_Analysis.md` — 155 target accounts tiered by ICP score, with case study matching and ATS research priorities.
* `00-ICP/Target_Account_List.csv` — Raw 2026 territory planning data (source for the analysis above).
* `01-Product/Product_Overview.md` — Approved product suite and unified SAIGE scoring engine.
* `01-Product/ROI_Data_Points.md` — Verified statistics database across 14 case studies.
* `02-Case_Studies/` — 13 detailed, sector-specific customer briefs created.
* `04-Brand_Voice/Sapia_Brand_Guidelines.md` — Active guidelines and prohibited terms.

### Step 2: Individual AE Setup (Action Required)
Each Account Executive (AE) must complete their personal configuration files:
- [ ] `03-Outreach/Email_Winners/Cold_Winners.md` — Add your 3–5 best-performing personal cold emails.
- [ ] `04-Brand_Voice/Sender_Voice_Profiles/` — Duplicate the template and complete your own Voice Profile (save as `[FirstName]_Voice.md`).

> **Note:** The target account list (`00-ICP/Target_Account_Analysis.md`) is pre-populated for the team. The Research Analyst will re-score accounts using the ICP Scoring Rubric as it works through them.

### Step 3: Configure MCP Servers
1. Open the `claude_desktop_config_template.json`
2. Replace all `"..."` values with your real API keys and credentials
3. Update the filesystem path to match your local setup
4. Copy the completed config to: `~/Library/Application Support/Claude/claude_desktop_config.json`
5. Restart Claude Desktop

**API Key Sources:**
| Service | Where to get it |
|---------|----------------|
| SalesLoft | Admin must enable Agentic package → Settings → API |
| HubSpot | Settings → Integrations → Private Apps |
| Lusha | Account Settings → API → Manage API Keys |
| Slack | Slack App Directory → Claude connector (OAuth) |
| Brave Search | brave.com/search/api |

### Step 3: Create Claude Projects
For each agent, create a new Claude Project in Claude Desktop:

1. **Claude Desktop** → Left sidebar → **New Project**
2. Name: Use exact names below
3. **Custom Instructions**: Paste the full contents of the corresponding `agent_prompts/` file
4. **Project Knowledge**: Upload the relevant vault documents (see table below)
5. **Connectors**: Enable the MCP servers listed for that agent

| Project Name | System Prompt File | Key Vault Docs | MCP Servers |
|-------------|-------------------|----------------|-------------|
| `SAPIA-SD — Sales Director` | 00_sales_director.md | All signal logs, performance tracker | HubSpot, SalesLoft, Slack, Filesystem |
| `SAPIA-RA — Research Analyst` | 01_research_analyst.md | ICP profile, ICP scoring rubric, target account analysis, persona maps, product overview | Lusha, HubSpot, Brave Search, Filesystem |
| `SAPIA-CR — Company Researcher` | 06_company_researcher.md | Persona maps, product overview, competitive differentiators | HubSpot, Brave Search, Filesystem |
| `SAPIA-ICP — ICP Scorer` | 02_icp_scorer.md | ICP profile, scoring rubric | Lusha, HubSpot, Filesystem |
| `SAPIA-CW — Copywriter` | 03_copywriter.md | Brand voice, sequences, objection library, email winners | Gong, Filesystem |
| `SAPIA-PH — Prospect Hunter` | 04_prospect_hunter.md | ICP profile, target account list | Lusha, SalesLoft, Filesystem |
| `SAPIA-RH — Reply Handler` | 05_reply_handler.md | Objection library, product overview, ROI data | SalesLoft, Slack, Filesystem |
| `SAPIA-GAT — GTM Action Thinker` | 07_gtm_action_thinker.md | ICP profile, competitive differentiators, ROI data | Filesystem |

### Step 4: Share with Your Team
1. In Claude Desktop → **Team Workspace** settings → Invite team members
2. Once shared, all Projects and their knowledge bases are accessible to team members
3. Each rep fills in their own Voice Profile in `04-Brand_Voice/Sender_Voice_Profiles/`

---

## Weekly Cadence Summary

| Day | What Happens |
|-----|-------------|
| **Monday** | Sales Director: signal harvest, account prioritisation, week plan |
| **Tuesday** | Copywriter drafts batch → Sales Director builds digest → **Human approves → SalesLoft sends** |
| **Thursday** | Same as Tuesday |
| **Friday** | Sales Director: weekly performance review, learnings update |
| **Monthly** | LinkedIn Sales Nav CSV upload → Prospect Hunter processes → Champion Movers flagged |
| **Fortnightly/Monthly** | Research Analyst: HubSpot newsletter engagement pull |

---

## The 3 Trigger Workflows

| Signal | Source | Action | Priority |
|--------|--------|--------|----------|
| Newsletter engagement | HubSpot MCP | Warm outreach email drafted | Same week |
| Job move (champion mover) | LinkedIn Sales Nav CSV + Lusha | Personalised congratulations sequence | Within 48 hours |
| Lookalike company discovery | Lusha MCP | Enrich, score, stage for approval | Next available batch |

---

## Human Approval Gates

You must always approve:
1. **Prospect queue** — new lookalike accounts before they enter the outreach pipeline
2. **Morning Digest** — all drafted emails before any SalesLoft send
3. **Positive reply responses** — drafted by Reply Handler, you send
4. **Objection responses** — drafted by Reply Handler, you approve

The system **auto-handles** (no approval needed):
- OOO detection and cadence pausing
- Unsubscribe processing (immediately removes from all cadences)

---

## Tips for Best Results

1. **Populate the vault first.** The agents are only as good as their reference material. Spend 2–3 hours populating the case studies, email winners, and voice profiles before running your first batch.

2. **Start small.** Run the system with 5–10 emails in the first batch. Review every output carefully. Iterate the system prompts and vault documents before scaling.

3. **Trust the quality gate.** If the Copywriter flags that it can't write a compelling email due to insufficient research, don't override it. Pause the account. Generic emails hurt your domain reputation.

4. **Update Campaign_Learnings.md every week.** This is the compounding learning loop. Skip it and the system stagnates.

5. **Calibrate the ICP Scorer.** After 4–6 weeks, look at which accounts converted and adjust the rubric weights. If every converted account was in Retail, increase the weight for industry fit.

---

## Sharing This System with Peers

Share the entire `Claude Sale Agent` folder via:
- **Shared drive** (Google Drive, SharePoint) — read-only access to all except their own Voice Profile
- **Claude Team Workspace** — Projects automatically shared with invited members
- The `claude_desktop_config_template.json` is safe to share — it contains no live credentials

Each rep needs to:
1. Set up their own local MCP config (credentials are personal)
2. Fill in their own Voice Profile
3. Have Claude Desktop with Team plan access

---

## Support & Questions

For questions about this setup, contact: [Your name / Slack handle]
For issues with individual MCP servers: check the vendor's help documentation
For Claude Desktop support: claude.ai/help

# Enrichment Report — 2026-07-15
## Prospect Hunter — Test Batch (10 companies, ICP-scored today: 5 Tier A, 5 Tier B)

All companies below passed the score-before-enrich gate. Outreach_History_Log.csv was empty at the start of this run, so no 90-day contact cooldown or 21-day company cooldown excluded anyone. All 7 staged contacts belong to different companies, satisfying the one-contact-per-company batch rule. Emails only were revealed; no phone numbers were requested or received.

| Company | Stakeholder | Title (source) | Verified Email | LinkedIn | Cooldown Check | Action |
|---|---|---|---|---|---|---|
| Spotless (Downer Group) | Jan O'Neill | Chief People Officer (brief + Lusha, matches) | jan.oneill@downergroup.com ✅ | [linkedin.com/in/janoneill](https://www.linkedin.com/in/janoneill) | Clear — no prior touch | Staged — PENDING APPROVAL |
| Crown Resorts | Louise Tebbutt | Chief People and Culture Officer (brief + Lusha, matches) | louise.tebbutt@crownresorts.com.au ✅ (alt: louise.tebbutt@crownmelbourne.com.au) | [linkedin.com/in/louise-tebbutt-a51a594](https://www.linkedin.com/in/louise-tebbutt-a51a594/) | Clear — no prior touch | Staged — PENDING APPROVAL |
| Fortescue | Jackie Donnan | Director of Global Human Resources (Lusha; brief had NO named contact) | jackie.donnan@fortescue.com ✅ (alt: jackie.donnan@fmgl.com.au) | [linkedin.com/in/jackie-donnan-99796727](https://www.linkedin.com/in/jackie-donnan-99796727) | Clear — no prior touch | Staged — PENDING APPROVAL (net-new find, no CHRO/COO title exists at Fortescue; this is the most senior HR-specific title on the ranked decision-maker list) |
| ANZ Group Holdings | Elisa Clements | Group Executive of Talent and Culture (Lusha confirms CURRENT and C-Suite as of last Lusha update 2024-11-25; no fresher public update found either way) | elisa.clements@anz.com ✅ | [linkedin.com/in/elisa-clements-82766a7b](https://www.linkedin.com/in/elisa-clements-82766a7b) | Clear — no prior touch | Staged — PENDING APPROVAL (brief's "unconfirmed" flag resolved: Lusha data supports she remains in role) |
| JB Hi-Fi | Dana Forte | **Title discrepancy:** brief says "Group People & Capability Director"; Lusha (updated today, 2026-07-15) says "Group Human Resources Director." Using the more recently verified Lusha title per data-quality standards. | dana.forte@jbhifi.com.au ✅ | [linkedin.com/in/dana-forte-949366130](https://www.linkedin.com/in/dana-forte-949366130) | Clear — no prior touch | Staged — PENDING APPROVAL |
| Reliance Retail Limited | Rakesh Ravindran | Senior Vice President and Chief Human Resources Officer (Lusha; brief had NO reliable named contact — several conflicting/unverifiable names were explicitly excluded) | rakesh.ravindran@ril.com ✅ | [linkedin.com/in/rakesh-ravindran-7971b31b](https://www.linkedin.com/in/rakesh-ravindran-7971b31b) | Clear — no prior touch | Staged — PENDING APPROVAL (net-new find via decision-maker ranking, strongest C-Suite HR title returned; note work email resolves to parent-company domain ril.com, not relianceretail.com — flagged, not a blocker) |
| PLDT Inc. | Stephanie Compa Sevilla | Senior Manager, Head of Talent Acquisition (brief + Lusha, matches) | ssevilla@pldt.com.ph ✅ | [linkedin.com/in/stephanie-sevilla-4070a56b](https://www.linkedin.com/in/stephanie-sevilla-4070a56b) | Clear — no prior touch | Staged — PENDING APPROVAL (champion selected over Gina Ordoñez per instruction — both verified equally solid, champion preferred) |
| IHH Healthcare Berhad | Sharon Foo Sook Yean | Group Chief Human Resources Officer (per brief) | Unverified — Lusha returned NOT_FOUND on two name-split attempts and on the brief's LinkedIn URL (my.linkedin.com/in/sharon-sy-foo) | Not confirmed via Lusha | Clear — no prior touch (moot, not staged) | **HOLD — no verified email found. Do not guess.** No equally strong alternative surfaced (only HR-adjacent contact returned was an HR Information Systems Executive — not a qualifying buyer/champion title). |
| Maybank | Mazhatulshima Mohd Zahid | Group Chief Human Capital Officer (per brief) | Unverified — Lusha returned NOT_FOUND on two name-split attempts | Not confirmed via Lusha | Clear — no prior touch (moot, not staged) | **HOLD — no verified email found. Do not guess.** decision_makers_search on maybank.com returned 44 ranked contacts, all in IT/Digital — zero HR representation, suggesting this domain maps to Maybank's tech arm rather than the group HR org. No usable alternative surfaced. |
| Newmont Corporation (Australian Operations) | Bronwyn Baker | Head of People, Newmont Australia (per brief, LinkedIn "verified" in brief) | Unverified — the LinkedIn URL from the brief (au.linkedin.com/in/bronwynbaker) and a direct name search both resolved in Lusha to a **different company** ("Chief Executive Women," a nonprofit), not Newmont — likely a mismatched or stale Lusha record | Mismatched profile, not used | Clear — no prior touch (moot, not staged) | **HOLD — record does not verify against Newmont. Do not guess or use the mismatched profile.** decision_makers_search on the global newmont.com domain returned no Australia-based HR/People contact as an alternative. |

**Ready for cadence:** 7 contacts staged and pending Slack `APPROVE` (Spotless, Crown Resorts, Fortescue, ANZ Group Holdings, JB Hi-Fi, Reliance Retail, PLDT).
**Enrolled this run:** 0 — no Slack `APPROVE` confirmed for this batch, and SalesLoft is not yet connected regardless, so enrolment cannot happen this session either way.
**Data Quality Holds:** 3 (IHH Healthcare, Maybank, Newmont Corporation Australian Operations) — flagged above, escalate to Sales Director / research-analyst for a fresh contact pass rather than guessing an email format.

All 7 staged contacts logged to `03-Outreach/Outreach_History_Log.csv` (Staged Date 2026-07-15, Status = PENDING APPROVAL, Last Contact Date left blank).

---

## Credit Log — 2026-07-15 Session

| Action | Detail | Credits |
|---|---|---|
| Named-contact preview search (contacts_search, enrich=false) | Batch 1: 9 named contacts (Jan O'Neill, Louise Tebbutt, Elisa Clements, Dana Forte, Gina Ordoñez, Stephanie Sevilla, Sharon Foo, Mazhatulshima Mohd Zahid, Bronwyn Baker) | 1 |
| Decision-maker search (Fortescue via fmgl.com.au — NOT_FOUND, Reliance Retail via relianceretail.com) | Free tool, no credit charge per Lusha pricing | 0 |
| Named-contact retry search (contacts_search, enrich=false) | Batch 2: 5 retry lookups (Bronwyn Baker by LinkedIn URL, Sharon Foo by LinkedIn URL and alt name split, Mazhatulshima Mohd Zahid x2 alt name splits) — all NOT_FOUND or mismatched | 1 |
| Decision-maker search (Fortescue via fortescue.com — success) | Free tool, no credit charge | 0 |
| Decision-maker search (Maybank, IHH Healthcare, Newmont — checking for alternates before HOLD) | Free tool, no credit charge | 0 |
| Email reveal (prospecting_contact_enrich, reveal=["emails"] only) | 7 contacts: Jan O'Neill (0), Louise Tebbutt (0), Elisa Clements (0), Dana Forte (1), Stephanie Sevilla (1), Rakesh Ravindran (1), Jackie Donnan (1) | 4 |
| **Session total** | | **6** |

- **Contacts enriched (email revealed):** 7 of 10 companies. 3 HOLDs (no credits spent on unverifiable reveals — no guessing).
- **No phone numbers requested at any point** (policy: email-only reveals).
- **Running total this week:** 6 credits (assuming this is the first run of the week for this rep).
- **Headroom vs 200/week guardrail:** 194 credits remaining this week. Well under budget — no alert required.
- **Headroom vs 1000-credit session test cap:** 994 credits remaining this session. Well under cap — no alert required.
- **Lusha account-wide balance (checked earlier this session):** 232,155 of 280,022 remaining before this run; 232,149 after this run's 6 credits.

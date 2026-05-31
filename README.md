# Data Scraping Method & Workflow

This document describes how faith-driven leader and company data is collected, what sources are used, which tools handle each source, and how raw output flows into the final Google Sheets database.

---

## Sources Overview

| Source | Type | URL | Skill | Tab Batch |
|---|---|---|---|---|
| Praxis | Portfolio directory | https://www.praxis.co/portfolio | [praxis](skills/praxis.md) | 3 at a time |
| Kingdom Advisors / FaithFi | Advisor directory | https://www.faithfi.com/find-a-cka | [kingdom_advisor](skills/kingdom_advisor.md) | Individual tabs |
| EverSource Wealth Advisors | Advisor listing | https://www.eversourcewealthadvisors.com/ | [kingdom_advisor](skills/kingdom_advisor.md) | Individual tabs |
| LinkedIn | Profile search | https://linkedin.com (keyword search) | [linkedin](skills/linkedin.md) | Individual tabs |
| Faith Driven Entrepreneur Podcast | Podcast episodes | https://faithdrivenentrepreneur.simplecast.com/ | [linkedin](skills/linkedin.md) | 2 episodes at a time |
| U.S. Christian Chamber of Commerce | Member directory | https://uschristianchamber.com/ | [usccc](skills/usccc.md) | 5 at a time |

---

## Tool Stack & Evolution

### Current Primary: Comet (Perplexity Agent)
Comet is a browser that runs a Perplexity-powered AI agent. It is the primary extraction tool because:
- Runs multiple internal search agents in parallel (~30 seconds per entry)
- Perplexity is optimized for web research — high accuracy on company/leader lookups
- Handles multi-tab extraction efficiently

**Fallback: Gemini on Chrome**
When Perplexity token quota resets the next day, Gemini on Chrome is used as a fallback. Performance is similar to Comet/Perplexity but with slightly higher rates of missing or inaccurate data on some fields.

### Abandoned Methods

| Method | Why Abandoned |
|---|---|
| Python + BeautifulSoup (Google) | Google actively blocks automated requests, Low yield (~50 records per 1.5 hours); not worth the time vs. in-browser agents |
| Python + BeautifulSoup (LinkedIn) | LinkedIn blocks non-browser scrapers, Low yield (~50 records per 1.5 hours); not worth the time vs. in-browser agents |
| Claude Chrome Extension | Too slow — ~5 minutes per entry; searched each field one-by-one in a new tab |

### Source Discovery
The existence of the network reference sheet was helpful. New endpoints for those sources are identified through AI-assisted research.

---

## Workflow Per Source

### Praxis
1. Open https://www.praxis.co/portfolio
2. Open 3 company pages in new tabs
3. Run the [Praxis skill prompt](skills/praxis.md) in each tab via Comet/Gemini
4. Macro: copy output → switch to .csv → paste
5. Close tabs, open next 3; repeat until all portfolio companies are done

### Kingdom Advisors / EverSource
1. Open the directory (FaithFi or EverSource)
2. For Kingdom Advisors: search each US city from the [city list](skills/kingdom_advisor.md#city-search-list) (Phase 1 major metros → Phase 2 state-by-state)
3. **Manually cherry-pick** unique advisors — the same person often appears across multiple city searches
4. Open selected advisor pages in tabs
5. Run the [Kingdom Advisor skill prompt](skills/kingdom_advisor.md) via Comet/Gemini
6. Macro: copy output → switch to .csv → paste; repeat

### LinkedIn
1. Search a keyword (e.g., `Convene CEO`, `C12 CEO`, `Faith Driven CEO`) in LinkedIn
2. **Manually cherry-pick** individuals of interest — same person may appear across multiple keyword searches
3. Open selected profiles in tabs
4. Run the [LinkedIn skill prompt](skills/linkedin.md) via Comet/Gemini
5. Macro: copy output → switch to .csv → paste; repeat across all keywords

### Faith Driven Entrepreneur Podcast
1. Open https://faithdrivenentrepreneur.simplecast.com/
2. Open 2 episode pages in new tabs
3. Identify the guest (exclude hosts: Henry Kaestner, William Norvell, Rusty Rueff, Justin Forman)
4. Ask the AI to find the guest's LinkedIn profile URL
5. Open the LinkedIn profile and run the [LinkedIn skill prompt](skills/linkedin.md)
6. Macro: copy output → paste to .csv; repeat for next 2 episodes

### USCCC
1. Open the USCCC member directory
2. Open 5 member pages in new tabs
3. Run the [USCCC skill prompt](skills/usccc.md) in each tab via Comet/Gemini
4. Macro: copy output → switch to .csv → paste
5. Close tabs, open next 5; repeat until all members done

---

## Output & Data Pipeline

### Raw Output Format
Each skill outputs **pipe-separated CSV** (no headers) — one row combining company fields + leader fields, per person. Example structure:

```
Company Name|Website|Industry|Sub-Industry|...|Leader LinkedIn URL|...|Date Added||Full Name|First Name|...|Date Added
```

### Collection
- Macro automates: copy from browser → switch to .csv file → paste
- Raw data lands in `.csv` files
- Semi-automated: macro handles copy/paste; human judgment handles tab selection and dedup

### Import
.csv files are imported into Google Sheets:
- **Companies sheet** — one row per company (done first)
- **Leaders sheet** — one row per leader (most fields copied from the completed company rows)

### Normalization (~3.5–4 hours per batch of 100–250 records)

**Order: Companies first, then Leaders.** Most leader fields mirror company fields — once the company entry is complete, the corresponding leader row is largely done.

**Step 1 — Fix CSV separator (~10–15 min)**
Google Sheets often misreads the pipe (`|`) separator on import. Fix column alignment first so all values land in the correct columns before touching any content.

**Step 2 — Data format cleanup (~30 min)**
- Remove parentheses and extra characters in field values
- Enforce consistent formatting across all columns (casing, whitespace, date format)
- Ensure all Industry/Sub-Industry values match the allowed taxonomy exactly

**Step 3 — Manual field enrichment (~3 hours)**
The most time-intensive step. Go through each entry and manually research + fill empty fields:
- Missing LinkedIn profile URLs
- Missing career/jobs page URLs
- Missing business email addresses
- Any other fields the AI agent left blank or got wrong

---

## Semi-Automation: Macro Setup

A keyboard macro handles the repetitive copy-paste cycle between browser and .csv file:
1. Copy extracted CSV row from browser agent output
2. Switch to the active .csv file
3. Paste
4. Switch back to browser

This semi-automation makes the workflow efficient enough to process hundreds of records per session while keeping human judgment in the loop for cherry-picking and dedup.

---

## Skills Reference

| Skill File | Claude Code Command | Used For |
|---|---|---|
| [skills/praxis.md](skills/praxis.md) | `/project:praxis <url>` | Praxis portfolio companies |
| [skills/kingdom_advisor.md](skills/kingdom_advisor.md) | `/project:kingdom_advisor <url>` | Kingdom Advisors, EverSource |
| [skills/linkedin.md](skills/linkedin.md) | `/project:linkedin <url>` | LinkedIn profiles, FDE Podcast guests |
| [skills/usccc.md](skills/usccc.md) | `/project:usccc <url>` | USCCC member pages |

Each skill file contains the full extraction prompt (with taxonomy) ready to paste into a browser agent. The `.claude/commands/` versions are lean equivalents for use directly in Claude Code.

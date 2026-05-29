# LinkedIn Skill

## Source
**LinkedIn** — used to extract structured data from individual executive profiles of faith-driven leaders.

This skill is triggered in two ways:
1. **Direct LinkedIn searches** using faith-related keywords (see search terms below)
2. **From the Faith Driven Entrepreneur Podcast** — find a guest's name in the episode page, search their LinkedIn, then run this skill on their profile

## When to Use
- Harvesting leaders from LinkedIn keyword searches (Convene, C12, Faith Driven keywords)
- Extracting structured data from any LinkedIn profile you've identified as a person of interest
- Processing FDE Podcast guests (after locating their LinkedIn from the episode page)

## Tool
Comet (Perplexity agent) — primary. Gemini on Chrome — fallback when Perplexity tokens are exhausted.

**Note:** Python/BeautifulSoup is blocked by LinkedIn. In-browser agents only.

## LinkedIn Search Keywords
Use these search terms in LinkedIn's search bar to surface faith-driven executives:
- `Convene CEO`
- `C12 CEO`
- `Faith Driven CEO`
- `Faith Driven Entrepreneur`
- `Christian CEO`
- `Kingdom business`

## Workflow

### Standard LinkedIn Search
1. Search one keyword at a time in LinkedIn
2. Scroll through results and **cherry-pick** individuals of interest (same person may appear across multiple keyword searches — manually dedup)
3. Open selected profiles in new tabs
4. Paste the extraction prompt in each tab and run it
5. Use macro to copy CSV output → switch to .csv file → paste
6. Repeat for the next keyword

### Faith Driven Entrepreneur Podcast (FDE) Path
1. Open https://faithdrivenentrepreneur.simplecast.com/
2. Open **2 episode pages** at a time in new tabs
3. Identify the guest(s) — **exclude these hosts:** Henry Kaestner, William Norvell, Rusty Rueff, Justin Forman
4. Ask the AI to find the guest's LinkedIn profile URL
5. Open the LinkedIn profile and run this skill
6. Use macro to copy output → paste to .csv
7. Repeat for the next 2 episodes

## Filter Criteria
Only extract positions where the title contains:
- Co-Founder, Founder, Partner, CEO, President, Chief
- C-Level (CTO, CFO, COO, etc.), Chair, Board, or Owner

Only include **current positions** (look for "Present" as end date or no end date listed).

**Exclude:** advisory roles, non-executive positions, past/ended positions (any role with a specific end date).

---

## Extraction Prompt

```
Filter criteria:
1. Only include positions where the title contains: Co-Founder, Founder, Partner, CEO, President, Chief, C-Level (CTO, CFO, COO, etc.), Chair, Board or Owner.
2. Only include CURRENT positions (look for "Present" as end date or no end date listed on LinkedIn).

Exclude:
- Advisory roles
- Non-executive positions
- Past/ended positions (any position with a specific end date)

For each executive-level position included in the filter within the Experience section, scrape with format:

- Company name
- Website URL (find it online; if you can't find it, attach the company LinkedIn number)
- Industry (value: Technology & Software; Financial Services; Healthcare & Life Sciences; Energy & Utilities; Consumer Products; Industrial Manufacturing; Transportation & Logistics; Communications & Media; Raw Materials & Mining; Professional & Business Services; Real Estate; Construction & Engineering; Hospitality & Leisure; Education & Training; Environmental & Waste Management; Government & Public Sector; Non-Profit & Social Impact; Defense & National Security; Arts, Entertainment & Culture; Information & Data Services; Aerospace & Space Exploration; Wellness & Longevity)
- Sub-Industry (value: Software & SaaS; Hardware & Semiconductors; Cloud Computing & Data Centers; Cybersecurity; Artificial Intelligence & Agents; Web3; Robotics; DevOps & Platform Engineering; IT Services & Managed Service Providers (MSPs); Banking & Lending; Investment Banking / Hedge Fund; Venture Capital / Private Equity; Financial Planning & Advising; Insurance; Fintech & Digital Payments; Real Estate Investment Trusts (REITs); Cryptocurrency & DeFi; Corporate Finance & FP&A; WealthTech / Personal Finance Apps; Pharmaceuticals; Biotechnology; Medical Devices & Equipment; Healthcare Providers & Clinics; Telemedicine & HealthTech; Healthcare Administration & Operations; Clinical Research Organizations (CROs); Oil, Gas & Fossil Fuels; Renewable Energy (Solar, Wind, Hydro); Electric & Water Utilities; Nuclear Energy; Energy Storage & Grid Tech; Energy Consulting & Advisory; EV Charging Infrastructure; Food & Beverage Production; Agriculture & AgTech; Consumer Packaged Goods (CPG); Supermarkets & Grocery; Delivery Services (Food & Other); E-commerce & Digital Retail; Apparel & Luxury Goods; Automotive & EVs; Home Improvement & Furniture; Consumer Electronics; Direct-to-Consumer (DTC) Brands; Marketplaces (Multi-vendor Platforms); Food Tech & Alternative Proteins; Supply Chain & Food Distribution; Aerospace & Defense; Heavy Machinery & Equipment; Electrical Components; Building Products; Automated Manufacturing Systems; Industrial Automation & Controls; Supply Chain Manufacturing Services; Airlines & Aviation Services; Maritime Shipping & Ports; Rail & Road Freight; Courier & Last-Mile Delivery; Supply Chain Management Software; Logistics Tech Platforms (FreightTech / 3PL); Fleet Management & Telematics; Telecommunications Services; Streaming & Digital Content; Broadcasting & Publishing; Advertising & Marketing Tech; Social Media Platforms; Creator Economy Platforms; Public Relations & Communications Firms; Metals & Mining (Gold, Copper, Lithium); Chemicals & Specialty Materials; Forest Products & Paper; Construction Materials (Cement, Glass); Packaging Materials; Battery Materials & Rare Earth Supply Chain; Sustainable Materials & Green Chemistry; Management Consulting; Marketing Agency; Creative & Digital Services; Legal Services; Human Resources & Staffing; Accounting & Audit; BPO (Business Process Outsourcing); Sales & Revenue Operations (RevOps); Customer Success & Support Services; Residential Development; Commercial Property; Property Management; Real Estate Investment Trusts (REITs); PropTech (Real Estate Technology); Residential Construction; Commercial Construction; Civil Engineering & Infrastructure; Architecture & Design; Construction Project Management; Engineering Services (Mechanical, Electrical, Structural); Infrastructure Development; Hotels & Resorts; Restaurants & Food Services; Casinos & Gaming; Sports & Fitness; Travel Agencies & Tour Operators; Event Management & Experiences; Short-Term Rental Platforms; K-12 Education; Higher Education (Universities); EdTech & Online Learning; Vocational & Corporate Training; Professional Development; Executive Coaching; Educational Supplies; Career Services & Job Placement Platforms; Learning Experience Platforms (LXP); Waste Collection & Disposal; Recycling & Circular Economy; Water Treatment; Environmental Consulting; Carbon Capture & Credits; ESG & Sustainability Consulting; Climate Tech Startups; National & Federal Agencies; Local & Municipal Government; Public Safety & Law Enforcement; Diplomatic Services; Social Security & Welfare; GovTech (Digital Government Services); Public Policy & Think Tanks; Charitable Organizations; Foundations & Philanthropy; Civic & Social Advocacy; International Development (NGOs); Churches & Denominations; Parachurch Christian Ministries; Social Enterprises (for-profit impact companies); Impact Investing Organizations; Intelligence & Surveillance; Military Hardware; Private Security Services; Space Defense; Maritime Security; Defense Technology (AI, Cyber, Drones); Dual-Use Startups; Fine Arts & Museums; Live Music & Performing Arts; Film & Television Production; Gaming & eSports; Photography & Visual Arts; Digital Content Creation Studios; Talent Management & Agencies; Market Research; Credit Reporting Agencies; Scientific Research & Development; News & Information Aggregators; Library & Archival Services; Data Analytics & Business Intelligence; AI Data Labeling & Training Services; Satellite Communications; Space Tourism; Launch Services; Orbital Manufacturing; Celestial Research; Space Data & Analytics; Satellite Infrastructure & Ground Systems; Personal Care & Spas; Nutrition & Supplements; Mental Health Services; Bio-hacking & Longevity Clinics; Alternative Medicine; Corporate Wellness Programs; Digital Health & Wellness Apps)
- City
- State/Region
- Country
- Company Size (find the information within that company LinkedIn)
- Estimated Revenue (find the information online, only summarize the approximate number)
- Primary Leader Name (Current CEO/President/Primary Leader - research this online)
- Primary Leader Business Email (find the email address online; if unavailable give the business email instead. Only provide concrete data, do not fabricate)
- Leader LinkedIn URL (find the information online)
- Faith Alignment Category (Summarize and decide for me, value: Explicit; Overt Leader; Implicit)
- Faith signal summary (Summarize the company's faith alignment in 1-2 sentences, find the information online)
- Faith signal source URL (put the source URL)
- Network Affiliation 1 (value: Faith Driven Entrepreneur; Faith Driven Investor; C12 Business Forums; Convene; Praxis; Christian Economic Forum; CBMC; FGBMFI; International Christian Chamber of Commerce; Kingdom Advisors; Legatus; FCCI; Young Catholic Professionals; BAM Global; U.S. Christian Chamber of Commerce; Other/Custom)
- Network Affiliation 2 (same values as above)
- Network Affiliation 3 (same values as above)
- Career Page URL (Use the company domain and search for a real careers/jobs listing page. Look for pages containing: Careers, Jobs, Join our team, Work with us, Opportunities, etc. If it redirects to a third-party ATS — Greenhouse, Lever, SmartRecruiters, Workday, Ashby, BambooHR, Teamtailor, Recruitee — follow that link and return the final URL. Do not return a generic culture page.)
- Hiring likelihood (Check the Career page. Estimate open roles: High = many roles / active hiring; Medium = a few roles or infrequent postings; Low = few or zero roles)
- Industry Priority (empty this)
- Confidence score (empty this)
- Priority score (empty this)
- Profile status (empty this)
- Date added (fill in today)
- Last updated (fill in today)
- (Blank Column)
- Full name (person whose profile is being scraped)
- First Name
- Last Name
- Title (the specific executive title at THIS company)
- Company name (same as above)
- Company Website (same as above)
- LinkedIn Profile URL (this person's LinkedIn URL)
- City (person's location)
- State/Region (person's location)
- Country (person's location)
- Faith Signal Summary (same as company faith signal summary)
- Faith Signal Source (same as company faith signal source)
- Network Affiliation 1 (same as company affiliations)
- Network Affiliation 2 (same as company affiliations)
- Network Affiliation 3 (same as company affiliations)
- Public Visibility Level (Summarize this, value: Archived; High; Medium)
- Role Seniority (based on their title at this company, value: Executive)
- Confidence Score (empty this)
- Influence Score (empty this)
- Status (empty this)
- Date added (fill in today)
- Last updated (fill in today)

For every missing input, either summarize from this page or research online; if unknown leave it empty. Format the value in CSV format (without the header), use | as separator. Remove any source citation hyperlinks. Output plain copyable text only.
```

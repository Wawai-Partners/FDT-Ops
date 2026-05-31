# USCCC Skill

## Source
**U.S. Christian Chamber of Commerce (USCCC)** — a membership directory of Christian-owned and faith-aligned businesses across the US.

- **Member directory:** [https://christianchamber.net/](https://business.uschristianchamber.com/directory) (or the main member listing page), Go through each one of the categories
- **Network affiliation value:** `U.S. Christian Chamber of Commerce`

## When to Use
When harvesting companies and leaders from the USCCC member directory. This source is highly iterable — members are listed in a browsable directory format.

## Tool
Comet (Perplexity agent) — primary. Gemini on Chrome — fallback when Perplexity tokens are exhausted.

## Workflow
1. Open the USCCC member directory
2. Open **5 member/business pages at a time** in new tabs
3. In each tab, paste the extraction prompt below and run it
4. Use macro to copy CSV output → switch to .csv file → paste
5. Close those 5 tabs, open the next 5, repeat until all members are covered

## Notes
- Get the company Website URL from the "Visit website" link on each member profile
- City/Country info is on the company profile; search online if not listed
- Because USCCC membership is explicit faith alignment, Network Affiliation 1 should always be `U.S. Christian Chamber of Commerce`

---

## Extraction Prompt

```
Scrape these pages with format:

- Company name
- Website URL (get it from the "Visit website" link)
- Industry (value: Technology & Software; Financial Services; Healthcare & Life Sciences; Energy & Utilities; Consumer Products; Industrial Manufacturing; Transportation & Logistics; Communications & Media; Raw Materials & Mining; Professional & Business Services; Real Estate; Construction & Engineering; Hospitality & Leisure; Education & Training; Environmental & Waste Management; Government & Public Sector; Non-Profit & Social Impact; Defense & National Security; Arts, Entertainment & Culture; Information & Data Services; Aerospace & Space Exploration; Wellness & Longevity)
- Sub-Industry (value: Software & SaaS; Hardware & Semiconductors; Cloud Computing & Data Centers; Cybersecurity; Artificial Intelligence & Agents; Web3; Robotics; DevOps & Platform Engineering; IT Services & Managed Service Providers (MSPs); Banking & Lending; Investment Banking / Hedge Fund; Venture Capital / Private Equity; Financial Planning & Advising; Insurance; Fintech & Digital Payments; Real Estate Investment Trusts (REITs); Cryptocurrency & DeFi; Corporate Finance & FP&A; WealthTech / Personal Finance Apps; Pharmaceuticals; Biotechnology; Medical Devices & Equipment; Healthcare Providers & Clinics; Telemedicine & HealthTech; Healthcare Administration & Operations; Clinical Research Organizations (CROs); Oil, Gas & Fossil Fuels; Renewable Energy (Solar, Wind, Hydro); Electric & Water Utilities; Nuclear Energy; Energy Storage & Grid Tech; Energy Consulting & Advisory; EV Charging Infrastructure; Food & Beverage Production; Agriculture & AgTech; Consumer Packaged Goods (CPG); Supermarkets & Grocery; Delivery Services (Food & Other); E-commerce & Digital Retail; Apparel & Luxury Goods; Automotive & EVs; Home Improvement & Furniture; Consumer Electronics; Direct-to-Consumer (DTC) Brands; Marketplaces (Multi-vendor Platforms); Food Tech & Alternative Proteins; Supply Chain & Food Distribution; Aerospace & Defense; Heavy Machinery & Equipment; Electrical Components; Building Products; Automated Manufacturing Systems; Industrial Automation & Controls; Supply Chain Manufacturing Services; Airlines & Aviation Services; Maritime Shipping & Ports; Rail & Road Freight; Courier & Last-Mile Delivery; Supply Chain Management Software; Logistics Tech Platforms (FreightTech / 3PL); Fleet Management & Telematics; Telecommunications Services; Streaming & Digital Content; Broadcasting & Publishing; Advertising & Marketing Tech; Social Media Platforms; Creator Economy Platforms; Public Relations & Communications Firms; Metals & Mining (Gold, Copper, Lithium); Chemicals & Specialty Materials; Forest Products & Paper; Construction Materials (Cement, Glass); Packaging Materials; Battery Materials & Rare Earth Supply Chain; Sustainable Materials & Green Chemistry; Management Consulting; Marketing Agency; Creative & Digital Services; Legal Services; Human Resources & Staffing; Accounting & Audit; BPO (Business Process Outsourcing); Sales & Revenue Operations (RevOps); Customer Success & Support Services; Residential Development; Commercial Property; Property Management; Real Estate Investment Trusts (REITs); PropTech (Real Estate Technology); Residential Construction; Commercial Construction; Civil Engineering & Infrastructure; Architecture & Design; Construction Project Management; Engineering Services (Mechanical, Electrical, Structural); Infrastructure Development; Hotels & Resorts; Restaurants & Food Services; Casinos & Gaming; Sports & Fitness; Travel Agencies & Tour Operators; Event Management & Experiences; Short-Term Rental Platforms; K-12 Education; Higher Education (Universities); EdTech & Online Learning; Vocational & Corporate Training; Professional Development; Executive Coaching; Educational Supplies; Career Services & Job Placement Platforms; Learning Experience Platforms (LXP); Waste Collection & Disposal; Recycling & Circular Economy; Water Treatment; Environmental Consulting; Carbon Capture & Credits; ESG & Sustainability Consulting; Climate Tech Startups; National & Federal Agencies; Local & Municipal Government; Public Safety & Law Enforcement; Diplomatic Services; Social Security & Welfare; GovTech (Digital Government Services); Public Policy & Think Tanks; Charitable Organizations; Foundations & Philanthropy; Civic & Social Advocacy; International Development (NGOs); Churches & Denominations; Parachurch Christian Ministries; Social Enterprises (for-profit impact companies); Impact Investing Organizations; Intelligence & Surveillance; Military Hardware; Private Security Services; Space Defense; Maritime Security; Defense Technology (AI, Cyber, Drones); Dual-Use Startups; Fine Arts & Museums; Live Music & Performing Arts; Film & Television Production; Gaming & eSports; Photography & Visual Arts; Digital Content Creation Studios; Talent Management & Agencies; Market Research; Credit Reporting Agencies; Scientific Research & Development; News & Information Aggregators; Library & Archival Services; Data Analytics & Business Intelligence; AI Data Labeling & Training Services; Satellite Communications; Space Tourism; Launch Services; Orbital Manufacturing; Celestial Research; Space Data & Analytics; Satellite Infrastructure & Ground Systems; Personal Care & Spas; Nutrition & Supplements; Mental Health Services; Bio-hacking & Longevity Clinics; Alternative Medicine; Corporate Wellness Programs; Digital Health & Wellness Apps)
- City (open the company profile, get it from here; if not available search online)
- State/Region
- Country (open the company profile, get it from here; if not available search online)
- Company Size (find the information online)
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
- Full name (fill based on available person on this page)
- First Name
- Last Name
- Title (the specific executive title at THIS company)
- Company name (same as above)
- Company Website (same as above)
- LinkedIn Profile URL (this person's LinkedIn URL)
- City (person's location; if not available search online)
- State/Region (person's location; if not available search online)
- Country (person's location; if not available search online)
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

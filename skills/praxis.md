# Praxis Skill

## Source
**Praxis** — a faith-integrated startup accelerator and investment community that supports founders building ventures around Christian values.

- **Portfolio page:** https://www.praxis.co/portfolio
- **Network affiliation value:** `Praxis`

## When to Use
When harvesting companies and leaders from the Praxis portfolio. Each portfolio card links to an individual company page where the full extraction runs.

## Tool
Comet (Perplexity agent) — primary. Gemini on Chrome — fallback when Perplexity tokens are exhausted.

## Workflow
1. Open https://www.praxis.co/portfolio
2. Open **3 company pages at a time** in new tabs (PC load limit)
3. In each tab, paste the extraction prompt below and run it
4. Use macro to copy the CSV output → switch to .csv file → paste
5. Close those 3 tabs, open the next 3, repeat until all portfolio companies are covered

## Notes
- If a page mentions multiple founders, co-founders, board chairs, or officers — create **one row per person** and duplicate the company fields for each
- Leader LinkedIn URL is often linked from the founder's name on the company page — follow it
- Faith alignment is implicit from Praxis membership; still summarize the specific signal from the page

---

## Extraction Prompt

```
Scrape this page with format:

- Company name
- Website URL
- Industry (value: Technology & Software; Financial Services; Healthcare & Life Sciences; Energy & Utilities; Consumer Products; Industrial Manufacturing; Transportation & Logistics; Communications & Media; Raw Materials & Mining; Professional & Business Services; Real Estate; Construction & Engineering; Hospitality & Leisure; Education & Training; Environmental & Waste Management; Government & Public Sector; Non-Profit & Social Impact; Defense & National Security; Arts, Entertainment & Culture; Information & Data Services; Aerospace & Space Exploration; Wellness & Longevity)
- Sub-Industry (value: Software & SaaS; Hardware & Semiconductors; Cloud Computing & Data Centers; Cybersecurity; Artificial Intelligence & Agents; Web3; Robotics; DevOps & Platform Engineering; IT Services & Managed Service Providers (MSPs); Banking & Lending; Investment Banking / Hedge Fund; Venture Capital / Private Equity; Financial Planning & Advising; Insurance; Fintech & Digital Payments; Real Estate Investment Trusts (REITs); Cryptocurrency & DeFi; Corporate Finance & FP&A; WealthTech / Personal Finance Apps; Pharmaceuticals; Biotechnology; Medical Devices & Equipment; Healthcare Providers & Clinics; Telemedicine & HealthTech; Healthcare Administration & Operations; Clinical Research Organizations (CROs); Oil, Gas & Fossil Fuels; Renewable Energy (Solar, Wind, Hydro); Electric & Water Utilities; Nuclear Energy; Energy Storage & Grid Tech; Energy Consulting & Advisory; EV Charging Infrastructure; Food & Beverage Production; Agriculture & AgTech; Consumer Packaged Goods (CPG); Supermarkets & Grocery; Delivery Services (Food & Other); E-commerce & Digital Retail; Apparel & Luxury Goods; Automotive & EVs; Home Improvement & Furniture; Consumer Electronics; Direct-to-Consumer (DTC) Brands; Marketplaces (Multi-vendor Platforms); Food Tech & Alternative Proteins; Supply Chain & Food Distribution; Aerospace & Defense; Heavy Machinery & Equipment; Electrical Components; Building Products; Automated Manufacturing Systems; Industrial Automation & Controls; Supply Chain Manufacturing Services; Airlines & Aviation Services; Maritime Shipping & Ports; Rail & Road Freight; Courier & Last-Mile Delivery; Supply Chain Management Software; Logistics Tech Platforms (FreightTech / 3PL); Fleet Management & Telematics; Telecommunications Services; Streaming & Digital Content; Broadcasting & Publishing; Advertising & Marketing Tech; Social Media Platforms; Creator Economy Platforms; Public Relations & Communications Firms; Metals & Mining (Gold, Copper, Lithium); Chemicals & Specialty Materials; Forest Products & Paper; Construction Materials (Cement, Glass); Packaging Materials; Battery Materials & Rare Earth Supply Chain; Sustainable Materials & Green Chemistry; Management Consulting; Marketing Agency; Creative & Digital Services; Legal Services; Human Resources & Staffing; Accounting & Audit; BPO (Business Process Outsourcing); Sales & Revenue Operations (RevOps); Customer Success & Support Services; Residential Development; Commercial Property; Property Management; Real Estate Investment Trusts (REITs); PropTech (Real Estate Technology); Residential Construction; Commercial Construction; Civil Engineering & Infrastructure; Architecture & Design; Construction Project Management; Engineering Services (Mechanical, Electrical, Structural); Infrastructure Development; Hotels & Resorts; Restaurants & Food Services; Casinos & Gaming; Sports & Fitness; Travel Agencies & Tour Operators; Event Management & Experiences; Short-Term Rental Platforms; K-12 Education; Higher Education (Universities); EdTech & Online Learning; Vocational & Corporate Training; Professional Development; Executive Coaching; Educational Supplies; Career Services & Job Placement Platforms; Learning Experience Platforms (LXP); Waste Collection & Disposal; Recycling & Circular Economy; Water Treatment; Environmental Consulting; Carbon Capture & Credits; ESG & Sustainability Consulting; Climate Tech Startups; National & Federal Agencies; Local & Municipal Government; Public Safety & Law Enforcement; Diplomatic Services; Social Security & Welfare; GovTech (Digital Government Services); Public Policy & Think Tanks; Charitable Organizations; Foundations & Philanthropy; Civic & Social Advocacy; International Development (NGOs); Churches & Denominations; Parachurch Christian Ministries; Social Enterprises (for-profit impact companies); Impact Investing Organizations; Intelligence & Surveillance; Military Hardware; Private Security Services; Space Defense; Maritime Security; Defense Technology (AI, Cyber, Drones); Dual-Use Startups; Fine Arts & Museums; Live Music & Performing Arts; Film & Television Production; Gaming & eSports; Photography & Visual Arts; Digital Content Creation Studios; Talent Management & Agencies; Market Research; Credit Reporting Agencies; Scientific Research & Development; News & Information Aggregators; Library & Archival Services; Data Analytics & Business Intelligence; AI Data Labeling & Training Services; Satellite Communications; Space Tourism; Launch Services; Orbital Manufacturing; Celestial Research; Space Data & Analytics; Satellite Infrastructure & Ground Systems; Personal Care & Spas; Nutrition & Supplements; Mental Health Services; Bio-hacking & Longevity Clinics; Alternative Medicine; Corporate Wellness Programs; Digital Health & Wellness Apps)
- City
- State/Region
- Country
- Company Size (find the information online)
- Estimated Revenue (find the information online, only summarize the approximate number)
- Primary Leader Name
- Leader LinkedIn URL (You can find it on the founder name link, just follow the link with his name)
- Faith Alignment Category (Summarize and decide for me, value: Explicit; Overt Leader; Implicit)
- Faith signal summary (Summarize for me in 1-2 sentences)
- Faith signal source URL (Put this URL)
- Network Affiliation 1 (value: Faith Driven Entrepreneur; Faith Driven Investor; C12 Business Forums; Convene; Praxis; Christian Economic Forum; CBMC; FGBMFI; International Christian Chamber of Commerce; Kingdom Advisors; Legatus; FCCI; Young Catholic Professionals; BAM Global; U.S. Christian Chamber of Commerce; Other/Custom)
- Network Affiliation 2 (same values as above)
- Network Affiliation 3 (same values as above)
- Hiring likelihood (Summarize from public information, value: High; Medium; Low)
- Industry Priority (Empty this)
- Confidence score (summarize the score, value: 1-5)
- Priority score (empty this)
- Profile status (empty this)
- Date added (fill in today)
- Last updated (fill in today)
- (Blank)
- Full name
- First Name
- Last Name
- Title
- Company name
- Company Website
- LinkedIn Profile URL (same as Leader LinkedIn URL above)
- City
- State/Region
- Country
- Faith Signal Summary (same as above)
- Faith Signal Source (same as above)
- Network Affiliation 1 (same as above)
- Network Affiliation 2 (same as above)
- Network Affiliation 3 (same as above)
- Public Visibility Level (Summarize this, value: Archived; High; Medium)
- Role Seniority (Summarize this, value: Low; Executive; VP; Director)
- Confidence Score (Summarize this, value: 1-5)
- Influence Score (Summarize this, value: 1-5)
- Status (empty this)
- Date added (fill in today)
- Last updated (fill in today)

Rules:
- If the page or related links mention multiple people (founders, co-founders, senior leaders, board chair, fractional executive, or officer roles), create a separate row for each and duplicate the same company fields for each person.
- For every missing input, either summarize from this page or research online; if unknown leave it empty.
- Format the value in CSV format (without the header), use | as separator.
- Remove any source citation hyperlinks. Output plain copyable text only.
```

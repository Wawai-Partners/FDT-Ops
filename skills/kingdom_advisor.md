# Kingdom Advisor Skill

## Source
**Kingdom Advisors (FaithFi)** — a network of Christian financial professionals who have completed the Certified Kingdom Advisor (CKA) designation.

- **Directory page:** https://www.faithfi.com/find-a-cka
- **Network affiliation value:** `Kingdom Advisors`

Also used for:
- **EverSource Wealth Advisors** — https://www.eversourcewealthadvisors.com/ (same extraction prompt, different starting URL)

## When to Use
When harvesting financial advisors and wealth management leaders from the Kingdom Advisors / FaithFi directory, or from EverSource's public advisor listing.

## Tool
Comet (Perplexity agent) — primary. Gemini on Chrome — fallback when Perplexity tokens are exhausted.

## Workflow
1. Open https://www.faithfi.com/find-a-cka
2. Search each city from the city list below (Phase 1, then Phase 2)
3. **Manually review results** — Pick the category, and cherry-pick each advisor; the same advisor often appears under multiple city searches; pick unique individuals only
4. Open selected advisor profiles in new tabs
5. Paste the extraction prompt in each tab and run it
6. Use macro to copy CSV output → switch to .csv file → paste
7. Continue through all cities in the list

## Notes
- Deduplication is manual — one advisor may serve multiple regions and show up in several searches
- The city list below ensures full US coverage across all metro areas and states

---

## City Search List

**Phase 1: Major Metropolitan Areas (High Yield)**
Search top 20 US cities by population using city name only:
- "New York", "Los Angeles", "Chicago", "Houston", "Phoenix"
- "Philadelphia", "San Antonio", "San Diego", "Dallas", "San Jose"
- "Austin", "Jacksonville", "Fort Worth", "Columbus", "Charlotte"
- "San Francisco", "Indianapolis", "Seattle", "Denver", "Washington"

**Phase 2: State-by-State Coverage**

Northeast:
- "Boston, Massachusetts", "Providence, Rhode Island", "Hartford, Connecticut"
- "Albany, New York", "Buffalo, New York", "Rochester, New York"
- "Philadelphia, Pennsylvania", "Pittsburgh, Pennsylvania"
- "Baltimore, Maryland", "Annapolis, Maryland"

Southeast:
- "Atlanta, Georgia", "Augusta, Georgia", "Savannah, Georgia"
- "Miami, Florida", "Tampa, Florida", "Orlando, Florida", "Jacksonville, Florida"
- "Charlotte, North Carolina", "Raleigh, North Carolina", "Greensboro, North Carolina"
- "Columbia, South Carolina", "Charleston, South Carolina"
- "Nashville, Tennessee", "Memphis, Tennessee", "Knoxville, Tennessee"

Midwest:
- "Chicago, Illinois", "Springfield, Illinois", "Peoria, Illinois"
- "Detroit, Michigan", "Grand Rapids, Michigan", "Lansing, Michigan"
- "Minneapolis, Minnesota", "Saint Paul, Minnesota", "Rochester, Minnesota"
- "Columbus, Ohio", "Cleveland, Ohio", "Cincinnati, Ohio"
- "Milwaukee, Wisconsin", "Madison, Wisconsin", "Green Bay, Wisconsin"
- "Indianapolis, Indiana", "Fort Wayne, Indiana", "Evansville, Indiana"
- "Kansas City, Missouri", "St. Louis, Missouri", "Springfield, Missouri"

Southwest:
- "Dallas, Texas", "Houston, Texas", "San Antonio, Texas", "Austin, Texas"
- "Fort Worth, Texas", "El Paso, Texas", "Arlington, Texas"
- "Phoenix, Arizona", "Tucson, Arizona", "Mesa, Arizona"
- "Denver, Colorado", "Colorado Springs, Colorado", "Aurora, Colorado"
- "Albuquerque, New Mexico", "Santa Fe, New Mexico", "Las Cruces, New Mexico"
- "Oklahoma City, Oklahoma", "Tulsa, Oklahoma", "Norman, Oklahoma"

West:
- "Los Angeles, California", "San Diego, California", "San Francisco, California"
- "Sacramento, California", "Fresno, California", "San Jose, California"
- "Seattle, Washington", "Spokane, Washington", "Tacoma, Washington"
- "Portland, Oregon", "Eugene, Oregon", "Salem, Oregon"
- "Salt Lake City, Utah", "Provo, Utah", "Ogden, Utah"
- "Las Vegas, Nevada", "Reno, Nevada", "Henderson, Nevada"
- "Boise, Idaho", "Nampa, Idaho", "Meridian, Idaho"

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
- Leader LinkedIn URL (find the information online)
- Faith Alignment Category (Summarize and decide for me, value: Explicit; Overt Leader; Implicit)
- Faith signal summary (Summarize the company's faith alignment in 1-2 sentences)
- Faith signal source URL (put this URL)
- Network Affiliation 1 (value: Faith Driven Entrepreneur; Faith Driven Investor; C12 Business Forums; Convene; Praxis; Christian Economic Forum; CBMC; FGBMFI; International Christian Chamber of Commerce; Kingdom Advisors; Legatus; FCCI; Young Catholic Professionals; BAM Global; U.S. Christian Chamber of Commerce; Other/Custom)
- Network Affiliation 2 (same values as above)
- Network Affiliation 3 (same values as above)
- Hiring likelihood (Summarize from public information, value: High; Medium; Low)
- Industry Priority (empty this)
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
- LinkedIn Profile URL (same as above)
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

For every missing input, either summarize from this page or research online; if unknown leave it empty. Format the value in CSV format (without the header), use | as separator. Remove any source citation hyperlinks. Output plain copyable text only.
```

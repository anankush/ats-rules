# ATS Rules & Keyword Taxonomy

[![Version](https://img.shields.io/badge/version-4.0.0-blue.svg)](rules.json)
[![Industries](https://img.shields.io/badge/industries-44-emerald.svg)](rules.json)
[![Keywords](https://img.shields.io/badge/keywords-822-indigo.svg)](rules.json)
[![Action Verbs](https://img.shields.io/badge/action__verbs-221-violet.svg)](rules.json)
[![Format](https://img.shields.io/badge/format-JSON-orange.svg)](rules.json)

A production-grade, dynamic ruleset and keyword taxonomy for modern **Applicant Tracking Systems (ATS)**, resume scoring engines, and CV builders.

This repository provides standardized evaluation criteria, industry-specific keyword dictionaries, power action verbs, and scoring weights to analyze resumes with high accuracy against modern ATS filters (Workday, Taleo, Greenhouse, Lever, etc.).

---

## Live Endpoint

Consume the latest rules directly in your application via GitHub's raw CDN:

```http
GET https://raw.githubusercontent.com/anankush/ats-rules/main/rules.json
```

---

## Features

- **44 Specialized Industry Taxonomies**: Covers software engineering, healthcare, legal, finance, aviation, maritime, trades, creative arts, agriculture, and civil services.
- **822 Curated High-Impact Keywords**: Extracted from real job descriptions and ATS parsing criteria to maximize matching accuracy.
- **221 Power Action Verbs**: Classified across leadership, engineering, clinical, litigation, financial, and analytical execution.
- **Weighted Multi-Factor Scoring Engine**: Standardized 100-point rubric assessing keyword density, verb strength, quantifiable metrics, and section completeness.
- **Dynamic Hot-Reloading**: Built for zero-downtime updates. Resume builders and parsers can poll or sync rules at runtime without redeploying application code.
- **Zero Dependencies**: Pure, valid JSON compatible with any language (TypeScript/JavaScript, Python, Go, Rust, Java, C#).

---

## Scoring Architecture

Resumes evaluated against this ruleset are scored on a standardized 100-point scale:

```
┌─────────────────────────────────────────────────────────────┐
│                   Total ATS Score (100)                     │
├─────────────────────┬───────────────────┬───────────────────┤
│ Keyword Match (45%) │ Action Verbs (25%)│ Metrics (15%)     │
├─────────────────────┴───────────────────┼───────────────────┤
│ Section Completeness (15%)              │ Weak Penalty (0%) │
└─────────────────────────────────────────┴───────────────────┘
```

| Criteria | Weight | Purpose |
| :--- | :---: | :--- |
| **`keywordMatch`** | **45%** | Measures presence of industry-specific technical and domain keywords. If a target job description is provided, measures direct lexical overlap. |
| **`actionVerbs`** | **25%** | Evaluates whether experience bullet points begin with strong, proactive verbs rather than passive phrases. |
| **`metricsAndNumbers`** | **15%** | Rewards quantifiable achievements (e.g., `%`, `$`, `₹`, numeric improvements, scale indicators). |
| **`sectionCompleteness`** | **15%** | Verifies existence of essential ATS sections: Contact Info, Summary/Objective, Experience, Education, and Skills. |

---

## Schema Specification

`rules.json` adheres to the following contract:

```json
{
  "version": "4.0.0",
  "lastUpdated": "2026-10-31",
  "scoringWeights": {
    "keywordMatch": 45,
    "actionVerbs": 25,
    "metricsAndNumbers": 15,
    "sectionCompleteness": 15
  },
  "actionVerbs": [
    "Spearheaded",
    "Architected",
    "Orchestrated",
    "Directed",
    "Pioneered",
    "Championed"
  ],
  "weakPhrases": [],
  "industryKeywords": {
    "Frontend & Web": [
      "React",
      "Next.js",
      "TypeScript",
      "Tailwind CSS",
      "Redux"
    ]
  }
}
```

### Field Definitions

| Field | Type | Description |
| :--- | :--- | :--- |
| `version` | `string` | Semantic version of the ruleset. |
| `lastUpdated` | `string` | ISO date of latest taxonomy expansion (`YYYY-MM-DD`). |
| `scoringWeights` | `object` | Weights allocated to the 4 evaluation pillars (sums to 100). |
| `actionVerbs` | `string[]` | 221 high-impact action verbs across all professions. |
| `weakPhrases` | `string[]` | Passive or filler phrases that reduce resume impact. |
| `industryKeywords` | `Record<string, string[]>` | Mapping of 44 industry names to their high-frequency ATS keywords. |

---

## Industry Taxonomy Breakdown

The taxonomy covers **44 industries** and **822 keywords**:

### 1. Technology & Engineering (126 Keywords)
- **Frontend & Web** (19): React, Next.js, Vue, Angular, TypeScript, JavaScript, HTML5, CSS3, Tailwind CSS, Redux, GraphQL, REST APIs, Webpack, Vite, WebSockets, SSR, Responsive Design, Jest, Cypress.
- **Backend & Systems** (20): Node.js, Express, NestJS, Python, Django, FastAPI, Java, Spring Boot, Go (Golang), C++, Rust, PostgreSQL, MySQL, MongoDB, Redis, Kafka, Microservices, System Design, gRPC, Docker.
- **Cloud & DevOps** (14): AWS, Azure, GCP, Kubernetes, Docker, Terraform, CI/CD, GitHub Actions, Jenkins, Ansible, Helm, Monitoring, Prometheus, Grafana.
- **Data Science & AI** (17): Machine Learning, Deep Learning, PyTorch, TensorFlow, Scikit-learn, Pandas, NumPy, NLP, LLM, Computer Vision, Data Analysis, SQL, Power BI, Tableau, Feature Engineering, Model Deployment, MLOps.
- **Mobile & Game Development** (18): React Native, Flutter, Swift, SwiftUI, Kotlin, Android SDK, iOS SDK, Unity, Unreal Engine, C#, Mobile UI/UX, In-App Purchases, Game Physics, Shaders, AR/VR, App Store Optimization, Firebase, Memory Management.
- **QA & Software Testing** (18): Manual Testing, Automated Testing, Selenium, Cypress, Playwright, TestNG, JUnit, Postman, API Testing, Performance Testing, JMeter, Bug Tracking, JIRA, Test Plans, Regression Testing, Smoke Testing, CI/CD Integration, Quality Assurance.

### 2. Business, Finance & Legal (145 Keywords)
- **Finance & Banking** (23): Financial Modeling, Valuation, Equity Research, Risk Management, Portfolio Management, Investment Banking, Asset Management, Wealth Management, Financial Analysis, DCF, M&A, Credit Analysis, Basel III, Capital Markets, Hedge Funds, Trading, Derivatives, Treasury, Compliance, KYC, AML, Credit Risk, Bloomberg Terminal.
- **Accounting & Tax** (27): Financial Reporting, US GAAP, IFRS, Auditing, Internal Controls, Tax Compliance, Corporate Tax, GST, VAT, Income Tax, General Ledger, Accounts Payable, Accounts Receivable, Bank Reconciliation, Payroll Accounting, QuickBooks, SAP ERP, Tally, Cost Accounting, Variance Analysis, SOX Compliance, Balance Sheet, P&L, Cash Flow, Fixed Assets, Forensic Accounting, Financial Statements.
- **Legal & Law** (25): Contract Drafting, Litigation, Legal Research, Due Diligence, Corporate Governance, Intellectual Property, Trademarks, Patents, Copyrights, Commercial Law, Mergers & Acquisitions, Regulatory Compliance, Dispute Resolution, Arbitration, Mediation, Employment Law, GDPR, Privacy Law, Legal Writing, Civil Litigation, Criminal Defense, Client Counseling, Brief Writing, Westlaw, LexisNexis.
- **Product & Management** (11): Product Strategy, Roadmap, User Stories, Agile, Scrum, Kanban, Product Discovery, Market Research, Feature Prioritization, Wireframing, Stakeholder Management.
- **Compliance & Secretarial** (13): Corporate Governance, Statutory Compliance, Board Meetings, Secretarial Audits, Due Diligence, Annual Filings, Regulatory Affairs, Shareholder Relations, Risk Assessment, Policy Drafting, Code of Conduct, Internal Audit, Ethics Compliance.
- **Insurance & Actuarial** (16): Underwriting, Actuarial Science, Risk Assessment, Claims Processing, Policy Administration, Reinsurance, Loss Prevention, Pricing Models, Solvency II, Life Insurance, Health Insurance, General Insurance, Actuarial Modeling, Reserve Calculation, Regulatory Compliance, Risk Mitigation.
- **Real Estate & Property** (16): Property Management, Real Estate Development, Lease Administration, Commercial Real Estate, Residential Sales, Tenant Relations, Valuation, Due Diligence, Zoning Laws, Property Acquisition, Facility Management, Asset Management, Real Estate Finance, Contract Negotiation, Escrow, Market Analysis.

### 3. Healthcare & Life Sciences (88 Keywords)
- **Healthcare & Medical** (28): Patient Assessment, Diagnosis, Treatment Planning, Electronic Health Records (EHR), Epic Systems, Cerner, Clinical Care, Patient Safety, Infection Control, Medical Terminology, Pharmacology, HIPAA, BLS, ACLS, CPR, Vital Signs, Phlebotomy, Patient Triage, Medical Records, Clinical Research, Wound Care, Medication Administration, Healthcare Administration, Telehealth, Medical Ethics, Patient Education, Diagnostic Testing, Surgery Preparation.
- **Nursing & Caregiving** (20): Patient Care, Nursing Assessment, Medication Administration, IV Therapy, Vital Signs Monitoring, Wound Care, Care Plans, Infection Control, BLS, ACLS, Patient Advocacy, Bedside Manner, ICU, Emergency Care, Pediatric Nursing, Geriatric Care, Palliative Care, EHR Documentation, Patient Triage, Patient Education.
- **Dental & Allied Health** (20): Dental Hygiene, Teeth Cleaning, Dental Radiography, Cavity Treatment, Dental Restorations, Patient Education, Sterilization Protocols, Chairside Assisting, Prosthodontics, Periodontics, Endodontics, Dental Surgery, Orthodontic Assisting, Impressions, Dental Software, Medical Equipment Operation, Patient Triage, Infection Prevention, Fluoride Treatments, Sealant Application.
- **Pharmacy & Life Sciences** (20): Prescription Dispensing, Pharmacology, Drug Interactions, Medication Therapy Management, Clinical Trials, Pharmacokinetics, Biopharmaceuticals, Regulatory Compliance, FDA Regulations, Good Manufacturing Practice (GMP), Drug Formulation, Pharmacovigilance, Compounding, Inventory Management, Patient Counseling, Microbiology, Biochemistry, Laboratory Analysis, SOP Development, Quality Control.

### 4. Operations, Infrastructure, Maritime & Aviation (111 Keywords)
- **Transportation & Logistics** (20): Supply Chain Management, Fleet Management, Route Optimization, Freight Forwarding, Warehousing, Inventory Management, Logistics Operations, 3PL, Dispatching, Customs Clearance, Material Handling, Last-Mile Delivery, Cold Chain, Safety Compliance, Shipping Documentation, Carrier Negotiations, ERP Systems, Demand Planning, Procurement, Vendor Management.
- **Construction & Civil Engineering** (22): Structural Analysis, Project Management, AutoCAD, Revit, Construction Estimation, Site Supervision, Quality Control, Building Codes, Concrete Technology, Geotechnical Engineering, Surveying, Civil 3D, Safety Compliance, OSHA, Blueprint Reading, Cost Estimation, Subcontractor Management, Structural Design, Project Scheduling, BIM, Urban Planning, Foundation Engineering.
- **Manufacturing & Industrial** (19): Lean Manufacturing, Six Sigma, Continuous Improvement, Quality Assurance, Production Planning, Kaizen, 5S, Plant Operations, Machine Operation, Maintenance Engineering, Root Cause Analysis, Supply Chain Optimization, Inventory Control, Safety Protocols, ISO 9001, Process Automation, CNC Programming, Preventive Maintenance, Value Stream Mapping.
- **Telecom & Networking** (20): Network Engineering, TCP/IP, Routing & Switching, Cisco Systems, CCNA, CCNP, Firewalls, VPN, LAN/WAN, BGP, OSPF, Network Security, Troubleshooting, VoIP, 5G, LTE, Wireless Networks, Optical Fiber, SDN, Load Balancing.
- **Energy & Power** (18): Power Systems, Electrical Engineering, Renewable Energy, Solar Power, Wind Energy, Grid Operations, Power Generation, High Voltage, Substation Design, Energy Efficiency, SCADA, Power Distribution, Transformer Maintenance, Commissioning, Power Quality, Regulatory Compliance, Electrical Safety, Smart Grids.
- **Oil & Gas / Petrochemicals** (16): Drilling Engineering, Reservoir Engineering, Petroleum Geology, Refinery Operations, Pipeline Integrity, Process Engineering, Offshore Operations, Safety Management, HAZOP, Environmental Compliance, Petrochemical Processing, Well Completion, Production Optimization, Asset Integrity, Commissioning, Natural Gas.
- **Aviation & Airlines** (19): Flight Operations, Aircraft Maintenance, Avionics, Pilot In Command, Air Traffic Control, FAA Regulations, ICAO Standards, Safety Management Systems (SMS), Pre-Flight Inspection, Crew Resource Management, Aircraft Systems, Aviation Security, Flight Planning, Ground Operations, Jet Engines, Navigation Systems, Emergency Procedures, Airworthiness, Line Maintenance.
- **Shipping & Maritime** (18): Maritime Operations, Ship Navigation, Cargo Operations, Seamanship, Marine Engineering, Port Operations, STCW Compliance, Vessel Safety, ISM Code, Ballast Management, Deck Operations, Shiphandling, Radar/ARPA, Marine Diesel Engines, Bulk Cargo Handling, Maritime Law, Oil Spill Response, Classification Societies.
- **Fire & Industrial Safety** (19): Fire Protection, Industrial Safety, Hazard Identification, OSHA Compliance, Emergency Response, Risk Assessment, Incident Investigation, Fire Suppression Systems, Safety Audits, PPE Compliance, Safety Training, Disaster Management, EHS Management, Fire Alarm Systems, Hazardous Materials (HAZMAT), Root Cause Analysis, Loss Prevention, Evacuation Planning, First Aid.
- **Security & Defense Services** (20): Physical Security, Surveillance Operations, Threat Assessment, Access Control, Asset Protection, Security Protocols, Crisis Management, Investigation, VIP Protection, CCTV Monitoring, Risk Mitigation, Security Guarding, Defense Tactics, Perimeter Security, Report Writing, Law Enforcement, Incident Management, Crowd Control, Anti-Terrorism, Emergency Procedures.

### 5. Services, Sales, Design & Public Sector (232 Keywords)
- **Marketing & Sales** (25): SEO, SEM, Content Marketing, Social Media Marketing, Google Ads, Email Marketing, Lead Generation, B2B Sales, B2C Sales, CRM, Salesforce, HubSpot, Sales Pipeline, Conversion Rate Optimization (CRO), Market Research, Brand Strategy, Inbound Marketing, Outbound Sales, Account Management, Cold Calling, Copywriting, Campaign Management, Product Marketing, Revenue Operations, KPI Tracking.
- **Design (Graphic & UX/UI)** (21): UI Design, UX Research, Figma, Adobe XD, Photoshop, Illustrator, Prototyping, Wireframing, User Personas, Usability Testing, Interaction Design, Design Systems, Typography, Layout Design, Visual Identity, Information Architecture, Motion Graphics, Branding, Responsive Design, Design Thinking, User Journeys.
- **Hospitality & Hotel Management** (22): Front Office Operations, Guest Relations, Housekeeping Management, Food & Beverage (F&B), Banquet Management, Revenue Management, Reservation Systems, Opera PMS, Customer Satisfaction, Event Planning, Hospitality Operations, Concierge Services, Staff Training, Menu Planning, Inventory Control, Hospitality Marketing, Service Standards, Crisis Management, Tourism Management, VIP Services, Quality Assurance, Hospitality Sales.
- **Retail & E-commerce** (21): Retail Sales, Store Management, Merchandising, E-commerce Operations, Inventory Management, Point of Sale (POS), Customer Experience, Shopify, Visual Merchandising, Order Fulfillment, Loss Prevention, Product Listing, Sales Optimization, Payment Gateways, Customer Retention, Upselling, Vendor Coordination, Omnichannel Retail, Returns Management, Pricing Strategy, Supply Chain Coordination.
- **Education & Teaching** (21): Curriculum Development, Lesson Planning, Classroom Management, Student Assessment, Differentiated Instruction, Educational Technology, Special Education, STEM Education, Educational Leadership, Parent Communication, Learning Outcomes, Standardized Testing, Teacher Training, Online Teaching, Child Development, Instructional Design, Literacy Instruction, Pedagogical Strategies, Classroom Technology, Academic Advising, Student Engagement.
- **HR & Recruitment** (20): Talent Acquisition, Full-Lifecycle Recruiting, Sourcing, Technical Recruitment, Interviewing, Onboarding, Employee Relations, HR Policies, Performance Management, Compensation & Benefits, HRIS, Workday, LinkedIn Recruiter, Applicant Tracking Systems (ATS), Employee Engagement, Conflict Resolution, Exit Interviews, Diversity & Inclusion, Labor Laws, Training & Development.
- **Government & Civil Services** (19): Public Policy, Public Administration, Government Affairs, Policy Analysis, Regulatory Enforcement, Interagency Coordination, Community Outreach, Public Budgeting, Legislative Affairs, Program Evaluation, Grant Management, Civil Service Regulations, Public Relations, Stakeholder Engagement, Crisis Response, Administrative Law, Strategic Planning, Governance, Citizen Services.
- **Media & Journalism** (19): Investigative Journalism, News Writing, Editorial Direction, Copy Editing, Feature Writing, Interviewing, Fact-Checking, Content Strategy, Storytelling, Podcasting, Broadcast Journalism, Video Editing, Digital Media, Social Media Strategy, AP Style, Press Releases, Media Production, Proofreading, Publishing.
- **Agriculture & Farming** (19): Agronomy, Crop Management, Soil Science, Precision Agriculture, Irrigation Systems, Farm Management, Pest Control, Sustainable Agriculture, Livestock Management, Greenhouse Operations, Harvesting, Seed Technology, Fertilization, Organic Farming, Agrochemicals, Agricultural Machinery, Supply Chain, Food Safety, Crop Yield Optimization.
- **Skilled Trades & Automotive** (16): Automotive Repair, Welding, Electrical Wiring, Plumbing, HVAC Installation, Engine Diagnostics, Mechanical Maintenance, Blueprint Reading, Brake Systems, Fabrication, Equipment Troubleshooting, Soldering, Preventive Maintenance, Pipefitting, Power Tools, Workshop Safety.
- **NGO & Social Work** (15): Community Development, Program Management, Fundraising, Grant Writing, Social Advocacy, Stakeholder Engagement, Non-Profit Leadership, Volunteer Coordination, Case Management, Social Justice, Humanitarian Aid, Monitoring & Evaluation (M&E), Field Operations, Capacity Building, Policy Advocacy.
- **Admin & Back Office** (16): Office Administration, Executive Assistance, Calendar Management, Data Entry, Document Management, Travel Coordination, Expense Reporting, Meeting Facilitation, Front Desk Operations, Records Management, Procurement, Customer Support, Billing, Correspondence, Filing Systems, Administrative Support.
- **Library & Information Science** (14): Cataloging, Metadata Management, Archival Preservation, Reference Services, Information Retrieval, Digital Libraries, Database Searching, Collection Development, Library Management Systems, Indexing, Research Assistance, Classification Systems, Document Archiving, Information Literacy.
- **Fashion & Textiles** (15): Fashion Design, Textile Manufacturing, Pattern Making, Garment Construction, Apparel Production, Trend Forecasting, Fabric Sourcing, Quality Control, Merchandising, Tech Packs, Fashion Styling, Draping, CAD for Fashion, Retail Merchandising, Sustainable Fashion.
- **Beauty & Wellness** (13): Cosmetology, Skincare, Hair Styling, Esthetics, Spa Treatments, Makeup Artistry, Client Consultation, Sanitation Standards, Product Sales, Salon Management, Wellness Coaching, Massage Therapy, Beauty Therapy.
- **Sports & Fitness** (15): Personal Training, Fitness Assessment, Exercise Physiology, Strength & Conditioning, Nutrition Planning, Group Fitness, Sports Coaching, Injury Rehabilitation, Workout Programming, Athletic Training, Health Promotion, Wellness Coaching, Client Motivation, Kinesiology, Sports Science.
- **Travel & Tourism** (15): Tour Operations, Travel Planning, Itinerary Creation, Tourism Marketing, Destination Management, Ticketing Systems, GDS Systems, Amadeus, Sabre, Client Relations, Visa Assistance, Group Travel, Hospitality Coordination, Cultural Tourism, Adventure Tourism.

---

## Action Verbs Library

The `actionVerbs` array contains **221 power verbs** formatted in past tense, optimized for initial-bullet parsing in ATS parsers:

- **Leadership & Strategy**: *Spearheaded, Architected, Orchestrated, Directed, Pioneered, Championed, Oversaw, Guided, Mentored, Mobilized, Delegated, Formulated, Steered, Governed, Commanded...*
- **Technical & Engineering**: *Engineered, Implemented, Developed, Deployed, Refactored, Optimized, Automated, Integrated, Debugged, Scaled, Provisioned, Benchmarked, Hardened, Overhauled...*
- **Analytics & Research**: *Analyzed, Modeled, Evaluated, Forecasted, Quantified, Benchmarked, Investigated, Synthesized, Discovered, Validated, Interpreted, Tracked...*
- **Clinical & Scientific**: *Diagnosed, Treated, Administered, Prescribed, Rehabilitated, Resuscitated, Cultured, Synthesized, Dispensed, Triage...*
- **Legal & Compliance**: *Litigated, Drafted, Arbitrated, Prosecuted, Defended, Advised, Represented, Mediated, Adjudicated, Audited...*
- **Revenue & Business Growth**: *Accelerated, Maximized, Negotiated, Closed, Prospected, Captured, Monetized, Expanded, Outperformed...*

---

## Integration Examples

### TypeScript / Node.js

```typescript
interface ATSRules {
  version: string;
  lastUpdated: string;
  scoringWeights: {
    keywordMatch: number;
    actionVerbs: number;
    metricsAndNumbers: number;
    sectionCompleteness: number;
  };
  actionVerbs: string[];
  weakPhrases: string[];
  industryKeywords: Record<string, string[]>;
}

async function fetchLatestAtsRules(): Promise<ATSRules> {
  const url = "https://raw.githubusercontent.com/anankush/ats-rules/main/rules.json";
  const response = await fetch(url);
  if (!response.ok) {
    throw new Error(`Failed to fetch ATS rules: ${response.statusText}`);
  }
  return response.json();
}

// Example evaluation logic
function evaluateResumeBullets(bullets: string[], rules: ATSRules): number {
  let strongBullets = 0;
  for (const bullet of bullets) {
    const firstWord = bullet.trim().split(/\s+/)[0];
    if (rules.actionVerbs.some(v => v.toLowerCase() === firstWord.toLowerCase())) {
      strongBullets++;
    }
  }
  return bullets.length > 0 ? (strongBullets / bullets.length) * 100 : 0;
}
```

### Python

```python
import requests
import re

RULES_URL = "https://raw.githubusercontent.com/anankush/ats-rules/main/rules.json"

def get_ats_rules() -> dict:
    response = requests.get(RULES_URL, timeout=10)
    response.raise_for_status()
    return response.json()

def match_industry_keywords(resume_text: str, industry: str, rules: dict) -> dict:
    keywords = rules.get("industryKeywords", {}).get(industry, [])
    found = []
    missing = []
    
    for kw in keywords:
        pattern = r"\b" + re.escape(kw) + r"\b"
        if re.search(pattern, resume_text, re.IGNORECASE):
            found.append(kw)
        else:
            missing.append(kw)
            
    match_score = (len(found) / len(keywords) * 100) if keywords else 0
    return {
        "score": round(match_score, 2),
        "found": found,
        "missing": missing
    }
```

---

## Contributing

1. **Adding an Industry**:
   Ensure all new industries contain a minimum of 12 verified, high-frequency ATS keywords.
2. **Adding Action Verbs**:
   Use strong past-tense transitive verbs that convey concrete outcomes. Avoid weak/passive verbs (*assisted, helped, was responsible for*).
3. **Format**:
   Keep `rules.json` strictly formatted with 2-space indentation. Maintain alphabetical ordering where applicable.

---

## License

MIT License. Free for commercial, personal, and educational ATS applications.

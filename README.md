# ATS Rules & Keyword Taxonomy

[![Version](https://img.shields.io/badge/version-5.0.0-blue.svg)](rules.json)
[![Industries](https://img.shields.io/badge/industries-66-emerald.svg)](rules.json)
[![Keywords](https://img.shields.io/badge/keywords-1262-indigo.svg)](rules.json)
[![Action Verbs](https://img.shields.io/badge/action__verbs-261-violet.svg)](rules.json)
[![Weak Phrases](https://img.shields.io/badge/weak__phrases-20-rose.svg)](rules.json)
[![Format](https://img.shields.io/badge/format-JSON-orange.svg)](rules.json)

Dynamic, production-grade ruleset and keyword taxonomy for modern **Applicant Tracking Systems (ATS)**, resume scoring engines, and CV builders.

---

## Quick Start (Raw CDN)

Access the live JSON ruleset directly in your app:

```http
GET https://raw.githubusercontent.com/anankush/ats-rules/main/rules.json
```

---

## Scoring Architecture

Evaluated on a standardized 100-point scale:

| Criteria | Weight | Purpose |
| :--- | :---: | :--- |
| **`keywordMatch`** | **45%** | Matches industry domain terms and target job description tokens. |
| **`actionVerbs`** | **25%** | Validates bullet points start with strong, proactive past-tense verbs. |
| **`metricsAndNumbers`** | **15%** | Rewards quantifiable metrics (`%`, `$`, `₹`, numbers, scale indicators). |
| **`sectionCompleteness`** | **15%** | Ensures core sections exist (Contact, Summary, Experience, Education, Skills). |

---

## Taxonomy Overview (66 Sectors · 1,262 Keywords)

| Domain | Sectors | Total Keywords | Sample Coverage |
| :--- | :---: | :---: | :--- |
| **1. Technology & Computing** | 12 | 244 | Web, Systems, Cloud, AI/ML, Cybersecurity, Robotics, Embedded |
| **2. Engineering & Trades** | 11 | 231 | Aerospace, EV, Renewable, Civil, Mining, Industrial Safety |
| **3. Healthcare & Life Sciences** | 6 | 128 | Clinical Care, Nursing, Biotech, Pharma, Veterinary, Dental |
| **4. Business, Finance & Legal** | 10 | 185 | Banking, Accounting, Legal, Sourcing, CSM, HR, Real Estate |
| **5. Creative, Media & Design** | 7 | 161 | Architecture, UI/UX, 3D/VFX, Video, PR, Technical Writing |
| **6. Services, Public & Logistics** | 20 | 313 | Supply Chain, Aviation, Maritime, Sales, Hospitality, Education |

---

## Sectors & Keywords Directory

<details>
<summary><b>1. Technology & Computing (12 Sectors · 244 Keywords)</b></summary>

<br>

| Sector | Keywords Count | Key Focus & Tokens |
| :--- | :---: | :--- |
| **Frontend & Web** | 19 | React, Next.js, Vue, Angular, TypeScript, Tailwind CSS, Redux, GraphQL, REST APIs, Vite |
| **Backend & Systems** | 20 | Node.js, Express, Python, Django, FastAPI, Java, Spring Boot, Go, PostgreSQL, Microservices |
| **Cloud & DevOps** | 14 | AWS, Azure, GCP, Kubernetes, Docker, Terraform, CI/CD, GitHub Actions, Prometheus |
| **Cybersecurity & InfoSec** | 20 | Penetration Testing, SOC, Incident Response, SIEM, CISSP, Zero Trust, Cryptography, EDR |
| **Data Science & AI** | 17 | Machine Learning, Deep Learning, PyTorch, TensorFlow, NLP, LLM, Computer Vision, MLOps |
| **Hardware & Embedded** | 20 | Firmware, PCB Design, FPGA, Verilog, Microcontrollers, RTOS, IoT, Altium, Oscilloscopes |
| **Mobile & Game Dev** | 18 | React Native, Flutter, Swift, SwiftUI, Kotlin, Unity, Unreal Engine, Mobile UI/UX, Shaders |
| **QA & Software Testing** | 18 | Automation, Selenium, Cypress, Playwright, API Testing, Performance Testing, JMeter, JIRA |
| **Blockchain & FinTech** | 20 | Smart Contracts, Solidity, Ethereum, DeFi, Tokenomics, Cryptography, DApps, Web3.js |
| **Robotics & Automation** | 20 | ROS, Kinematics, PLC, SCADA, Computer Vision, SLAM, Cobots, Mechatronics, Actuators |
| **Telecom & Networking** | 20 | TCP/IP, Cisco, CCNA, CCNP, Firewalls, VPN, BGP, OSPF, VoIP, 5G, Optical Fiber |
| **Instructional Design & EdTech** | 20 | ADDIE, LMS, Canvas, Moodle, Articulate 360, SCORM, Curriculum Mapping, Gamification |

</details>

<details>
<summary><b>2. Engineering & Trades (11 Sectors · 231 Keywords)</b></summary>

<br>

| Sector | Keywords Count | Key Focus & Tokens |
| :--- | :---: | :--- |
| **Aerospace & Defense** | 20 | Aerodynamics, Propulsion, Orbital Mechanics, Spacecraft, Avionics, CFD, GNC, AS9100 |
| **Automotive & EV** | 20 | EV Powertrains, Battery Pack, ADAS, CAN Bus, MATLAB/Simulink, Crash Safety, ISO 26262 |
| **Renewable & CleanTech** | 20 | Solar PV, Wind Turbine, BESS, Inverters, Energy Auditing, PVsyst, Microgrid, Decarbonization |
| **Civil & Construction** | 22 | Structural Analysis, AutoCAD, Revit, Site Supervision, Concrete, Surveying, BIM, OSHA |
| **Manufacturing & Industrial** | 19 | Lean Manufacturing, Six Sigma, Continuous Improvement, Kaizen, 5S, ISO 9001, CNC, Automation |
| **Energy & Power** | 18 | Power Systems, Electrical Engineering, Grid Operations, High Voltage, Substation, SCADA |
| **Oil, Gas & Petrochem** | 16 | Drilling, Reservoir Engineering, Refinery Operations, Pipeline Integrity, HAZOP, Natural Gas |
| **Mining & Geosciences** | 20 | Exploration, Geotechnical, Open-Pit, Smelting, Geological Mapping, Blasting, GIS, Tailings |
| **Skilled Trades & Auto Repair** | 16 | Welding, Electrical Wiring, Plumbing, HVAC, Engine Diagnostics, Soldering, Preventive Maintenance |
| **Fire & Industrial Safety** | 19 | Fire Protection, Hazard Identification, OSHA, Emergency Response, EHS, HAZMAT, Safety Audits |
| **Environmental & ESG** | 20 | ESG Reporting, Carbon Footprint, EIA, Life Cycle Assessment (LCA), Circular Economy, ISO 14001 |

</details>

<details>
<summary><b>3. Healthcare & Life Sciences (6 Sectors · 128 Keywords)</b></summary>

<br>

| Sector | Keywords Count | Key Focus & Tokens |
| :--- | :---: | :--- |
| **Healthcare & Medical** | 28 | Patient Assessment, Diagnosis, EHR, Epic, Cerner, Clinical Care, HIPAA, BLS, ACLS, CPR |
| **Nursing & Caregiving** | 20 | Patient Care, Nursing Assessment, IV Therapy, Vital Signs, Wound Care, ICU, Patient Advocacy |
| **Dental & Allied Health** | 20 | Dental Hygiene, Dental Radiography, Sterilization Protocols, Prosthodontics, Chairside Assisting |
| **Pharmacy & Life Sciences** | 20 | Dispensing, Pharmacology, Clinical Trials, Pharmacokinetics, GMP, Pharmacovigilance, HPLC |
| **Biotechnology & Biomedical** | 20 | CRISPR-Cas9, PCR, Cell Culture, DNA Sequencing, NGS, Bioinformatics, Medical Device Design |
| **Veterinary & Animal Health** | 20 | Veterinary Medicine, Surgical Assistance, Diagnostics, Pharmacology, Anesthesia, Pathology |

</details>

<details>
<summary><b>4. Business, Finance & Legal (10 Sectors · 185 Keywords)</b></summary>

<br>

| Sector | Keywords Count | Key Focus & Tokens |
| :--- | :---: | :--- |
| **Finance & Banking** | 23 | Financial Modeling, Valuation, Equity Research, Risk Management, M&A, Basel III, Bloomberg |
| **Accounting & Tax** | 27 | Financial Reporting, US GAAP, IFRS, Auditing, Corporate Tax, General Ledger, SAP, SOX |
| **Legal & Law** | 25 | Contract Drafting, Litigation, Legal Research, Due Diligence, IP, Corporate Governance, Arbitration |
| **Product Management** | 11 | Product Strategy, Roadmap, User Stories, Agile, Scrum, Feature Prioritization, Wireframing |
| **Compliance & Secretarial** | 13 | Statutory Compliance, Secretarial Audits, Board Meetings, Risk Assessment, Policy Drafting |
| **Insurance & Actuarial** | 16 | Underwriting, Actuarial Science, Claims Processing, Solvency II, Reserve Calculation, Risk Models |
| **Real Estate & Property** | 16 | Property Management, Development, Lease Admin, Commercial Sales, Due Diligence, Valuation |
| **Customer Success (CSM)** | 20 | CSM, Zendesk, Salesforce Service Cloud, Churn Reduction, CSAT, NPS, SLA Management |
| **Procurement & Sourcing** | 20 | Strategic Sourcing, RFP/RFQ, Vendor Evaluation, SRM, Contract Negotiation, Spend Analysis |
| **HR & Recruitment** | 20 | Talent Acquisition, Full-Lifecycle Recruiting, Sourcing, Onboarding, HRIS, Workday, ATS |

</details>

<details>
<summary><b>5. Creative, Media, Architecture & Writing (7 Sectors · 161 Keywords)</b></summary>

<br>

| Sector | Keywords Count | Key Focus & Tokens |
| :--- | :---: | :--- |
| **Architecture & Interiors** | 20 | Architectural Design, Space Planning, BIM, Revit, AutoCAD, 3D Rendering, LEED, FF&E |
| **Design (Graphic & UX/UI)** | 21 | UI Design, UX Research, Figma, Adobe XD, Design Systems, Typography, Wireframing |
| **Animation, 3D & VFX** | 20 | 3D Animation, Blender, Maya, ZBrush, Houdini, Rigging, VFX Compositing, Nuke, Unreal |
| **Film & Video Production** | 20 | Video Editing, Premiere Pro, DaVinci Resolve, Cinematography, Sound Design, Color Grading |
| **Media & Journalism** | 19 | News Writing, Investigative Journalism, Editorial Direction, Fact-Checking, AP Style |
| **PR & Communications** | 20 | Press Releases, Media Relations, Crisis Communication, Brand Reputation, Thought Leadership |
| **Writing & Content** | 20 | Technical Writing, SEO Writing, Copywriting, API Docs, Markdown, Style Guides, Ghostwriting |

</details>

<details>
<summary><b>6. Services, Public Sector & Logistics (20 Sectors · 313 Keywords)</b></summary>

<br>

| Sector | Keywords Count | Key Focus & Tokens |
| :--- | :---: | :--- |
| **Logistics & Supply Chain** | 20 | Supply Chain Management, Fleet Management, 3PL, Route Optimization, Freight, Warehousing |
| **Aviation & Airlines** | 19 | Flight Operations, Aircraft Maintenance, Pilot In Command, ATC, FAA, Aircraft Systems |
| **Shipping & Maritime** | 18 | Ship Navigation, Cargo Operations, Marine Engineering, STCW, Port Operations, ISM Code |
| **Security & Defense** | 20 | Physical Security, Surveillance, Threat Assessment, Access Control, Investigation, CCTV |
| **Marketing & Sales** | 25 | SEO, SEM, Content Marketing, Google Ads, CRM, B2B Sales, HubSpot, Conversion Rate (CRO) |
| **Hospitality & Hotel** | 22 | Front Office, Guest Relations, F&B, Opera PMS, Banquet Management, Service Standards |
| **Event Production** | 20 | Corporate Event Planning, Venue Sourcing, Run-of-Show, Stage Management, AV Production |
| **Food Science & Culinary** | 20 | Culinary Arts, HACCP, Food Safety, Menu Engineering, Food Production, ServSafe, Sanitation |
| **Retail & E-commerce** | 21 | Retail Sales, Store Management, Merchandising, POS, Shopify, Order Fulfillment, Retention |
| **Education & Teaching** | 21 | Curriculum Development, Lesson Planning, Classroom Management, Assessment, STEM, Advising |
| **Psychology & Counseling** | 20 | Psychotherapy, CBT, Mental Health Assessment, Crisis Intervention, DSM-5, Trauma-Informed |
| **Government & Civil Services** | 19 | Public Policy, Administration, Regulatory Enforcement, Interagency Coordination, Governance |
| **NGO & Social Work** | 15 | Community Development, Fundraising, Grant Writing, Social Advocacy, Humanitarian Aid, M&E |
| **Admin & Back Office** | 16 | Office Administration, Executive Assistance, Calendar Management, Billing, Records Management |
| **Library & Info Science** | 14 | Cataloging, Metadata Management, Archival Preservation, Digital Libraries, Indexing |
| **Fashion & Textiles** | 15 | Fashion Design, Textile Manufacturing, Pattern Making, Garment Construction, Tech Packs |
| **Beauty & Wellness** | 13 | Cosmetology, Skincare, Hair Styling, Esthetics, Spa Treatments, Client Consultation |
| **Sports & Fitness** | 15 | Personal Training, Exercise Physiology, Strength & Conditioning, Nutrition Planning |
| **Travel & Tourism** | 15 | Tour Operations, Itinerary Creation, Tourism Marketing, GDS Systems, Amadeus, Sabre |
| **Agriculture & Farming** | 19 | Agronomy, Crop Management, Soil Science, Precision Agriculture, Irrigation, Pest Control |

</details>

---

## Action Verbs (261 Verbs by Role)

| Functional Group | Count | Sample Verbs |
| :--- | :---: | :--- |
| **Leadership & Strategy** | 45 | *Spearheaded, Architected, Orchestrated, Directed, Pioneered, Championed, Oversaw, Guided, Commanded* |
| **Engineering & Tech** | 55 | *Engineered, Implemented, Deployed, Automated, Refactored, Optimized, Fortified, Calibrated, Fabricated* |
| **Analytics & Science** | 40 | *Analyzed, Modeled, Evaluated, Forecasted, Investigated, Synthesized, Sequenced, Assayed, Surveyed* |
| **Clinical & Healthcare** | 35 | *Diagnosed, Treated, Administered, Prescribed, Rehabilitated, Resuscitated, Triaged, Vaccinated* |
| **Revenue & Commercial** | 40 | *Accelerated, Maximized, Negotiated, Closed, Prospected, Captured, Monetized, Sourced, Procured* |
| **Creative & Media** | 46 | *Authored, Presented, Campaigned, Storyboarded, Conceptualized, Rigged, Composited, Curated, Styled* |

---

## Weak Phrase Detection (20 Flags)

Bullets starting with or containing these passive phrases trigger ATS recommendations:

| Weak / Passive Phrase | Recommended Power Verb Alternative |
| :--- | :--- |
| `worked on`, `worked with` | **Engineered**, **Developed**, **Architected** |
| `responsible for`, `in charge of` | **Spearheaded**, **Oversaw**, **Directed** |
| `helped with`, `helped the team` | **Collaborated**, **Facilitated**, **Accelerated** |
| `assisted in`, `aided in` | **Partnered**, **Supported**, **Co-authored** |
| `tried to`, `attempted to` | **Implemented**, **Executed**, **Tested** |
| `participated in`, `took part in` | **Contributed**, **Mobilized**, **Delivered** |
| `handled tasks`, `duties included` | **Managed**, **Streamlined**, **Resolved** |
| `tasked with`, `assigned to` | **Delegated**, **Commissioned**, **Pioneered** |
| `looked after`, `served as` | **Administered**, **Governed**, **Mentored** |

---

## Code Integration

### TypeScript / Node.js

```typescript
interface ATSRules {
  version: string;
  lastUpdated: string;
  scoringWeights: Record<string, number>;
  actionVerbs: string[];
  weakPhrases: string[];
  industryKeywords: Record<string, string[]>;
}

async function getAtsRules(): Promise<ATSRules> {
  const res = await fetch("https://raw.githubusercontent.com/anankush/ats-rules/main/rules.json");
  if (!res.ok) throw new Error("Failed to load ATS rules");
  return res.json();
}
```

### Python

```python
import requests

RULES_URL = "https://raw.githubusercontent.com/anankush/ats-rules/main/rules.json"

def get_ats_rules() -> dict:
    return requests.get(RULES_URL, timeout=10).json()
```

---

## License

MIT License. Free for open-source and commercial ATS applications.

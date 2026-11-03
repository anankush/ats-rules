# ATS Rules & Keyword Taxonomy

[![Version](https://img.shields.io/badge/version-5.0.0-blue.svg)](rules.json)
[![Industries](https://img.shields.io/badge/industries-66-emerald.svg)](rules.json)
[![Keywords](https://img.shields.io/badge/keywords-1262-indigo.svg)](rules.json)
[![Action Verbs](https://img.shields.io/badge/action__verbs-261-violet.svg)](rules.json)
[![Weak Phrases](https://img.shields.io/badge/weak__phrases-20-rose.svg)](rules.json)
[![Format](https://img.shields.io/badge/format-JSON-orange.svg)](rules.json)

A comprehensive, production-grade ruleset and keyword taxonomy for modern **Applicant Tracking Systems (ATS)**, resume scoring engines, and CV builders.

This repository provides standardized evaluation criteria, cross-industry keyword dictionaries, power action verbs, passive phrase flags, and scoring weights to analyze resumes with high accuracy against modern ATS algorithms (Workday, Taleo, Greenhouse, Lever, iCIMS, Bullhorn, etc.).

---

## Live Endpoint

Consume the latest rules directly in your application via GitHub's raw CDN:

```http
GET https://raw.githubusercontent.com/anankush/ats-rules/main/rules.json
```

---

## What's New in v5.0.0

- **22 New Industry Sectors Added** (expanding from 44 to **66 distinct job markets**).
- **1,262 Curated High-Impact Keywords** (+440 newly researched ATS tokens).
- **261 Power Action Verbs** (+40 new domain-specific action verbs).
- **20 Detected Weak & Passive Phrases** (`weakPhrases` dictionary for real-time penalty and suggestion flagging).
- Comprehensive coverage of emerging markets: Cybersecurity, Robotics, EV Engineering, Blockchain/Web3, EdTech, ESG/Sustainability, Biotech, Architecture, and Customer Success.

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
  "version": "5.0.0",
  "lastUpdated": "2026-11-03",
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
    "Fortified",
    "Pioneered"
  ],
  "weakPhrases": [
    "worked on",
    "responsible for",
    "helped with"
  ],
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
| `actionVerbs` | `string[]` | 261 high-impact action verbs across all professions. |
| `weakPhrases` | `string[]` | 20 passive or filler phrases that reduce resume impact. |
| `industryKeywords` | `Record<string, string[]>` | Mapping of 66 industry names to their high-frequency ATS keywords. |

---

## Complete Industry Taxonomy (66 Sectors & 1,262 Keywords)

### 1. Technology, Software & Computing (244 Keywords)
- **Frontend & Web** (19): React, Next.js, Vue, Angular, TypeScript, JavaScript, HTML5, CSS3, Tailwind CSS, Redux, GraphQL, REST APIs, Webpack, Vite, WebSockets, SSR, Responsive Design, Jest, Cypress.
- **Backend & Systems** (20): Node.js, Express, NestJS, Python, Django, FastAPI, Java, Spring Boot, Go (Golang), C++, Rust, PostgreSQL, MySQL, MongoDB, Redis, Kafka, Microservices, System Design, gRPC, Docker.
- **Cloud & DevOps** (14): AWS, Azure, GCP, Kubernetes, Docker, Terraform, CI/CD, GitHub Actions, Jenkins, Ansible, Helm, Monitoring, Prometheus, Grafana.
- **Cybersecurity & Information Security** (20): Penetration Testing, SOC, Incident Response, SIEM, CISSP, CEH, Vulnerability Assessment, Threat Intelligence, ISO 27001, Zero Trust, Cryptography, Identity & Access Management (IAM), Endpoint Detection & Response (EDR), Malware Analysis, Digital Forensics, Network Firewalls, Security Audits, SOC 2 Compliance, Ethical Hacking, Threat Hunting.
- **Data Science & AI** (17): Machine Learning, Deep Learning, PyTorch, TensorFlow, Scikit-learn, Pandas, NumPy, NLP, LLM, Computer Vision, Data Analysis, SQL, Power BI, Tableau, Feature Engineering, Model Deployment, MLOps.
- **Hardware, Embedded Systems & Semiconductor** (20): Firmware Development, PCB Design, FPGA, Verilog, VHDL, Microcontrollers, Embedded C, RTOS, Internet of Things (IoT), Sensors & Actuators, ASIC Design, Circuit Design, Oscilloscopes, Soldering & Assembly, Altium Designer, I2C / SPI / UART, Hardware Debugging, Schematic Capture, Logic Analyzers, Signal Integrity.
- **Mobile & Game Development** (18): React Native, Flutter, Swift, SwiftUI, Kotlin, Android SDK, iOS SDK, Unity, Unreal Engine, C#, Mobile UI/UX, In-App Purchases, Game Physics, Shaders, AR/VR, App Store Optimization, Firebase, Memory Management.
- **QA & Software Testing** (18): Manual Testing, Automated Testing, Selenium, Cypress, Playwright, TestNG, JUnit, Postman, API Testing, Performance Testing, JMeter, Bug Tracking, JIRA, Test Plans, Regression Testing, Smoke Testing, CI/CD Integration, Quality Assurance.
- **Blockchain, Web3 & FinTech** (20): Blockchain Architecture, Smart Contract Development, Solidity, Ethereum Virtual Machine (EVM), Web3.js & Ethers.js, Decentralized Finance (DeFi), Tokenomics Design, Applied Cryptography, Consensus Mechanisms, Distributed Ledger Technology (DLT), Decentralized Applications (DApps), Hardhat & Foundry, InterPlanetary File System (IPFS), NFT Smart Contracts, Crypto Wallet Integration, Payment Gateway APIs, Algorithmic Trading Systems, Core Banking Integration, Anti-Money Laundering (AML) Compliance, FinTech APIs.
- **Robotics, Mechatronics & Industrial Automation** (20): Robotics Engineering, Robot Operating System (ROS), Robot Kinematics & Dynamics, Motion Planning Algorithms, PLC Programming, Industrial SCADA Systems, Servo Drives & Actuators, Computer Vision for Robotics, Simultaneous Localization and Mapping (SLAM), Industrial Automation Engineering, Mechatronics Design, Collaborative Robots (Cobots), Autonomous Mobile Robots (AMR), Sensor Integration, Inverse Kinematics, Pneumatic & Hydraulic Controls, Robotic End-Effector Design, Factory Automation Workcells, Motor Control Systems, Safety PLC & Interlocks.
- **Telecom & Networking** (20): Network Engineering, TCP/IP, Routing & Switching, Cisco Systems, CCNA, CCNP, Firewalls, VPN, LAN/WAN, BGP, OSPF, Network Security, Troubleshooting, VoIP, 5G, LTE, Wireless Networks, Optical Fiber, SDN, Load Balancing.
- **Instructional Design & EdTech** (20): Instructional Systems Design, ADDIE Model, Learning Management Systems (LMS), Canvas LMS, Moodle, E-Learning Course Authoring, Articulate Storyline 360, Adobe Captivate, SCORM & xAPI Standards, Curriculum Mapping, Learning Needs Assessment, Microlearning Development, Adult Learning Principles, Formative & Summative Assessment, Educational Multimedia Design, Blended Learning Strategy, Interactive Video Modules, Educational Gamification, Course Evaluation & Feedback, Training Program Delivery.

### 2. Engineering, Infrastructure, Energy & Trades (231 Keywords)
- **Aerospace & Defense Engineering** (20): Aerodynamics, Propulsion Systems, Orbital Mechanics, Spacecraft Systems, Avionics Engineering, Flight Control Systems, Satellite Communications, Computational Fluid Dynamics (CFD), Structural Dynamics, Missile Guidance Systems, Radar & Sensor Systems, Systems Engineering, Finite Element Analysis (FEA), Telemetry Systems, Payload Integration, Wind Tunnel Testing, Space Thermal Analysis, Guidance, Navigation & Control (GNC), Defense Contracting Compliance, AS9100 Quality Standards.
- **Automotive Engineering & Electric Vehicles (EV)** (20): Automotive Systems Design, Electric Vehicle (EV) Powertrains, Battery Pack Engineering, Advanced Driver Assistance Systems (ADAS), CAN Bus Protocol, MATLAB & Simulink Modeling, Vehicle Dynamics Simulation, Crash & Impact Safety, Thermal Management Systems, Chassis Engineering, ISO 26262 Functional Safety, Transmission & Drivetrain, Automotive Telematics, Internal Combustion Engines (ICE), Autonomous Driving Technology, Sensor Fusion Algorithms, Engine & ECU Calibration, Homologation & Compliance, Automotive Suspension Tuning, Vehicle Noise, Vibration & Harshness (NVH).
- **Renewable Energy, Solar & CleanTech** (20): Solar Photovoltaic (PV) Design, Wind Turbine Engineering, Battery Energy Storage Systems (BESS), Battery Management Systems (BMS), Inverter Technologies, Grid Interconnection Standards, Clean Energy Policy, Energy Auditing, EV Charging Infrastructure Design, Power Generation Modeling, PVsyst Software, Microgrid Architecture, Net Energy Metering, System Commissioning, Power Purchase Agreements (PPA), Renewable Resource Assessment, CleanTech Innovation, Industrial Decarbonization, Substation Intertie, Energy Conservation Measures.
- **Construction & Civil Engineering** (22): Structural Analysis, Project Management, AutoCAD, Revit, Construction Estimation, Site Supervision, Quality Control, Building Codes, Concrete Technology, Geotechnical Engineering, Surveying, Civil 3D, Safety Compliance, OSHA, Blueprint Reading, Cost Estimation, Subcontractor Management, Structural Design, Project Scheduling, BIM, Urban Planning, Foundation Engineering.
- **Manufacturing & Industrial** (19): Lean Manufacturing, Six Sigma, Continuous Improvement, Quality Assurance, Production Planning, Kaizen, 5S, Plant Operations, Machine Operation, Maintenance Engineering, Root Cause Analysis, Supply Chain Optimization, Inventory Control, Safety Protocols, ISO 9001, Process Automation, CNC Programming, Preventive Maintenance, Value Stream Mapping.
- **Energy & Power** (18): Power Systems, Electrical Engineering, Renewable Energy, Solar Power, Wind Energy, Grid Operations, Power Generation, High Voltage, Substation Design, Energy Efficiency, SCADA, Power Distribution, Transformer Maintenance, Commissioning, Power Quality, Regulatory Compliance, Electrical Safety, Smart Grids.
- **Oil & Gas / Petrochemicals** (16): Drilling Engineering, Reservoir Engineering, Petroleum Geology, Refinery Operations, Pipeline Integrity, Process Engineering, Offshore Operations, Safety Management, HAZOP, Environmental Compliance, Petrochemical Processing, Well Completion, Production Optimization, Asset Integrity, Commissioning, Natural Gas.
- **Mining, Metallurgy & Geosciences** (20): Mineral Exploration, Mining Engineering, Geotechnical Engineering, Open-Pit Mining, Underground Mining, Mineral Processing, Blasting Operations, Mine Safety Standards, Ore Reserve Estimation, Extractive Metallurgy, Smelting Operations, Geological Mapping, Exploration Drilling, Mine Feasibility Studies, Environmental Reclamation, Mine Planning Software, Geographic Information Systems (GIS), Hydrogeology, Mine Ventilation, Tailings Dam Management.
- **Skilled Trades & Automotive** (16): Automotive Repair, Welding, Electrical Wiring, Plumbing, HVAC Installation, Engine Diagnostics, Mechanical Maintenance, Blueprint Reading, Brake Systems, Fabrication, Equipment Troubleshooting, Soldering, Preventive Maintenance, Pipefitting, Power Tools, Workshop Safety.
- **Fire & Industrial Safety** (19): Fire Protection, Industrial Safety, Hazard Identification, OSHA Compliance, Emergency Response, Risk Assessment, Incident Investigation, Fire Suppression Systems, Safety Audits, PPE Compliance, Safety Training, Disaster Management, EHS Management, Fire Alarm Systems, Hazardous Materials (HAZMAT), Root Cause Analysis, Loss Prevention, Evacuation Planning, First Aid.
- **Environmental Science, ESG & Sustainability** (20): ESG Reporting, Carbon Footprint Calculation, Environmental Impact Assessment (EIA), Sustainability Auditing, Waste Management, Life Cycle Assessment (LCA), Greenhouse Gas (GHG) Accounting, Climate Resilience, Circular Economy, Biodiversity Conservation, Environmental Compliance, Water Resource Management, Renewable Energy Strategy, Environmental Policy, ISO 14001, Pollution Abatement, Ecological Monitoring, Net Zero Strategies, Resource Conservation, Carbon Offsetting.

### 3. Healthcare, Medicine & Life Sciences (128 Keywords)
- **Healthcare & Medical** (28): Patient Assessment, Diagnosis, Treatment Planning, Electronic Health Records (EHR), Epic Systems, Cerner, Clinical Care, Patient Safety, Infection Control, Medical Terminology, Pharmacology, HIPAA, BLS, ACLS, CPR, Vital Signs, Phlebotomy, Patient Triage, Medical Records, Clinical Research, Wound Care, Medication Administration, Healthcare Administration, Telehealth, Medical Ethics, Patient Education, Diagnostic Testing, Surgery Preparation.
- **Nursing & Caregiving** (20): Patient Care, Nursing Assessment, Medication Administration, IV Therapy, Vital Signs Monitoring, Wound Care, Care Plans, Infection Control, BLS, ACLS, Patient Advocacy, Bedside Manner, ICU, Emergency Care, Pediatric Nursing, Geriatric Care, Palliative Care, EHR Documentation, Patient Triage, Patient Education.
- **Dental & Allied Health** (20): Dental Hygiene, Teeth Cleaning, Dental Radiography, Cavity Treatment, Dental Restorations, Patient Education, Sterilization Protocols, Chairside Assisting, Prosthodontics, Periodontics, Endodontics, Dental Surgery, Orthodontic Assisting, Impressions, Dental Software, Medical Equipment Operation, Patient Triage, Infection Prevention, Fluoride Treatments, Sealant Application.
- **Pharmacy & Life Sciences** (20): Prescription Dispensing, Pharmacology, Drug Interactions, Medication Therapy Management, Clinical Trials, Pharmacokinetics, Biopharmaceuticals, Regulatory Compliance, FDA Regulations, Good Manufacturing Practice (GMP), Drug Formulation, Pharmacovigilance, Compounding, Inventory Management, Patient Counseling, Microbiology, Biochemistry, Laboratory Analysis, SOP Development, Quality Control.
- **Biotechnology & Biomedical Engineering** (20): CRISPR-Cas9, Polymerase Chain Reaction (PCR), Cell Culture, DNA Sequencing, Gene Editing, Next-Generation Sequencing (NGS), Bioinformatics, Medical Device Design, Bioreactors, Western Blotting, Chromatography, Assay Development, Biomaterials, Molecular Biology, Protein Purification, FDA 510(k), Tissue Engineering, Microfluidics, Good Laboratory Practice (GLP), High-Performance Liquid Chromatography (HPLC).
- **Veterinary & Animal Health** (20): Veterinary Medicine, Animal Care & Welfare, Surgical Assistance, Animal Husbandry, Clinical Diagnostics, Veterinary Pharmacology, Vaccination Administration, Animal Behavior Assessment, Anesthesia Monitoring, Dental Prophylaxis, Radiography & Ultrasound, Zoonotic Disease Control, Emergency Animal Triage, Pet Nutrition, Practice Management Software, Client Communication, Electronic Veterinary Records, Laboratory Pathology, Animal Restraint Protocols, Parasitology.

### 4. Business, Finance, Legal & Management (185 Keywords)
- **Finance & Banking** (23): Financial Modeling, Valuation, Equity Research, Risk Management, Portfolio Management, Investment Banking, Asset Management, Wealth Management, Financial Analysis, DCF, M&A, Credit Analysis, Basel III, Capital Markets, Hedge Funds, Trading, Derivatives, Treasury, Compliance, KYC, AML, Credit Risk, Bloomberg Terminal.
- **Accounting & Tax** (27): Financial Reporting, US GAAP, IFRS, Auditing, Internal Controls, Tax Compliance, Corporate Tax, GST, VAT, Income Tax, General Ledger, Accounts Payable, Accounts Receivable, Bank Reconciliation, Payroll Accounting, QuickBooks, SAP ERP, Tally, Cost Accounting, Variance Analysis, SOX Compliance, Balance Sheet, P&L, Cash Flow, Fixed Assets, Forensic Accounting, Financial Statements.
- **Legal & Law** (25): Contract Drafting, Litigation, Legal Research, Due Diligence, Corporate Governance, Intellectual Property, Trademarks, Patents, Copyrights, Commercial Law, Mergers & Acquisitions, Regulatory Compliance, Dispute Resolution, Arbitration, Mediation, Employment Law, GDPR, Privacy Law, Legal Writing, Civil Litigation, Criminal Defense, Client Counseling, Brief Writing, Westlaw, LexisNexis.
- **Product & Management** (11): Product Strategy, Roadmap, User Stories, Agile, Scrum, Kanban, Product Discovery, Market Research, Feature Prioritization, Wireframing, Stakeholder Management.
- **Compliance & Secretarial** (13): Corporate Governance, Statutory Compliance, Board Meetings, Secretarial Audits, Due Diligence, Annual Filings, Regulatory Affairs, Shareholder Relations, Risk Assessment, Policy Drafting, Code of Conduct, Internal Audit, Ethics Compliance.
- **Insurance & Actuarial** (16): Underwriting, Actuarial Science, Risk Assessment, Claims Processing, Policy Administration, Reinsurance, Loss Prevention, Pricing Models, Solvency II, Life Insurance, Health Insurance, General Insurance, Actuarial Modeling, Reserve Calculation, Regulatory Compliance, Risk Mitigation.
- **Real Estate & Property** (16): Property Management, Real Estate Development, Lease Administration, Commercial Real Estate, Residential Sales, Tenant Relations, Valuation, Due Diligence, Zoning Laws, Property Acquisition, Facility Management, Asset Management, Real Estate Finance, Contract Negotiation, Escrow, Market Analysis.
- **Customer Success & Client Support** (20): Customer Success Management (CSM), Zendesk, Salesforce Service Cloud, Churn Reduction, Customer Retention, Client Onboarding, Customer Satisfaction (CSAT), Net Promoter Score (NPS), Escalation Management, Ticket Resolution, Service Level Agreements (SLA), Omnichannel Support, Customer Advocacy, Account Renewal, Technical Support, CRM Maintenance, Help Desk Management, Upselling & Cross-selling, Product Adoption, Incident Triage.
- **Procurement, Sourcing & Supply Management** (20): Strategic Sourcing, RFP & RFQ Management, Vendor Evaluation, Supplier Relationship Management (SRM), Contract Negotiation, Purchase Order (PO) Processing, Category Management, Spend Analysis, Cost Reduction Initiatives, Inventory Optimization, Supply Chain Risk Management, Global Sourcing, Contract Lifecycle Management, E-Procurement Platforms, Supplier Quality Audits, Purchase Requisitioning, Total Cost of Ownership (TCO), Logistics Procurement, Vendor Compliance Monitoring, Invoice Reconciliation.
- **HR & Recruitment** (20): Talent Acquisition, Full-Lifecycle Recruiting, Sourcing, Technical Recruitment, Interviewing, Onboarding, Employee Relations, HR Policies, Performance Management, Compensation & Benefits, HRIS, Workday, LinkedIn Recruiter, Applicant Tracking Systems (ATS), Employee Engagement, Conflict Resolution, Exit Interviews, Diversity & Inclusion, Labor Laws, Training & Development.

### 5. Creative, Media, Architecture & Writing (161 Keywords)
- **Architecture & Interior Design** (20): Architectural Design, Space Planning, Building Information Modeling (BIM), Revit, AutoCAD, 3D Rendering, SketchUp, V-Ray, Building Codes, LEED Certification, Construction Drawings, Material Specification, Interior Styling, Facade Engineering, Zoning Regulations, Sustainable Architecture, Site Planning, Lighting Design, Millwork Detailing, FF&E Specification.
- **Design (Graphic & UX/UI)** (21): UI Design, UX Research, Figma, Adobe XD, Photoshop, Illustrator, Prototyping, Wireframing, User Personas, Usability Testing, Interaction Design, Design Systems, Typography, Layout Design, Visual Identity, Information Architecture, Motion Graphics, Branding, Responsive Design, Design Thinking, User Journeys.
- **Animation, 3D Modeling & VFX** (20): 3D Animation, 3D Modeling, Blender, Autodesk Maya, ZBrush, Houdini, Character Rigging, Texture Mapping, VFX Compositing, Nuke, Unreal Engine Cine, Motion Design, CGI Generation, Storyboarding, Keyframe Animation, UV Unwrapping, Particle Simulations, Photorealistic Rendering, Lighting & Shading, Concept Art.
- **Film, Audio & Video Production** (20): Video Editing, Adobe Premiere Pro, DaVinci Resolve, Final Cut Pro, Cinematography, Sound Design, Audio Mixing & Mastering, Camera Operation, Studio Lighting, Motion Graphics, After Effects, Storyboarding, Post-Production Workflow, Scriptwriting, Color Grading, Film Directing, Foley & Sound Effects, Live Streaming Production, Broadcast Operations, Production Scheduling.
- **Media & Journalism** (19): Investigative Journalism, News Writing, Editorial Direction, Copy Editing, Feature Writing, Interviewing, Fact-Checking, Content Strategy, Storytelling, Podcasting, Broadcast Journalism, Video Editing, Digital Media, Social Media Strategy, AP Style, Press Releases, Media Production, Proofreading, Publishing.
- **Public Relations & Corporate Communications** (20): Press Releases, Media Relations, Crisis Communication, Corporate Communications, Brand Reputation Management, Media Pitching, Strategic Messaging, Internal Communications, Event Coordination, Speechwriting, Stakeholder Engagement, Public Affairs, Media Monitoring, Company Spokesperson, Press Conferences, Thought Leadership, Brand Storytelling, Influencer Partnerships, Media Kits, Publicity Campaigns.
- **Content Creation, Copywriting & Technical Writing** (20): Technical Writing, Direct Response Copywriting, Content Marketing Strategy, SEO Content Optimization, Software Documentation, REST API Documentation, Proofreading & Editing, Blog Editorial Calendars, Content Management Systems (CMS), WordPress Administration, Markdown Authoring, Style Guide Adherence, Ghostwriting, White Paper Development, Customer Case Studies, Creative Copywriting, Brand Tone of Voice, Audience Persona Targeting, Microcopy & UX Writing, Editorial Workflow Management.

### 6. Logistics, Services, Public Sector & Social (313 Keywords)
- **Transportation & Logistics** (20): Supply Chain Management, Fleet Management, Route Optimization, Freight Forwarding, Warehousing, Inventory Management, Logistics Operations, 3PL, Dispatching, Customs Clearance, Material Handling, Last-Mile Delivery, Cold Chain, Safety Compliance, Shipping Documentation, Carrier Negotiations, ERP Systems, Demand Planning, Procurement, Vendor Management.
- **Aviation & Airlines** (19): Flight Operations, Aircraft Maintenance, Avionics, Pilot In Command, Air Traffic Control, FAA Regulations, ICAO Standards, Safety Management Systems (SMS), Pre-Flight Inspection, Crew Resource Management, Aircraft Systems, Aviation Security, Flight Planning, Ground Operations, Jet Engines, Navigation Systems, Emergency Procedures, Airworthiness, Line Maintenance.
- **Shipping & Maritime** (18): Maritime Operations, Ship Navigation, Cargo Operations, Seamanship, Marine Engineering, Port Operations, STCW Compliance, Vessel Safety, ISM Code, Ballast Management, Deck Operations, Shiphandling, Radar/ARPA, Marine Diesel Engines, Bulk Cargo Handling, Maritime Law, Oil Spill Response, Classification Societies.
- **Security & Defense Services** (20): Physical Security, Surveillance Operations, Threat Assessment, Access Control, Asset Protection, Security Protocols, Crisis Management, Investigation, VIP Protection, CCTV Monitoring, Risk Mitigation, Security Guarding, Defense Tactics, Perimeter Security, Report Writing, Law Enforcement, Incident Management, Crowd Control, Anti-Terrorism, Emergency Procedures.
- **Marketing & Sales** (25): SEO, SEM, Content Marketing, Social Media Marketing, Google Ads, Email Marketing, Lead Generation, B2B Sales, B2C Sales, CRM, Salesforce, HubSpot, Sales Pipeline, Conversion Rate Optimization (CRO), Market Research, Brand Strategy, Inbound Marketing, Outbound Sales, Account Management, Cold Calling, Copywriting, Campaign Management, Product Marketing, Revenue Operations, KPI Tracking.
- **Hospitality & Hotel Management** (22): Front Office Operations, Guest Relations, Housekeeping Management, Food & Beverage (F&B), Banquet Management, Revenue Management, Reservation Systems, Opera PMS, Customer Satisfaction, Event Planning, Hospitality Operations, Concierge Services, Staff Training, Menu Planning, Inventory Control, Hospitality Marketing, Service Standards, Crisis Management, Tourism Management, VIP Services, Quality Assurance, Hospitality Sales.
- **Event Management & Production** (20): Corporate Event Planning, Event Budget Administration, Vendor Coordination, Venue Sourcing & Contracting, Live Event Production, Stage & Show Management, Catering Coordination, Attendee Registration Platforms, Corporate Sponsorship Acquisition, Audio-Visual (AV) Production, Vendor Contract Negotiation, Run-of-Show Schedules, Event Marketing & Promotion, Floor Plan Layout Design, On-Site Event Execution, Hospitality Logistics, Virtual & Hybrid Conferences, Event Ticketing Platforms, Post-Event Analytics, VIP Guest Protocol.
- **Culinary Arts, Food Science & Beverage** (20): Culinary Arts, Food Safety Protocols, HACCP Compliance, Menu Engineering, Food Preparation, Recipe Development, Kitchen Management, Food Sanitation, Quality Control (QC), Commercial Food Production, Baking & Pastry, Inventory Control, ServSafe Certification, Beverage Management, Sensory Evaluation, Nutritional Analysis, Food Packaging, Fermentation Science, Food Cost Control, Catering Operations.
- **Retail & E-commerce** (21): Retail Sales, Store Management, Merchandising, E-commerce Operations, Inventory Management, Point of Sale (POS), Customer Experience, Shopify, Visual Merchandising, Order Fulfillment, Loss Prevention, Product Listing, Sales Optimization, Payment Gateways, Customer Retention, Upselling, Vendor Coordination, Omnichannel Retail, Returns Management, Pricing Strategy, Supply Chain Coordination.
- **Education & Teaching** (21): Curriculum Development, Lesson Planning, Classroom Management, Student Assessment, Differentiated Instruction, Educational Technology, Special Education, STEM Education, Educational Leadership, Parent Communication, Learning Outcomes, Standardized Testing, Teacher Training, Online Teaching, Child Development, Instructional Design, Literacy Instruction, Pedagogical Strategies, Classroom Technology, Academic Advising, Student Engagement.
- **Psychology, Counseling & Mental Health** (20): Psychotherapy, Cognitive Behavioral Therapy (CBT), Mental Health Assessment, Crisis Intervention, Psychological Counseling, Case Management, Clinical Psychology, Group Therapy Facilitation, DSM-5 Diagnostics, Diagnostic Evaluation, Trauma-Informed Care, Patient Advocacy, Individual Treatment Planning, Behavioral Health Intervention, Substance Abuse Counseling, Psychoeducation, Clinical Documentation, Family Systems Therapy, Mental Health Screenings, Mindfulness-Based Interventions.
- **Government & Civil Services** (19): Public Policy, Public Administration, Government Affairs, Policy Analysis, Regulatory Enforcement, Interagency Coordination, Community Outreach, Public Budgeting, Legislative Affairs, Program Evaluation, Grant Management, Civil Service Regulations, Public Relations, Stakeholder Engagement, Crisis Response, Administrative Law, Strategic Planning, Governance, Citizen Services.
- **NGO & Social Work** (15): Community Development, Program Management, Fundraising, Grant Writing, Social Advocacy, Stakeholder Engagement, Non-Profit Leadership, Volunteer Coordination, Case Management, Social Justice, Humanitarian Aid, Monitoring & Evaluation (M&E), Field Operations, Capacity Building, Policy Advocacy.
- **Admin & Back Office** (16): Office Administration, Executive Assistance, Calendar Management, Data Entry, Document Management, Travel Coordination, Expense Reporting, Meeting Facilitation, Front Desk Operations, Records Management, Procurement, Customer Support, Billing, Correspondence, Filing Systems, Administrative Support.
- **Library & Information Science** (14): Cataloging, Metadata Management, Archival Preservation, Reference Services, Information Retrieval, Digital Libraries, Database Searching, Collection Development, Library Management Systems, Indexing, Research Assistance, Classification Systems, Document Archiving, Information Literacy.
- **Fashion & Textiles** (15): Fashion Design, Textile Manufacturing, Pattern Making, Garment Construction, Apparel Production, Trend Forecasting, Fabric Sourcing, Quality Control, Merchandising, Tech Packs, Fashion Styling, Draping, CAD for Fashion, Retail Merchandising, Sustainable Fashion.
- **Beauty & Wellness** (13): Cosmetology, Skincare, Hair Styling, Esthetics, Spa Treatments, Makeup Artistry, Client Consultation, Sanitation Standards, Product Sales, Salon Management, Wellness Coaching, Massage Therapy, Beauty Therapy.
- **Sports & Fitness** (15): Personal Training, Fitness Assessment, Exercise Physiology, Strength & Conditioning, Nutrition Planning, Group Fitness, Sports Coaching, Injury Rehabilitation, Workout Programming, Athletic Training, Health Promotion, Wellness Coaching, Client Motivation, Kinesiology, Sports Science.
- **Travel & Tourism** (15): Tour Operations, Travel Planning, Itinerary Creation, Tourism Marketing, Destination Management, Ticketing Systems, GDS Systems, Amadeus, Sabre, Client Relations, Visa Assistance, Group Travel, Hospitality Coordination, Cultural Tourism, Adventure Tourism.
- **Agriculture & Farming** (19): Agronomy, Crop Management, Soil Science, Precision Agriculture, Irrigation Systems, Farm Management, Pest Control, Sustainable Agriculture, Livestock Management, Greenhouse Operations, Harvesting, Seed Technology, Fertilization, Organic Farming, Agrochemicals, Agricultural Machinery, Supply Chain, Food Safety, Crop Yield Optimization.

---

## Action Verbs Library (261 Verbs)

Formatted in past tense for ATS bullet-point validation:

- **Executive & Leadership**: *Spearheaded, Architected, Orchestrated, Directed, Pioneered, Championed, Oversaw, Guided, Mentored, Mobilized, Delegated, Formulated, Steered, Governed, Commanded, Onboarded, Hosted...*
- **Engineering & Systems**: *Engineered, Implemented, Developed, Deployed, Refactored, Optimized, Automated, Integrated, Debugged, Scaled, Provisioned, Benchmarked, Hardened, Fortified, Remediated, Calibrated, Fabricated, Soldered, Machined, Prototyped...*
- **Analytics & Research**: *Analyzed, Modeled, Evaluated, Forecasted, Quantified, Benchmarked, Investigated, Synthesized, Discovered, Validated, Interpreted, Tracked, Appraised, Surveyed...*
- **Clinical & Biomedical**: *Diagnosed, Treated, Administered, Prescribed, Rehabilitated, Resuscitated, Cultured, Synthesized, Dispensed, Triaged, Sequenced, Purified, Assayed, Anesthetized, Vaccinated, Medicated...*
- **Legal & Compliance**: *Litigated, Drafted, Arbitrated, Prosecuted, Defended, Advised, Represented, Mediated, Adjudicated, Audited, Certified...*
- **Commercial & Revenue**: *Accelerated, Maximized, Negotiated, Closed, Prospected, Captured, Monetized, Expanded, Outperformed, Procured, Sourced, Reconciled, Staked, Minted, Tokenized...*
- **Communications, Media & Design**: *Authored, Presented, Campaigned, Pitched, Broadcasted, Publicized, Ghostwrote, Copyedited, Curated, Rendered, Storyboarded, Conceptualized, Rigged, Animated, Composited, Scored...*

---

## Detected Weak Phrases (20 Passive Flags)

ATS systems downgrade passive or low-ownership descriptions. The ruleset identifies the following weak phrases in resume bullets:

```
"worked on", "responsible for", "helped with", "assisted in", "tried to",
"participated in", "handled tasks", "was involved in", "duties included",
"tasked with", "assigned to", "attempted to", "helped the team", "looked after",
"in charge of", "served as", "worked with", "aided in", "took part in", "supported in"
```

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

def check_bullet_strength(bullet: str, rules: dict) -> dict:
    bullet_lower = bullet.lower()
    weak_found = [wp for wp in rules.get("weakPhrases", []) if wp in bullet_lower]
    first_word = bullet.strip().split()[0] if bullet.strip() else ""
    has_action_verb = any(v.lower() == first_word.lower() for v in rules.get("actionVerbs", []))
    
    return {
        "bullet": bullet,
        "has_action_verb": has_action_verb,
        "weak_phrases_detected": weak_found,
        "is_optimal": has_action_verb and not weak_found
    }
```

---

## Contributing

1. **Adding an Industry**:
   Ensure all new industries contain a minimum of 15 verified, high-frequency ATS keywords.
2. **Adding Action Verbs**:
   Use strong past-tense transitive verbs that convey concrete outcomes. Avoid weak/passive verbs (*assisted, helped, was responsible for*).
3. **Format**:
   Keep `rules.json` strictly formatted with 2-space indentation.

---

## License

MIT License. Free for commercial, personal, and educational ATS applications.

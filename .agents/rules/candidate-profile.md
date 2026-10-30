# Candidate Profile & Anti-Hallucination Rules
# Edit this file to establish your ground-truth career history, verified metrics, and application boundaries.
# The AI agent MUST consult this file before generating any resume, cover letter, or application text.

---

## 1. ANTI-HALLUCINATION: NEVER INVENT NUMBERS OR FACTS (STRICT)

This is the single most important rule in the entire repository. Every metric, percentage, scale number, tool, and date written into a resume or cover letter must originate from:
1. `CV_Base.tex` (your master resume)
2. The **Verified Metrics Bank** in Section 2 below
3. Explicit confirmation provided by the user in conversation

**NEVER:**
- Invent hypothetical metrics (e.g., "increased throughput by 65%") without backing data.
- Invent team sizes, user counts, or client numbers you were not told.
- Add vague intensifiers like *"significantly"*, *"dramatically"*, *"substantially"* to disguise missing numbers — these are immediate red flags that you have no real data.
- If a metric is unknown, conservative qualitative impact is preferred, or ask the user:
  > *"Can you confirm approximately how many records/users/hours this affected? I want to make sure every metric on your resume is 100% interview-defensible."*

---

## 2. VERIFIED METRICS BANK (CUSTOMIZE THIS FOR YOUR FIELD)

Add your proven achievements here. When tailoring, the AI selects, reorders, and highlights from this bank:

### Example Data Engineering & Science Metrics:
- **Throughput / Volume**: Scaled distributed streaming pipeline to ingest **2.5TB+ to 3TB+ daily events** across microservices with 99.99% uptime.
- **Latency / Performance**: Reduced batch query/ETL latency by **45%** (from 4.5 hours to 2.5 hours) through partitioning, dbt model refactoring, and cluster tuning.
- **Cost Savings**: Optimized cloud data warehouse and compute spend, saving **£35,000 / $45,000 annually** in compute instances.
- **Data Quality**: Automated schema contract validation and anomaly monitoring, catching **98%** of upstream schema drifts before downstream warehouse ingestion.
- **Operational Scale**: Designed self-serve data models and automated refresh workflows, saving analytics teams **12+ hours per week**.
- **Leadership / Mentorship**: Mentored **4 junior engineers** on distributed data modeling, code review standards, and CI/CD best practices.

*(Replace or expand the above list with your own verified numbers!)*

---

## 3. EMPLOYMENT HISTORY (GROUND TRUTH — EXACT DATES ONLY)

List your exact titles, companies, and date boundaries so the AI never alters dates or creates gaps:

| Company | Official Internal Title | CV Presentation Title | Exact Dates | Key Focus Areas |
|---|---|---|---|---|
| **Tech Corp / Global Finance** | Analyst / Engineer | Senior Data Engineer | Mar 2023 – Present | Cloud ETL, PySpark, Airflow, Snowflake |
| **Data Solutions Ltd** | Junior Engineer | Data Engineer | Feb 2021 – Mar 2023 | SQL pipelines, dbt, PostgreSQL, Data modeling |

- **Gap Rules**: Ensure dates are continuous. If there is a legitimate career break or transition period, state how it should be presented (e.g., "completed MSc", "independent consulting").

---

## 4. EDUCATION & CERTIFICATIONS (EXACT DETAILS)

| Degree / Credential | Institution / Issuer | Exact Dates | Status / Grade |
|---|---|---|---|
| MSc Data Science / CS | University Name | Sep 2024 – Sep 2025 | Completed / Distinction |
| BSc Computer Science / Engineering | University Name | 2017 – 2021 | First Class Honours |
| Cloud Certification (AWS / GCP / Azure) | Cloud Provider | 2023 | Active |

- **Rule**: Never mark a completed degree as "in progress". State final status or expected date accurately.

---

## 5. VISA & WORK AUTHORISATION LANGUAGE

Define your exact status phrasing:
- **UK Applications**: Always write `Right to Work: Full UK work authorisation — no sponsorship required`.
- **US Applications**: Always write `Work Authorization: US Citizen / Permanent Resident (No sponsorship required)`.
- **Rule**: Never use phrasing that names specific temporary visa codes or implies future sponsorship hurdles unless explicitly requested. Keep it positive, direct, and candidate-centric.

---

## 6. CURRENCY RULES

- Always match the currency to the target job market:
  - **UK applications**: Always use **GBP (£)** (e.g., `£35,000 saved annually`).
  - **US applications**: Always use **USD ($)** (e.g., `$45,000 saved annually`).
  - **European applications**: Always use **EUR (€)**.
- Never use foreign currencies on domestic job applications.

---

## 7. BULLET POINT RULES — GOOGLE XYZ FORMULA

Every bullet point on the resume MUST strictly follow the Google XYZ formula:  
**Accomplished [X] as measured by [Y] by doing [Z]**

Checklist for every generated bullet:
- [ ] Starts with a strong, active power verb (*Architected, Spearheaded, Re-engineered, Scaled*).
- [ ] Contains at least one specific metric or number from the Verified Metrics Bank.
- [ ] Shows clear business outcome/result, not just passive duties.
- [ ] Maximum 2 lines per bullet.
- [ ] Strictly bans passive filler: *"responsible for"*, *"helped with"*, *"assisted"*, *"participated in"*.

---

## 8. JOB TITLES ON CV

- If your company used generic internal banding (e.g., "Analyst", "Associate", "Member of Technical Staff"), present the functional industry title that accurately describes your actual responsibilities:
  - Default: `Senior Data Engineer`
  - When targeting platform roles: `Data Platform Engineer`
  - When targeting analytics roles: `Analytics Engineer / Data Engineer`

---

## 9. REAL TAILORING — NOT FIND-AND-REPLACE

True tailoring requires all 5 of the following actions:
1. **Summary Alignment**: Rewrite the professional summary to mirror the exact job title and top 3 core requirements from the JD.
2. **Skills Reordering**: Reorder `CORE SKILLS` categories and rows so that technologies emphasized in the JD appear first.
3. **Bullet Prioritization**: Move the most JD-relevant bullets to the TOP of each job section.
4. **Natural Keyword Integration**: Weave exact technical phrases from the JD into existing bullets without altering factual history.
5. **Availability & Location**: Match the candidate's availability and location line to the job format (e.g. hybrid / remote).

---

## 10. COVER LETTER GUIDELINES — SOUND HUMAN

When generating cover letters:
- **Target length**: 280–360 words across 3 to 4 concise paragraphs.
- **Avoid AI Clichés (Banned Phrases)**:
  - ❌ *"At the intersection of..."*
  - ❌ *"I thrive in fast-paced environments..."*
  - ❌ *"I would welcome the opportunity to discuss..."*
  - ❌ *"In today's data-driven world..."*
  - ❌ Rhetorical formulas like: *"[Big claim] demands more than X — it demands Y"*
  - ❌ Chained em-dashes (`---`) in prose.
- **Do**:
  - Open directly: *"I came across this role on [platform] and wanted to apply."*
  - Reference 1 or 2 specific, researched company initiatives.
  - Sign off naturally (e.g., `Kind regards` in the UK/EU, `Sincerely` in the US).

---

## 11. JOB FEASIBILITY & DEALBREAKER CRITERIA

Define requirements that should trigger an automatic **SKIP** in `Resume_Tracker.md` instead of wasting time tailoring a non-viable CV:

| Requirement Filter | Candidate Status | Action if Strictly Required in JD |
|---|---|---|
| **Security Clearance (SC / DV / Top Secret)** | Ineligible (requires 5+ years residency or citizenship) | **SKIP** (Log reason in Tracker) |
| **Foreign Languages** | English (Fluent) only | **SKIP** if role requires non-English language |
| **Regional Driving Licence** | Does not hold one | **SKIP** if role requires car/travel |

---

## 12. PERSONAL DETAILS & PREFERENCES

- **Name**: Alex Taylor
- **Location**: London, UK
- **Phone**: +44 7123 456789
- **Email**: alex.taylor@example.com
- **LinkedIn**: linkedin.com/in/alex-taylor-de
- **GitHub**: github.com/alextaylor-data
- **Driving Licence**: No
- **Open to Relocation**: London and nationally
- **Open to Hybrid / Remote**: Fully flexible

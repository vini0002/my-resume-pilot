---
name: onboarding-wizard
description: Interactively onboard a new user into AI Resume Pilot. Ingests raw resume text/files, interviews for ground-truth metrics, and automatically configures config.yaml, CV_Base.tex, and candidate-profile.md.
---

# Onboarding Wizard

## When to Use This Skill
Activate this skill whenever the user:
- Asks to "set up", "initialize", "configure", or "onboard" the repository.
- Pastes an existing CV, resume, or LinkedIn text to start.
- Asks: "How do I make this repo mine?" or "Set this up for my friend/me".
- Provides a master resume file to convert into LaTeX.

---

## Onboarding Protocol

### Step 1: Intake & Resume Analysis
Examine the user's input. If they provided a resume (pasted text, markdown, or file path):
1. Extract:
   - Full Name
   - Target Role / Discipline (e.g. Senior Data Engineer, Machine Learning Engineer, Backend Developer)
   - Contact Info: Email, phone, location, LinkedIn, GitHub/Portfolio
   - Work Experience: Companies, titles, exact dates, key accomplishments
   - Education & Certifications
   - Technical Stack & Core Competencies

If any critical information is missing, proceed to Step 2 to ask. If they haven't provided a resume yet, ask them to paste their existing resume text or drop their CV file in the workspace.

---

### Step 2: The Calibration Interview (Ask in 1 Clear Message)
Present a concise, structured interview asking only for what wasn't in their resume:

1. **Target Role & Field**:
   > *"What specific titles are you targeting? (e.g. Senior Data Engineer, Big Data Architect, Data Scientist)"*
2. **Work Authorization & Availability**:
   > *"What is your work authorization status and availability? (e.g. 'Full UK work authorisation — no sponsorship required', 'US Citizen', 'Available immediately') and what is your location preference (e.g., London hybrid or remote)?"*
3. **Overleaf Sync**:
   > *"Would you like automatic push to an Overleaf project for instant cloud PDF compilation? If yes, provide your Overleaf project Git URL or we can set it up later."*
4. **Verified Metrics Discovery (Anti-Hallucination Moat)**:
   > *"To ensure your tailored resumes never hallucinate numbers you can't defend in interviews, what are 3 to 5 real metrics from your past projects? (e.g., data volumes processed like '3TB/day', pipeline runtime cuts like 'reduced batch by 40%', money saved, team size, uptime)"*
5. **Hard Dealbreakers & Constraints**:
   > *"Are there any roles we should automatically SKIP? (e.g. roles strictly requiring UK Security Clearance, foreign languages you don't speak, or regional driving licences)?"*

---

### Step 3: Automated File Generation
Once the user confirms or provides their details, execute the following file updates:

#### 1. Update `config.yaml`
Write candidate metadata, role title, naming conventions, and Overleaf settings.

#### 2. Generate Master `CV_Base.tex`
Translate their work experience into the ATS-optimized LaTeX layout:
- Geometry: `[margin=0.75in]{geometry}`
- Font: `helvet` (clean modern sans-serif)
- Single-column, readable by all ATS engines (Workday, Greenhouse, Lever, Taleo)
- Sections:
  1. Header with Name, Title, and clickable links (`mailto`, `linkedin`, `github`, `portfolio`)
  2. `PROFESSIONAL SUMMARY` (tailored to their target discipline)
  3. `CORE SKILLS` (clean 2-column `tabularx` grouping their stack)
  4. `PROFESSIONAL EXPERIENCE` (companies, titles, dates, with bullets adhering strictly to Google's XYZ formula: *Accomplished [X] as measured by [Y] by doing [Z]*)
  5. `KEY ACHIEVEMENTS` (top 4-5 bullet highlights with verified metrics)
  6. `EDUCATION & CERTIFICATIONS`
  7. `AVAILABILITY & WORK AUTHORISATION`

#### 3. Update `.agents/rules/candidate-profile.md`
Record their exact dates, verified metrics bank, visa phrasing, and dealbreaker rules. This locks in the anti-hallucination moat so all future tailored resumes remain 100% accurate.

#### 4. Initialize `Resume_Tracker.md`
Set the initial baseline row pointing to their new `CV_Base.tex`.

---

### Step 4: Verification & Readiness Hand-off
1. Confirm all 3 files (`config.yaml`, `CV_Base.tex`, `.agents/rules/candidate-profile.md`) are successfully generated.
2. Provide a single clean wrap-up message:
   - Summary of the profile configured (Candidate name, target title, verified stack).
   - Instructions on how to drop their first JD into `JD/` and trigger tailoring with *"new JD"*.


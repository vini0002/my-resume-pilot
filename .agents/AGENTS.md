# AI Resume Pilot System Instructions

This repository contains an autonomous resume tailoring and career management engine. As an AI assistant, you operate in two primary modes:

1. **Onboarding / Setup Mode** (triggered when configuring a new candidate profile or when the user says "setup", "init", "configure", or pastes their master resume).
2. **Resume Tailoring Mode** (triggered when the user mentions a "new JD", "new CV", or adds a job description to `JD/`).

---

## Mode 1: Automated Onboarding & Setup Workflow

When a user asks to set up, initialize, or adapt this repository for themselves (or their friend), or pastes an existing resume:

1. **Invoke the `onboarding-wizard` Skill**: Follow the guidelines in `.agents/skills/onboarding-wizard/SKILL.md`.
2. **Intake Resume Data**:
   - Extract candidate identity, target field/roles (e.g. Data Engineering, Data Science, Software Engineering, Product), contact information, employment history, and technical stack.
3. **Conduct Calibration Interview (in 1 structured message)**:
   - Ask for any missing contact links (LinkedIn, GitHub/portfolio).
   - Ask for work authorization status, availability, and location preference.
   - Ask if they want **Overleaf integration** (ask for their Overleaf Git URL if they want instant cloud PDF compilation).
   - Ask for **3 to 5 verified metrics** from past roles (throughput, runtime reduction, cost saved, team scale) to establish the **anti-hallucination ground truth**.
   - Ask for any **dealbreaker constraints** (e.g., clearance restrictions, driving requirements, language constraints).
4. **Generate the Core Files**:
   - Write `config.yaml` with candidate details and settings.
   - Generate master `CV_Base.tex` using the ATS-optimized, single-column LaTeX architecture and Google XYZ bullet formatting.
   - Write `.agents/rules/candidate-profile.md` containing their ground-truth dates, verified metrics bank, and feasibility checks.
   - Reset `Resume_Tracker.md` with the new baseline row.
5. **Confirmation**:
   - Confirm setup completion and inform the user they can now drop job descriptions into `JD/` and say *"new JD"*.

---

## Mode 2: Automated Resume Tailoring Workflow

Whenever the user mentions they have added a "new JD", "new CV", or new job description:

1. **Identify the New JD**: Check the `JD/` directory for new job description files and cross-reference them with `Resume_Tracker.md` to identify untailored roles.
2. **Read the JD & Configuration**:
   - Read the job description file to understand the key skills, requirements, and keywords.
   - Read `config.yaml` for candidate metadata, naming conventions, and sync settings.
   - Read `.agents/rules/candidate-profile.md` for candidate-specific verified metrics, career boundaries, and feasibility checks (e.g., clearance, driving license, work authorization).
3. **Feasibility Pre-Check**:
   - If the role strictly requires qualifications, clearances, or licenses the candidate does not have (as defined in `candidate-profile.md`), mark as "Skipped" with reason in `Resume_Tracker.md` and state this in the 1-line response.
4. **Tailor the Resume**:
   - Use `CV_Base.tex` as the baseline.
   - Apply guidelines from `resume-tailor` and `resume-bullet-writer` skills (in `.agents/skills/`) to strategically reorder skills/bullets and rigorously enforce the Google XYZ formula (`Accomplished [X] as measured by [Y] by doing [Z]`) using **only verified metrics** from `candidate-profile.md`.
   - Create a new `.tex` file following the naming convention in `config.yaml` (e.g., `[cv_prefix]_[CompanyName].tex`).
5. **Chat Response**:
   - Respond with **ONLY 1 single line** stating whether the JD is suitable for the resume/profile and confirming the tailored file creation. Do **NOT** provide lengthy summaries, breakdowns, or conversational filler in the chat.
6. **Update the Tracker**:
   - Automatically update `Resume_Tracker.md` by appending a row for the newly created resume (Company name, JD file path, Tailored Resume file path, Status, Date).
7. **Sync to Overleaf (Optional)**:
   - If `overleaf_sync.enabled` is `true` in `config.yaml`, automatically copy the new `.tex` file into the designated sync folder, commit, and push via git. If disabled, skip this step without error.

---

## Strict Resume Rules & Constraints

- **NEVER Include JD Logistics/Schedule Details**: Under no circumstances should job-specific work patterns, client office locations, day counts, or commute notes (e.g., "(2 days/week) in Ashton", "3 days/week on-site", "travel 3x/month", "commutable to X") be written in any resume. The `AVAILABILITY & WORK AUTHORISATION` section (specifically `Location`) MUST strictly remain general and candidate-centric as established in `config.yaml` and `CV_Base.tex`.
- **Anti-Hallucination**: Never fabricate numbers, percentages, company names, or dates not documented in `candidate-profile.md` or `CV_Base.tex`.
- **One-Page ATS Architecture**: Keep layouts clean, single-column, with standardized LaTeX geometry (`[margin=0.75in]{geometry}`), `helvet` font, and standard sections (`PROFESSIONAL SUMMARY`, `CORE SKILLS`, `PROFESSIONAL EXPERIENCE`, `KEY ACHIEVEMENTS`, `EDUCATION`, `AVAILABILITY & WORK AUTHORISATION`).

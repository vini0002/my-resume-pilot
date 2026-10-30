# Adapting AI Resume Pilot for Any Field

AI Resume Pilot is built from the ground up to be **100% domain-agnostic**. The core skills—like Google's XYZ metric formula, ATS keyword optimization, cover letter generation, and cold email crafting—work across every industry.

---

## 3-Step Setup for Any Target Field

### Step 1: Update `config.yaml`
Set your personal name, target job title, location, and contact links:
```yaml
candidate:
  first_name: "Jordan"
  last_name: "Lee"
  title: "Senior Product Manager | Growth & B2B SaaS"
  email: "jordan.lee@example.com"
```

### Step 2: Establish Ground Truth in `.agents/rules/candidate-profile.md`
This is your **anti-hallucination moat**. Define:
1. **Verified Metrics**: Proven numbers you can defend in interviews (e.g. "Increased MRR by 35%", "Led team of 8").
2. **Employment History**: Accurate company names and start/end dates.
3. **Education**: Degrees and certifications.
4. **Feasibility Filters**: Things you cannot do (e.g. roles requiring security clearance, specific driving licenses, or languages you do not speak).

### Step 3: Populate `CV_Base.tex`
Take the template in `CV_Base.tex` (or start from one of the pre-built samples in `examples/`):
- `examples/data-engineer/`: Apache Spark, Kafka, SQL, Python, Cloud ETL, Data Warehousing.
- `examples/software-engineer/`: Full-stack & backend engineering, distributed systems, APIs.
- `examples/sharepoint-m365/`: Microsoft 365, SharePoint Online, Power Platform.

---

## Working with Non-Technical Roles
If applying for non-technical fields (e.g., Marketing, Sales, Operations, Healthcare, Education):
- Replace the `CORE SKILLS` table categories in `CV_Base.tex` with your discipline's terminology.
- Use `resume-bullet-writer` to frame achievements around **revenue generated, efficiency gained, volume handled, or client satisfaction**.
- The ATS optimizer and Cover Letter generator will automatically mirror the exact industry jargon found in each incoming job description.


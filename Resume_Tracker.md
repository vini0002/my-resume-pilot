# Resume Tracker

This tracker links incoming Job Descriptions (JDs) in the `JD/` directory to their custom-tailored LaTeX resumes.
Whenever a new JD is added or updated, the automated pipeline updates this table.

| Company / Role | Job Description File | Tailored Resume File | Status | Last Updated |
|---|---|---|---|---|
| **Base CV** | N/A | `CV_Base.tex` | ✅ Master Baseline | YYYY-MM-DD |

---

### Instructions for Generating New Resumes
1. Drop the Job Description file (e.g., `.txt`, `.rtf`, `.md`, or `.pdf`) into the `JD/` directory.
2. Tell your AI agent: *"I've added a new JD for [Company Name]"*.
3. The AI reads the requirements, tailors the summary, reorders skills and bullets using verified metrics, creates the `.tex` file, and updates this tracker automatically!


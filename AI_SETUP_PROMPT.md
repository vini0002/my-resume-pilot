# 🤖 1-Click AI Setup Prompt

> **How to use**: Copy and paste the prompt below into **any AI assistant** (Google Antigravity, Claude, ChatGPT, Cursor, GitHub Copilot) along with your current resume text or PDF. The AI will interview you, configure all files, and have your automated resume tailor ready in 60 seconds!

---

```markdown
Hello AI! I want to set up this `ai-resume-pilot` repository for my personal job search.

Please read `.agents/AGENTS.md` and activate the `onboarding-wizard` skill (.agents/skills/onboarding-wizard/SKILL.md) to initialize the project for me.

Here is my current resume / background:
---
[PASTE YOUR RESUME TEXT OR LINKEDIN SUMMARY HERE]
---

Please do the following:
1. Review my background and target role (e.g. Data Engineer, Data Scientist, Software Engineer, Product Manager, etc.).
2. Ask me a single structured set of questions for anything you still need, specifically:
   - Any missing contact info, portfolio/GitHub, or LinkedIn links.
   - My work authorization status, availability, and location preference.
   - Whether I want Overleaf integration for instant cloud PDF compilation (and my Overleaf Git URL if yes).
   - 3 to 5 real, interview-defensible metrics from my past projects (e.g. pipeline throughput, runtime cuts %, dollar savings, team size) so my tailored resumes have an anti-hallucination ground truth.
   - Any hard dealbreakers to automatically skip (e.g., security clearances I don't hold, foreign languages, driving licenses).
3. Once I reply, automatically generate and update:
   - `config.yaml`
   - `CV_Base.tex` (in ATS-friendly single-column LaTeX using the Google XYZ formula for bullets)
   - `.agents/rules/candidate-profile.md`
   - `Resume_Tracker.md`
4. Confirm when everything is ready so I can start dropping job descriptions into `JD/`!
```


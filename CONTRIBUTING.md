# Contributing to AI Resume Pilot

We welcome community contributions to make AI Resume Pilot more versatile, reliable, and accessible!

## How You Can Contribute

1. **New Domain Examples**:
   - Add new role templates to `examples/` (e.g., `examples/product-manager/`, `examples/data-analyst/`, `examples/devops-sre/`, `examples/ux-designer/`).
   - Include a sample `CV_Base_[Role].tex` and a corresponding `candidate-profile-[role].md`.

2. **Skill Enhancements**:
   - Expand instructions in `.agents/skills/` to support emerging ATS formats, new industry certifications, or interview prep frameworks.

3. **LaTeX Templates**:
   - Contribute new ATS-friendly LaTeX themes (e.g., modern minimal, two-column academic, executive format).

## Pull Request Guidelines

- Ensure LaTeX templates compile cleanly with standard `pdflatex` or `latexmk`.
- Keep templates single-page friendly and strictly ATS compliant (avoid floating boxes, tables inside headers, or untagged symbols).
- Never commit private personal data, active phone numbers, or authentication tokens.
- Follow the MIT License terms.


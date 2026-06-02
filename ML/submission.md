# Prompt: Prepare Machine Learning Homework Submission

Use this prompt when preparing a final `submission/` folder after lab code, figures, notebooks, or reports have been created.

## Purpose

Create a minimal, unambiguous submission package that matches the assignment handout. Avoid submitting process artifacts unless the assignment explicitly asks for them.

## Inputs to Read

- Top-level homework handout, such as `HW*.pdf`, `Homework*.pdf`, `hw*.pdf`, or assignment instructions.
- Lab PDFs or Markdown statements.
- Starter scripts and completed scripts.
- Generated figures, data files, result files, reports, and notebooks.
- Original lab zip files, if available, for starter-script comparison.

## Workflow

1. Read the top-level homework handout first and list the required deliverables.
2. Separate deliverables into categories: report, Python scripts, data files, figures, notebooks, and optional notes.
3. If the handout contains explicit report questions, ensure the final report answers those questions directly. Do not replace them with a generic lab summary.
4. If runnable `.py` files are required, sync completed TODO implementations into `script_lab*.py`.
5. Preserve starter-script imports, function signatures, helper functions, main execution flow, output filenames, and dependency restrictions.
6. If the user wants a blank starter copy for self-practice, copy the original file first, such as `script_lab9_starter.py`, and leave TODO blocks unchanged there.
7. If original zips or starter files are available, compare completed scripts against them and confirm edits are limited to student info plus TODO implementation regions.
8. Run scripts from inside the intended submission folders and confirm expected figures or output files are produced.
9. Create or update `submission/` with only core required files.
10. Remove duplicate or confusing files from `submission/`, such as stale PDFs, old reports, notebooks, rebuild scripts, converted `Lab*.md`, `issues.md`, or `README.md`, unless requested.

## Core Submission Checks

- There is exactly one final report PDF unless the handout asks for more.
- The report title, name, student ID, date, and page limit match the assignment.
- The report answers every explicit report question in the handout.
- Completed `.py` files contain student info and no placeholder implementation.
- Required data files are included, such as `.mat` files used by scripts.
- Generated figures or result files are included when the starter script produces them.
- Scripts run from their own folder using relative paths.
- The final package contains no ambiguous old report, assignment handout mistaken as an answer, or process-only artifact.

## Optional Files

Include these only when the assignment or user asks for them:

- Converted `Lab*.md` statements.
- Notebook solutions.
- Rebuild scripts.
- `README.md`.
- `issues.md`.
- LaTeX source, if only PDF is required.

## Environment Notes

If `matplotlib` fails because Python imports an incompatible user-site NumPy, try running with:

```powershell
$env:PYTHONNOUSERSITE='1'
```

Record the workaround only if it affects reproducibility; do not include environment notes in the final package unless useful or requested.

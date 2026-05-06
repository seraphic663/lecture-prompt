# Prompt: Write a Machine Learning Homework Report

Use this prompt when writing a homework-level LaTeX report that summarizes multiple lab folders in one homework directory.

## Purpose

Find the homework LaTeX template, preserve the original template, and create `report.tex` in the homework directory beside the lab folders.

Do not directly modify starter scripts unless the user explicitly requests script edits. Starter scripts such as `script_lab*.py` are read-only by default.

## Inputs to Read

- Homework directory containing one or more lab folders.
- Lab PDFs or markdown instructions inside each lab folder.
- Starter scripts, notebook solutions, simple lab reports, result files, and generated figures inside each lab folder.
- A LaTeX template located somewhere inside the homework directory, such as `Homework-Template/.../main.tex`.
- Previous homework reports, if available, to match style.

## Workflow

1. Inspect the homework directory and identify lab folders.
2. Search within the homework directory for the LaTeX template. Prefer a file named `main.tex` under a template-like directory.
3. Do not modify the template original.
4. Read each lab's assignment statement first, then read its starter script, notebook solution, report, and result files when present.
5. Prefer notebook solutions as the implementation reference when they exist.
6. Create `report.tex` in the homework directory, at the same level as the lab folders.
7. Keep the template preamble, page limit, title/author format, and basic structure when a template is available.
8. Write concise English sections for each lab, focused on objectives, formulas, implementation choices, and verified results.
9. Compile LaTeX if the local environment allows it. If compilation is unavailable, complete source-level checks.

## Report Content

For each lab, include:

- The lab objective and required tasks.
- Key formulas or algorithms.
- Important matrix or tensor shapes.
- Implementation choices and numerical-stability notes when relevant.
- Actual results or generated figures when available.
- A brief interpretation of the results.

For missing outputs, state what could not be verified instead of inventing numbers.

## Output

Create or update:

- `<HOMEWORK_DIR>/report.tex`

Optional outputs:

- `<HOMEWORK_DIR>/issues.md` if blockers or uncertainties affect the report.

## Error Reporting

If you run into missing templates, unreadable PDFs, missing lab outputs, failed LaTeX compilation, missing dependencies, permission issues, or any other blocker, continue with a reasonable fallback when possible.

Create or update a short issue report named `issues.md` in the homework directory:

```md
# Issues

- Context: <file, problem, slide, lab, command, or task>
  Problem: <what went wrong>
  Impact: <what part of the report may be incomplete or uncertain>
  Fallback: <what you did to continue>
  Needs user: <yes/no; what input is needed if yes>
```

Do not stop solely because one lab is incomplete. Stop only when the missing information makes the whole report unreliable.

## Checklist

- `report.tex` exists in the homework directory, beside the lab folders.
- The template original was not modified.
- The starter scripts were not directly modified unless explicitly requested.
- Each lab has a concise section.
- Actual results are quoted only when available.
- Missing or unverified outputs are clearly marked.
- LaTeX compiles if the local environment allows it; otherwise source-level checks were completed.

## Avoid

- Do not create `report.tex` inside a single lab folder for a homework-level report.
- Do not modify template originals.
- Do not edit starter scripts by default.
- Do not paste full code.
- Do not invent numeric results.

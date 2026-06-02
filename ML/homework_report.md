# Prompt: Write a Machine Learning Homework Report

Use this prompt when writing a homework-level LaTeX report. A homework report may summarize labs, answer explicit tech-report questions, or solve theory questions. Always identify the required report type from the top-level homework handout before writing.

## Purpose

Find the homework requirements and LaTeX template, preserve the original template, and create `report.tex` in the homework directory. The report must answer the actual homework handout, not merely summarize available lab folders.

Do not directly modify starter scripts unless the user explicitly requests script edits. Starter scripts such as `script_lab*.py` are read-only by default.

## Inputs to Read

- Homework directory containing one or more lab folders.
- Top-level homework handout, such as `HW*.pdf`, `Homework*.pdf`, `hw*.pdf`, or assignment instructions.
- Lab PDFs or markdown instructions inside each lab folder.
- Starter scripts, notebook solutions, simple lab reports, result files, and generated figures inside each lab folder.
- A LaTeX template located somewhere inside the homework directory, such as `Homework-Template/.../main.tex`.
- Previous homework reports, if available, to match style.

## Workflow

1. Inspect the homework directory and identify top-level handouts, lab folders, and templates.
2. Read the top-level homework handout before writing. Extract report questions, point values, page limit, due date, and required deliverables.
3. Search within the homework directory for the LaTeX template. Prefer a file named `main.tex` under a template-like directory.
4. Do not modify the template original.
5. If the handout asks explicit tech-report or theory questions, answer those questions directly.
6. If the handout asks for a lab summary, read each lab's statement, starter script, notebook solution, report, and result files when present.
7. Prefer verified completed code or notebook solutions as implementation references when lab discussion is required.
8. Create `report.tex` in the homework directory, at the same level as the lab folders.
9. Keep the template preamble, page limit, title/author format, and basic structure when a template is available.
10. Write concise English sections focused on the requested questions, formulas, derivations, implementation choices, and verified results.
11. Compile LaTeX if the local environment allows it. If compilation is unavailable, complete source-level checks.

## Report Content

If the handout asks explicit report questions:

- Answer each question in the same order as the handout.
- Include derivations, formulas, algorithm updates, and assumptions requested by the question.
- Do not replace these answers with a generic lab-method summary.

If the handout asks for lab summaries, for each lab include:

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
- The top-level homework handout was read.
- The report answers the explicit handout questions, if any.
- The template original was not modified.
- The starter scripts were not directly modified unless explicitly requested.
- Each lab has a concise section.
- Actual results are quoted only when available.
- Missing or unverified outputs are clearly marked.
- LaTeX compiles if the local environment allows it; otherwise source-level checks were completed.

## Avoid

- Do not create `report.tex` inside a single lab folder for a homework-level report.
- Do not assume the report is a lab summary when the handout asks tech-report or theory questions.
- Do not modify template originals.
- Do not edit starter scripts by default.
- Do not paste full code.
- Do not invent numeric results.

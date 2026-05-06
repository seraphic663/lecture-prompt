# Prompt: Write a Simple Machine Learning Lab Report

Use this prompt when writing a concise Markdown report for a machine-learning lab. This is an auxiliary workflow; for lab solution creation, read `ipynb_solution.md` first unless the user explicitly requests a report-only task.

## Purpose

Create a short `report.md` that summarizes the lab tasks, core formulas, implementation approach, and available results. The report should be readable as a compact explanation of what the solution does.

Do not directly modify the starter script unless the user explicitly requests script edits. Starter scripts such as `script_lab*.py` are read-only by default.

## Inputs to Read

- `<LAB_DIR>/<LAB_PDF_NAME>.pdf`: lab statement.
- `<LAB_DIR>/<SCRIPT_NAME>.py`: starter script or implementation script.
- Notebook solution files, if present.
- `<LAB_DIR>/result.txt`: experiment numbers, if present.
- Generated figures, if present.

## Workflow

1. Inspect the lab directory and verify exact file names.
2. Read the lab PDF and list the required tasks.
3. Read the starter script and identify required functions, signatures, shapes, formulas, and testing flow.
4. If a notebook solution exists, read it as the primary implementation reference.
5. Read `result.txt` or generated outputs when present. If outputs are missing, do not invent numbers.
6. Write a concise Markdown report in English.

## Report Content

For each task, include:

- The implementation objective.
- The key formula or algorithm.
- Important matrix or tensor shapes.
- A short note about numerical stability or implementation choices when relevant.

For experiments, include:

- Actual numeric results if available.
- A brief interpretation of the results.
- A note when expected outputs are missing or could not be verified.

## Output

Create or update:

- `<LAB_DIR>/report.md`

## Error Reporting

If you run into missing files, unreadable content, OCR uncertainty, unavailable outputs, failed commands, missing dependencies, or any other blocker, continue with a reasonable fallback when possible.

Create or update a short issue report named `issues.md` in the lab directory:

```md
# Issues

- Context: <file, problem, slide, cell, command, or task>
  Problem: <what went wrong>
  Impact: <what part of the report may be incomplete or uncertain>
  Fallback: <what you did to continue>
  Needs user: <yes/no; what input is needed if yes>
```

## Checklist

- `report.md` exists in the lab directory.
- The starter script was not directly modified unless explicitly requested.
- Required tasks are summarized.
- Key formulas and shapes are included.
- Actual results are quoted only when available.
- Missing or unverified outputs are clearly marked.

## Avoid

- Do not write a long LaTeX-style report.
- Do not paste full code.
- Do not add large tables.
- Do not over-explain basic concepts.
- Do not invent results.

# Prompt: Build a Machine Learning Notebook Solution

Use this when creating or rebuilding a notebook solution for a machine-learning lab or homework.

## Inputs to Read

- Assignment PDF or markdown instructions.
- Starter script, if present.
- Existing notebook or rebuild script, if present.
- Result files and generated figures, if present.

## Workflow

1. Read the assignment statement and list required tasks/functions.
2. Read the starter script and preserve function names, signatures, return values, and required testing flow.
3. Do not add forbidden dependencies.
4. Choose the requested solution mode. The user may not use the exact labels; infer the intended mode from wording:
   - Concise Mode: for users with some foundation, exam review, quick completion, or submission-focused work. Use shorter markdown, essential formulas, core shape notes, and executable correctness.
   - Detailed Mode: for zero-foundation or beginner-friendly explanations. Add background notes, definitions, shape reasoning, and step-by-step derivations before code.
   - If no mode is specified or the request is ambiguous, generate both a concise/submission version and a detailed/teaching version.
5. Organize cells in the same order as the lab tasks.
6. Put short markdown before code cells explaining the objective, formula, shapes, and expected output according to the selected mode.
7. End with a full testing cell that reproduces the starter script outputs.
8. Run all cells if possible; otherwise validate extracted code with a script or syntax check.

## Output

Produce one or more of the following, depending on the requested mode:

- Single requested Concise Mode: `<LAB_DIR>/<lab>_solution.ipynb` and, if useful, `<LAB_DIR>/rebuild_<lab>_solution.py`.
- Single requested Detailed Mode: `<LAB_DIR>/<lab>_solution.ipynb` and, if useful, `<LAB_DIR>/rebuild_<lab>_solution.py`.
- No clear mode or both requested: `<LAB_DIR>/<lab>_solution_concise.ipynb`, `<LAB_DIR>/<lab>_solution_detailed.ipynb`, and matching rebuild scripts if used.
- Updated result files or figures, if requested.

If a rebuild script exists, prefer updating it so the notebook can be regenerated.

## Error Reporting

If you run into missing files, unreadable content, OCR uncertainty, failed commands, missing dependencies, permission issues, or any other blocker, first try to continue with a reasonable fallback and complete as much of the requested output as possible.

Create or update a short issue report named `issues.md` in the working/output directory. Keep it concise and actionable:

```md
# Issues

- Context: <file, problem, slide, cell, command, or task>
  Problem: <what went wrong>
  Impact: <what part of the output may be incomplete or uncertain>
  Fallback: <what you did to continue>
  Needs user: <yes/no; what input is needed if yes>
```

Do not stop solely because one item is unclear. Stop only when the task cannot be completed safely or the missing information makes the whole output unreliable.

## Checklist

- All required functions are present.
- Function signatures match the starter script.
- The notebook can run top to bottom.
- Random seeds are fixed when needed.
- No local absolute paths are required.
- Figures and printed metrics are produced when expected.












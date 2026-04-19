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
4. Choose notebook style:
   - Teaching notebook: more explanation and shape notes.
   - Submission notebook: shorter explanations and executable correctness.
5. Organize cells in the same order as the lab tasks.
6. Put short markdown before code cells explaining the objective, formula, shapes, and expected output.
7. End with a full testing cell that reproduces the starter script outputs.
8. Run all cells if possible; otherwise validate extracted code with a script or syntax check.

## Output

Produce one or more of:

- `<LAB_DIR>/<lab>_teaching_notebook.ipynb`
- `<LAB_DIR>/rebuild_<lab>_teaching_notebook.py`
- Updated result files or figures, if requested

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



# Prompt: Build a Machine Learning Notebook Solution

Use this prompt when creating or rebuilding a notebook solution for a machine-learning lab or homework. This is the default workflow for lab tasks unless the user explicitly asks for a report-only workflow.

## Purpose

Create one or more `.ipynb` solution files from the lab statement and starter script. The notebook should contain complete executable implementation code and clear mathematical or algorithmic explanations.

Do not directly modify the starter script unless the user explicitly requests script edits. Starter scripts such as `script_lab*.py` are read-only by default. The notebook may include complete implementations of the required functions, but the original script file should remain unchanged.

Notebook explanations should be written mainly in Chinese, while keeping important technical terms in English when they are standard course vocabulary, such as Kernel PCA, Lasso, ISTA, K-NN graph, Laplacian Eigenmaps, covariance, eigenvalue, and bandwidth. Code identifiers, file names, function names, and required output names should remain unchanged.

## Inputs to Read

- Assignment PDF or markdown instructions.
- Starter script, if present.
- Existing notebook or rebuild script, if present.
- Result files, generated figures, or previous outputs, if present.

## Workflow

1. Inspect the lab directory and verify exact file names.
2. Read the assignment statement and list the required tasks, functions, outputs, and dependency restrictions.
3. Read the starter script and preserve function names, signatures, return values, imports, dependency limits, and required testing flow.
4. Treat the starter script as read-only unless the user explicitly asks for direct script modification.
5. Choose the requested solution mode. The user may not use the exact labels; infer the intended mode from wording:
   - Concise Mode: for users with some foundation, review, quick completion, or submission-focused work. Use short markdown, essential formulas, core shape notes, and executable correctness.
   - Detailed Mode: for beginner-friendly or teaching-focused work. Add background notes, definitions, shape reasoning, algorithmic intuition, and step-by-step derivations before code.
   - If no mode is specified or the request is ambiguous, generate both a concise/submission version and a detailed/teaching version.
6. Organize notebook cells in the same order as the lab tasks.
7. Before each main code cell, add Chinese markdown explaining the objective, key formula, important shapes, and expected behavior. Keep important technical terms in English where appropriate.
8. Implement the required functions inside the notebook while matching the starter script signatures and testing flow.
9. End with a full testing cell that reproduces the starter script's intended execution path and saves expected figures or outputs.
10. Run all cells if possible. If notebook execution is unavailable, validate the extracted code with a script or syntax check.

## Output

Produce one or more of the following depending on the requested mode:

- Single requested Concise Mode: `<LAB_DIR>/<lab>_solution.ipynb` and, if useful, `<LAB_DIR>/rebuild_<lab>_solution.py`.
- Single requested Detailed Mode: `<LAB_DIR>/<lab>_solution.ipynb` and, if useful, `<LAB_DIR>/rebuild_<lab>_solution.py`.
- No clear mode or both requested: `<LAB_DIR>/<lab>_solution_concise.ipynb`, `<LAB_DIR>/<lab>_solution_detailed.ipynb`, and matching rebuild scripts if useful.
- Generated figures or result files when the notebook is expected to produce them.

If a rebuild script already exists, prefer updating it so the notebook can be regenerated. If no rebuild script exists, create one only when it materially improves reproducibility or verification.

## Error Reporting

If you run into missing files, unreadable content, OCR uncertainty, failed commands, missing dependencies, permission issues, unavailable Jupyter execution, or any other blocker, first try to continue with a reasonable fallback and complete as much of the requested output as possible.

Create or update a short issue report named `issues.md` in the working or output directory:

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

- The starter script was not directly modified unless explicitly requested.
- All required functions are present in the notebook.
- Function signatures match the starter script.
- Dependency restrictions are respected.
- The notebook can run top to bottom, or extracted code passes a syntax/source check.
- Random seeds are fixed when deterministic output is expected.
- No local absolute paths are required inside the notebook.
- Figures and printed metrics are produced when expected.
- Markdown includes both code-level and mathematical explanations.
- Markdown explanations are mainly Chinese, with important technical terms kept in English.

## Avoid

- Do not edit starter scripts by default.
- Do not add dependencies forbidden by the starter script or assignment.
- Do not omit the testing flow from the notebook.
- Do not provide code without explaining the relevant formulas and shapes.
- Do not invent numeric outputs.

# ML Prompt Pack

Reusable prompts for machine-learning coursework workflows. These prompts are intended for an AI assistant that can read local files, create notebooks, write concise reports, run verification commands, and summarize issues.

## Default Priority

For a machine-learning lab, read and follow `ipynb_solution.md` first unless the user explicitly asks for a report-only workflow. The primary default deliverable is a notebook solution generated from the lab PDF and starter script.

Do not directly modify starter scripts such as `script_lab*.py` unless the user explicitly asks for script edits. Starter scripts are read-only by default. A generated notebook may contain complete implementation code copied or adapted from the starter script structure, but the original starter file should remain unchanged.

## Files

- `ipynb_solution.md`: Build one or two notebook solutions from a lab PDF and starter script, with executable code and mathematical explanation.
- `lab_report.md`: Write a simple Markdown lab report from the lab statement, starter script or notebook, and available results.
- `homework_report.md`: Write a homework-level LaTeX report by finding a template in the homework directory and creating `report.tex` beside the lab folders.

## General Rules

1. Read the assignment PDF or instructions first; do not infer requirements only from code.
2. Read starter scripts to identify required functions, signatures, return values, constraints, and testing flow.
3. Preserve starter function signatures, expected file names, and dependency restrictions in generated solutions.
4. Treat starter scripts as read-only unless the user explicitly requests direct script modification.
5. Use actual numeric outputs from `result.txt`, generated notebook runs, or generated scripts; do not invent results.
6. Keep explanations focused, formula-driven, and tied to the implementation.
7. Do not modify template originals; copy or use them only to create outputs in the requested working directory.
8. Verify outputs with source checks, notebook execution, Python syntax checks, or LaTeX compilation when the local environment allows it.

## Notebook Solution Modes

`ipynb_solution.md` supports two modes:

- Concise Mode: for users with some foundation or submission-focused work. Use short markdown, essential formulas, core shape notes, and executable correctness.
- Detailed Mode: for beginner-friendly or teaching-focused work. Include background definitions, shape reasoning, derivations, and step-by-step algorithm explanations before code.

If the user clearly asks for one mode, generate a single solution notebook. If no mode is specified, generate both concise and detailed notebooks.

## Typical Deliverables

- Notebook solution files such as `<lab>_solution.ipynb`, `<lab>_solution_concise.ipynb`, or `<lab>_solution_detailed.ipynb`.
- Optional rebuild scripts when useful for reproducibility.
- Generated figures and numeric outputs when the notebook or report requires them.
- `report.md` for a simple lab report when requested.
- `report.tex` for a homework-level LaTeX report when requested.
- `issues.md` when a blocker or uncertainty affects the output.

## Error Reporting

When a prompt encounters missing files, failed runs, missing dependencies, unavailable TeX or Jupyter environments, unclear requirements, or OCR uncertainty, continue with a reasonable fallback when possible and write a concise `issues.md` in the working or output directory.

# ML Prompt Pack

Reusable prompts for machine-learning coursework workflows. These prompts are intended for an AI assistant that can read local files, create notebooks, write concise reports, run verification commands, and summarize issues.

## Default Priority

For a homework directory, first look for a top-level homework handout such as `HW*.pdf`, `Homework*.pdf`, `hw*.pdf`, or an assignment PDF outside individual lab folders. Read it before writing reports or preparing submissions. Do not assume a homework report should summarize labs; the handout may instead ask explicit theory or tech-report questions.

For a machine-learning lab, read and follow `ipynb_solution.md` first unless the user explicitly asks for a report-only workflow. If the lab PDF has not already been converted to Markdown, use `pdf2md.md` first to create `Lab*.md` beside `Lab*.pdf`, then use the PDF/Markdown statement and starter script to build the notebook solution.

Do not directly modify starter scripts such as `script_lab*.py` unless the user explicitly asks for script edits. Starter scripts are read-only by default. A generated notebook may contain complete implementation code copied or adapted from the starter script structure, but the original starter file should remain unchanged.

For final Python-programming submissions, it is acceptable to copy the completed TODO implementations back into `script_lab*.py` when the assignment or user asks for runnable `.py` files. Preserve imports, function signatures, helper functions, main execution flow, and output filenames. If the user wants to keep a blank starter for self-practice, copy the original script first, for example as `script_lab*_starter.py`, and leave its TODO blocks unchanged.

## Files

- `pdf2md.md`: Convert `Lab*.pdf` assignment statements into clean `Lab*.md` files beside the PDFs.
- `ipynb_solution.md`: Build one or two notebook solutions from a lab PDF and starter script, with executable code and mathematical explanation.
- `lab_report.md`: Write a simple Markdown lab report from the lab statement, starter script or notebook, and available results.
- `homework_report.md`: Write a homework-level LaTeX report by finding a template in the homework directory and creating `report.tex` beside the lab folders.
- `submission.md`: Prepare a minimal final submission folder after code, figures, and reports are complete.

## General Rules

1. Read the assignment PDF or Markdown statement first; do not infer requirements only from code.
2. For homework directories, read the top-level homework handout before individual lab files.
3. When a `Lab*.pdf` exists but no matching `Lab*.md` exists, create `Lab*.md` with `pdf2md.md` before building notebooks or reports.
4. Read starter scripts to identify required functions, signatures, return values, constraints, and testing flow.
5. Preserve starter function signatures, expected file names, and dependency restrictions in generated solutions.
6. Treat starter scripts as read-only during notebook/report creation unless the user explicitly requests direct script modification.
7. For final `.py` submission, update only student info and TODO implementation regions; verify against original zip/starter files when available.
8. Use actual numeric outputs from `result.txt`, generated notebook runs, or generated scripts; do not invent results.
9. Keep explanations focused, formula-driven, and tied to the implementation.
10. Do not modify template originals; copy or use them only to create outputs in the requested working directory.
11. Verify outputs with source checks, notebook execution, Python syntax checks, or LaTeX compilation when the local environment allows it.

## Notebook Solution Modes

`ipynb_solution.md` supports two modes:

- Concise Mode: for users with some foundation or submission-focused work. Use short markdown, essential formulas, core shape notes, and executable correctness.
- Detailed Mode: for beginner-friendly or teaching-focused work. Include background definitions, shape reasoning, derivations, and step-by-step algorithm explanations before code.

If the user clearly asks for one mode, generate a single solution notebook. If no mode is specified, generate both concise and detailed notebooks.

## Typical Deliverables

- Notebook solution files such as `<lab>_solution.ipynb`, `<lab>_solution_concise.ipynb`, or `<lab>_solution_detailed.ipynb`.
- Markdown lab statements such as `Lab5.md` or `Lab6.md`, generated from `Lab5.pdf` or `Lab6.pdf`.
- Optional rebuild scripts when useful for reproducibility.
- Generated figures and numeric outputs when the notebook or report requires them.
- `report.md` for a simple lab report when requested.
- `report.tex` for a homework-level LaTeX report when requested.
- A minimal `submission/` folder with only required final files when requested.
- `issues.md` when a blocker or uncertainty affects the output.

Working artifacts such as converted `Lab*.md`, notebooks, rebuild scripts, `issues.md`, and `README.md` should not be included in the final submission by default unless the assignment or user requests them.

## Error Reporting

When a prompt encounters missing files, failed runs, missing dependencies, unavailable TeX or Jupyter environments, unclear requirements, or OCR uncertainty, continue with a reasonable fallback when possible and write a concise `issues.md` in the working or output directory.

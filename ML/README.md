# ML Prompt Pack

Reusable prompts for machine-learning coursework workflows. They are intended for an AI assistant that can read local files, edit code, run scripts, inspect outputs, and write reports or notebooks.

## Files

- `lab_report.md`: Write a concise LaTeX lab report from a lab script, lab PDF, result files, tuning files, and a template.
- `homework_report.md`: Placeholder for a root-level homework technical report prompt.
- `ipynb_solution.md`: Build or rebuild a notebook solution from an assignment statement and starter script.

## General Rules

1. Read the assignment PDF or instructions first; do not infer requirements only from code.
2. Preserve starter function signatures and required file names.
3. Use actual numeric outputs from `result.txt`, `tuning_result.txt`, or generated runs; do not invent results.
4. Keep reports short, English, formula-focused, and result-driven unless the prompt or user asks otherwise.
5. Save full tuning tables to `tuning_result.txt` and summarize only the key settings in reports.
6. Do not modify template originals; copy them into the working lab/homework folder.
7. Verify outputs with source checks and compile LaTeX or run notebooks when the local environment allows it.

## Notebook Solution Modes

`ipynb_solution.md` supports two modes:

- Concise Mode: for users with some foundation or submission-focused work. It uses shorter markdown, essential formulas, core shape notes, and executable correctness.
- Detailed Mode: for zero-foundation or beginner-friendly explanations. It includes background notes, definitions, shape reasoning, and step-by-step derivations before code.

If the user clearly asks for one mode, generate a single solution notebook. If no mode is specified, generate both concise and detailed notebooks.

## Typical Deliverables

- Completed `.py` script or notebook.
- `result.txt` for baseline numeric outputs.
- `tuning_result.txt` if tuning is requested.
- `report.tex` or a root-level homework report.
- Optional README/manifest for submission packaging.

## Error Reporting

When a prompt encounters missing files, failed runs, missing dependencies, unavailable TeX/Jupyter environments, or unclear requirements, it should continue with reasonable fallback checks when possible and write a concise `issues.md` in the working/output directory.

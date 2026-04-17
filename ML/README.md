# ML Prompt Pack

Reusable prompts for machine-learning coursework workflows. They are intended for an AI assistant that can read local files, edit code, run scripts, inspect outputs, and write reports.

## Files

- `lab_report.md`: Write a concise LaTeX lab report from a lab script, lab PDF, result files, tuning files, and a template.
- `homework_report.md`: Write a root-level homework technical report from a homework PDF plus related lab or lecture files.
- `ipynb_solution.md`: Build or rebuild a notebook solution from an assignment statement and starter script.

## General Rules

1. Read the assignment PDF first; do not infer requirements only from code.
2. Preserve starter function signatures and required file names.
3. Use actual numeric outputs from `result.txt` or generated runs; do not invent results.
4. Keep reports short, English, formula-focused, and result-driven.
5. Save full tuning tables to `tuning_result.txt` and summarize only the key settings in reports.
6. Do not modify template originals; copy them into the working lab/homework folder.
7. Verify outputs with source checks and compile LaTeX when the local TeX environment works.

## Typical Deliverables

- Completed `.py` script or notebook.
- `result.txt` for baseline numeric outputs.
- `tuning_result.txt` if tuning is requested.
- `report.tex` or a root-level homework report.
- Optional README/manifest for submission packaging.

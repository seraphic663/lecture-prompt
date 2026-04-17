# Prompt: Write a Machine Learning Lab Report

Use this when writing a concise report for a machine-learning lab.

## Inputs to Read

- `<LAB_DIR>/<SCRIPT_NAME>.py`: main implementation.
- `<LAB_DIR>/<LAB_PDF_NAME>.pdf`: lab statement.
- `<LAB_DIR>/result.txt`: experiment numbers, if present.
- `<LAB_DIR>/tuning_result.txt`: tuning results, if present.
- `<TEMPLATE_DIR>/main.tex`: LaTeX template.
- A previous lab report, if available, to match style.

## Workflow

1. Inspect the lab directory and verify exact file names.
2. Read the lab PDF and list the required tasks.
3. Read the script and identify implemented functions, shapes, formulas, and numerical-stability choices.
4. Read `result.txt` and `tuning_result.txt`. If outputs are missing and the script can run, run it to generate them.
5. Copy the template `main.tex` to `<LAB_DIR>/report.tex`; do not modify the template original.
6. Keep the template preamble, page limit, title/author format, and basic structure.
7. Write the report in English and keep it short enough for the page limit.

## Report Content

For each task, include:

- What was implemented.
- The key formula or objective.
- Important matrix/tensor shapes.
- A short derivation for closed forms, gradients, coordinate updates, alternating steps, or multiplicative updates.
- Important implementation choices and numerical-stability handling.

For experiments:

- Quote actual numbers from `result.txt`.
- Explain what matches expectation and what is surprising.
- If a metric is misleading, explain why briefly.

For tuning, if `tuning_result.txt` exists:

- State tuned parameters, candidate counts, total grid size, baseline setting, best setting, and best metric.
- Mention runtime if recorded.
- Add: `Full tables are saved in tuning_result.txt.`
- If test metrics are used for tuning, note that a strict pipeline should use validation data.

## Checklist

- `report.tex` exists in the lab directory.
- Template original was not modified.
- No placeholders remain: `Question XX`, `Student Name`, `XXXX`, `Date of Submission`.
- The report cites real result numbers.
- Tuning is summarized when available.
- LaTeX compiles if the local environment allows it; otherwise say source-level checks were completed.

## Avoid

- Do not paste full code.
- Do not add large tables.
- Do not over-explain basic concepts.
- Do not claim a finite-grid best setting is theoretically optimal.

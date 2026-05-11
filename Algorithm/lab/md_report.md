# Prompt: Write a Machine Learning Homework Technical Report

Use this when a homework PDF asks for a short technical report that may depend on lab PDFs, lecture PDFs, scripts, or previous lab reports.

## Inputs to Read

- `<ROOT>/<HOMEWORK_PDF>.pdf`: homework requirements.
- Related lab PDFs and lab scripts.
- Related lecture PDFs when the homework references equation numbers.
- Existing result/tuning files when the report should mention experiments.
- The course LaTeX template, if provided.

## Workflow

1. Read the homework PDF first and list every required deliverable.
2. Separate programming deliverables from written technical questions.
3. Resolve all references. If the homework says to derive from equation `(23)` to `(25)`, locate those equations in the lecture PDF instead of guessing.
4. Create the report from the template if one is used. Preserve the preamble and page-limit guard.
5. Keep programming summaries brief; spend most space on the required technical questions.
6. If packaging is requested, include reports, scripts, result files, and tuning files; exclude lecture PDFs, notebooks, caches, logs, and unused generated figures.

## How to Write Technical Answers

For derivations:

- Restate the source equation.
- Define variables and shapes.
- Substitute the model or representation.
- Simplify step by step.
- End at the requested target equation.

For chain-rule questions:

- Identify the path, such as `h -> K(h) -> L`.
- Write the matrix chain rule.
- Derive the elementwise derivative.
- Combine them into the requested gradient.

For algorithm-design questions:

- State the proposed objective or regularizer.
- Explain why it gives the desired property.
- Provide a practical algorithm and update rule.
- State the stopping criterion and final selected output.

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

- Every question in the homework PDF is answered.
- Referenced equation numbers match the actual PDF.
- No template placeholders remain.
- Required scripts/reports/results are present if submission includes programming.
- The final package has a short README or manifest if requested.
## Lab Implementation Style

When the lab asks for an algorithm or data-structure implementation, prefer the minimal version needed to demonstrate the textbook method.

- Implement the required algorithm directly; do not add broad engineering frameworks, generic libraries, benchmarking harnesses, or packaging code unless the task asks for them.
- A small demonstration case is enough. Avoid long performance experiments unless the lab explicitly requires comparison or timing.
- Keep the code clear and plain. Prefer simple control flow, ordinary structs/classes, and readable helper functions over overly abstract or complex designs.
- Avoid unnecessary maintenance-only fields, validation layers, ownership frameworks, logging, and statistics counters that do not help explain the algorithm.
- Add short Chinese comments at key textbook steps, such as partition, link, consolidate, cut, or dynamic-programming transition. Do not comment every line.
- Reports should remain complete and useful: explain the implementation idea, key operations, complexity, compile command, and sample output. The minimal-implementation rule applies to code, not to removing necessary explanation from reports.



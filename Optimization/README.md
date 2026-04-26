# Optimization Prompt Pack

Reusable prompts for optimization-course workflows. They are intended for an AI assistant that can inspect local files, convert PDFs into LaTeX, read lecture materials, and write separate solution files.

## Files

- `pdf2tex.md`: Convert an optimization homework PDF into a clean LaTeX source file.
- `tex_solution.md`: Write one or more separate solution LaTeX files from a homework LaTeX source file.

## Homework Workflow

1. Use `pdf2tex.md` to convert the original homework PDF into `<root>.tex`.
2. Review the reconstructed LaTeX source and fix OCR or notation issues if needed.
3. Use `tex_solution.md` to generate separate solution LaTeX files from the reconstructed homework source.

Do not write answers into the original homework `.tex` file.

## Solution Modes

`tex_solution.md` supports two solution modes:

- Concise Mode: for students with some foundation. It focuses on key derivations, simplex tables, corner-point evaluations, and final answers with minimal background.
- Detailed Mode: for zero-foundation or beginner-friendly explanations. It explains relevant optimization concepts, reformulations, tableau steps, and method choices before giving answers.

The user may not use the exact mode labels. Infer intent from wording such as `简洁`, `关键步骤`, `复习版`, `详细`, `零基础`, or `讲背景`.

If the user clearly asks for one mode, generate only the matching file:

```text
<root>_solution_concise.tex
or
<root>_solution_detailed.tex
```

If the user does not specify a mode, generate both:

```text
<root>_solution_concise.tex
<root>_solution_detailed.tex
```

## Optimization-Specific Expectations

For graphical LP problems, identify constraint boundaries, corner points, feasibility, adjacency, and objective values when required.

For simplex, Big M, and two-phase problems, show standard-form conversion, variable introductions, tableau transitions, pivot choices, and stopping conditions explicitly.

For reformulation problems, show the exact substitution or equivalent transformation before solving.

## Error Reporting

When a prompt encounters missing files, unreadable formulas, OCR uncertainty, failed commands, missing dependencies, unavailable LaTeX environments, or unclear requirements, it should continue with reasonable fallback checks when possible and write a concise `issues.md` in the working/output directory.

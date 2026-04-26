# Prompt: Convert an Optimization Homework PDF to LaTeX

You are given an optimization-course homework PDF. Your task is to reconstruct it as a clean, compilable LaTeX source file.

Do not solve any problem.
Do not modify the original PDF.

## Input

- A homework PDF file, such as `hw2.pdf`, `2.pdf`, or `homework_03.pdf`.
- Optional extracted text, OCR output, or a previous converted `.tex` file that indicates the desired reconstruction style.
- Optional lecture notes or nearby course files if they help disambiguate notation, but do not use them to rewrite the homework content.

## Output File Naming

Create one LaTeX source file for the homework statement.

Use the homework root name as the output file name:

```text
<root>.tex
```

Examples:

- `hw2.pdf` -> `hw2.tex`
- `2.pdf` -> `2.tex`

Do not name the output file after this prompt file.

## Writing Goal

Rebuild the PDF as if it were a human-written LaTeX source file, not raw OCR output.

Preserve the original mathematical meaning, numbering, wording, and problem hierarchy, while normalizing line breaks, spacing, punctuation, and mathematical notation into clean LaTeX.

Prefer semantic LaTeX structure over visual imitation of the PDF layout.

## Workflow

1. Read the PDF carefully and identify the title, due date, problem numbering, subproblem structure, and all mathematical models.
2. Remove page numbers, OCR fragments, broken line wraps, and other PDF artifacts.
3. Reconstruct the prose into normal sentences and paragraphs.
4. Rebuild optimization models in proper LaTeX math environments.
5. Keep the result minimal, clean, and directly compilable.
6. If part of the PDF is unclear, mark the uncertainty in `issues.md` and use the least speculative reconstruction possible.

## Required Structure

Use a clean source structure similar to:

```tex
\documentclass{article}
\usepackage[a4paper,margin=1.6cm]{geometry}
\usepackage{amsmath}

\begin{document}

\textbf{Homework 2}

\textbf{Due Date:} 4 p.m., April 27 (Mon)

\begin{enumerate}
\item ...
\end{enumerate}

\end{document}
```

Adjust the title text, due date text, and content according to the actual PDF.

## Formatting Rules

- Use `\documentclass{article}`.
- Use `\usepackage[a4paper,margin=1.6cm]{geometry}`.
- Use `\usepackage{amsmath}`.
- Keep the preamble minimal unless the PDF clearly requires more packages.
- Put the homework label or title in bold.
- Put the due date on its own line if the PDF presents it separately.
- Use `enumerate` for the main problem list.
- Use nested `enumerate` for subproblems such as `(a)`, `(b)`, `(c)`.
- Typeset optimization models in display math with `aligned` whenever the PDF presents an objective and multiple constraints.
- Write the objective and constraints in a consistent form such as:

```tex
\[
\begin{aligned}
\max \quad & Z = \cdots \\
\text{s.t.} \quad & \cdots \\
& \cdots
\end{aligned}
\]
```

- Put each functional constraint on its own aligned row.
- Use proper subscripts such as `x_1`, `x_2`, and `x_j`.
- Use math mode for variables, inequalities, quantified index ranges, and short mathematical phrases.
- Keep short prose sentences outside math mode unless they are inherently mathematical statements.
- If a short prose sentence follows a displayed model, keep it as normal text. Example: `no lower bound constraint for $x_1$.`

## Rules

- Do not solve the homework.
- Do not modify the original PDF.
- Do not preserve PDF line breaks mechanically.
- Do not keep OCR noise such as split tokens, missing spaces, broken punctuation, or malformed symbols.
- Do not rewrite the exercises in your own style beyond light normalization needed for reconstruction.
- Do not add unnecessary macros, theorem environments, or packages.
- Do not invent missing text. If something is unreadable or ambiguous, report it in `issues.md`.
- Preserve the original problem order and subproblem order.

## Style Constraints

- Write the reconstructed `.tex` file in the same language as the source PDF unless the user asks otherwise.
- Keep the source plain and maintainable.
- Prefer standard LaTeX over clever shorthand.
- The final result should look like plausible original course source, not an OCR transcript.
- The file should compile directly in a standard LaTeX environment when the source content is complete.

## Error Reporting

If you run into missing files, unreadable content, OCR uncertainty, failed commands, missing dependencies, permission issues, or any other blocker, first try to continue with a reasonable fallback and complete as much of the requested output as possible.

Create or update a short issue report named `issues.md` in the working/output directory. Keep it concise and actionable:

```md
# Issues

- Context: <file, page, problem, formula, command, or task>
  Problem: <what went wrong>
  Impact: <what part of the output may be incomplete or uncertain>
  Fallback: <what you did to continue>
  Needs user: <yes/no; what input is needed if yes>
```

Do not stop solely because one symbol or sentence is unclear. Stop only when the task cannot be completed safely or the missing information makes the whole output unreliable.

## Important

The goal is to reconstruct the original homework statement as clean LaTeX, not to produce notes or solutions.

The original PDF remains the source of truth. The new `<root>.tex` file is a reconstructed source version of the homework statement only.

# Prompt: Write Optimization Homework Solutions from a LaTeX File

You are given an optimization homework LaTeX file that contains problem statements. Your task is to write a separate complete solution LaTeX file for the homework.

Do not modify the original homework `.tex` file.

## Input

- A homework LaTeX file, such as `2.tex`, `hw2.tex`, or `homework_03.tex`.
- Optional previous solution files to learn the desired explanation style.
- Optional lecture slides, notes, textbook excerpts, screenshots, or PDFs.

## Output File Naming

The output depends on the requested solution mode.

If the user clearly requests one mode, create exactly one solution file:

```text
<root>_solution_concise.tex
or
<root>_solution_detailed.tex
```

Examples:

- If the homework file is `2.tex` and the user asks for concise solutions, write `2_solution_concise.tex`.
- If the homework file is `hw2.tex` and the user asks for detailed solutions, write `hw2_solution_detailed.tex`.

If the user does not specify a mode clearly, create both versions:

```text
<root>_solution_concise.tex
<root>_solution_detailed.tex
```

Do not name any output file after this prompt file.

## Solution Modes

The user may not use the exact labels below. Infer the intended mode from meaning, tone, and wording.

### Concise Mode

Use this mode when the user asks for a concise, compact, exam-review, answer-focused, or "I already know the basics" version.

Audience: students with some foundation who mainly need the key setup, essential derivations, simplex tables, and final answers.

Write with these constraints:

- Keep explanations short and focused on the required derivation.
- Show essential formulas, pivots, tables, corner-point evaluations, and final answers.
- Skip broad background knowledge unless it is directly needed to avoid a mistake.
- Prefer compact tables, aligned derivations, and short boxed conclusions.
- Do not include long conceptual introductions.

### Detailed Mode

Use this mode when the user asks for a detailed, beginner-friendly, zero-foundation, step-by-step, explanatory, or background-heavy version.

Audience: students who may not know the prerequisite concepts and need the reasoning built from basics.

Write with these constraints:

- Explain the relevant optimization concept before using it.
- Define important terms such as feasible region, corner-point feasible solution, basic feasible solution, slack variable, artificial variable, pivot column, pivot row, and reduced cost when needed.
- Show each algebraic or tableau step and explain why it is valid.
- Introduce the purpose of methods such as graphical analysis, simplex, Big M, and two-phase before applying them.
- Still avoid irrelevant textbook exposition that does not help solve the current problem.

### Mode Selection Rule

- If the user clearly requests Concise Mode, generate only the concise version.
- If the user clearly requests Detailed Mode, generate only the detailed version.
- If the user does not specify a mode, or the request is ambiguous, generate both versions using the two-file naming scheme above.
- If the user asks for both, generate both versions.

## Writing Goal

Write a complete, careful, and self-contained solution for every problem in the homework LaTeX file, following the selected solution mode.

The solution should be mathematically correct, easy to study from, and faithful to the problem order and notation of the source file.

When nearby solution files exist, follow their style for language, structure, notation, and level of detail.

## Required Structure

Use a clean LaTeX article structure. The solution file should reproduce each original problem statement before its solution.

A typical structure is:

```tex
\documentclass{article}
\usepackage[a4paper,margin=1.6cm]{geometry}
\usepackage{amsmath,amssymb}

\begin{document}

\textbf{Homework 2 Solutions}

\begin{enumerate}
\item
<original problem statement>

\textbf{Solution.}

...
\end{enumerate}

\end{document}
```

You may add minimal packages needed for mathematical formatting, tables, or simple figures, but keep the preamble restrained.

## Rules

- Do not edit the original problem file.
- Copy the full problem statement for each problem from the source homework file before writing its solution.
- Do not skip any problem or subproblem.
- Keep the same problem order and subproblem order as the original homework.
- If a statement is ambiguous, state the assumption you are using before solving.
- Preserve the original notation unless there is a compelling reason to introduce auxiliary notation, and define any new notation clearly.
- Keep all mathematical claims justified.
- When a problem asks for a step-by-step method, actually show the steps rather than jumping directly to the final answer.
- If a problem asks for a tableau or tabular simplex derivation, include the tableau sequence explicitly.
- If a problem asks for graphical analysis, identify the relevant corner points, feasible or infeasible status, objective values when needed, and final conclusion.
- If a problem involves unrestricted-sign variables or reformulation, show the substitution clearly.

## Optimization-Specific Guidance

### Graphical LP Problems

When solving graphical linear-programming problems:

- State the constraint boundaries explicitly.
- Identify all relevant intersection points.
- Distinguish feasible corner points from infeasible ones when the problem asks for all corner-point solutions.
- Compute objective values for all required corner-point feasible solutions.
- State adjacency relations and shared boundaries when asked.

### Simplex and Tableau Problems

When solving simplex problems:

- Show the standard-form conversion when needed.
- Introduce slack, surplus, and artificial variables explicitly.
- State the initial basic feasible solution or explain how it is obtained.
- For each iteration, identify the entering variable, leaving variable, pivot position, and updated tableau.
- State the stopping condition and final optimal solution clearly.

### Big M and Two-Phase Problems

When solving Big M or two-phase problems:

- Explain why artificial variables are needed.
- Write the modified objective or Phase I objective explicitly.
- Show the initial tableau and the transition between phases when using the two-phase method.
- Report infeasibility if artificial variables cannot be driven to zero.

### Reformulation Problems

When reformulating a model:

- State the original issue clearly, such as equality constraints, `\ge` constraints, negative right-hand sides, minimization, or variables without lower bounds.
- Show the exact substitution or transformation used.
- Present the final equivalent form cleanly before solving it.

## Style Constraints

- Write in the same language as the homework file unless the user asks otherwise.
- If the homework is in Chinese or bilingual Chinese-English, write the solution mainly in Chinese while preserving standard optimization terms in English where useful.
- Prefer concise but complete derivations.
- Avoid vague phrases such as "obvious" when a calculation, pivot, or feasibility check is needed.
- Keep notation and formatting consistent across all problems.
- The final file should be suitable for study notes, checking work, or submission reference.

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

Do not stop solely because one item is unclear. Stop only when the task cannot be completed safely or the missing information makes the whole output unreliable.

## Important

The goal is to produce a separate solution `.tex` file, not to overwrite or inject answers into the original homework source.

The original homework `.tex` file is the source of problem statements. The new solution file, such as `<root>_solution_concise.tex` or `<root>_solution_detailed.tex`, is the only file that should contain answers.

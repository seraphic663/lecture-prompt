# Prompt: Write Complete Solutions from a Homework Markdown File

You are given a Markdown homework file that contains algorithm problems. The file may use the following structure:

```md
## <problem-number>

<problem statement>

<enter you answer>
```

Your task is to write a separate complete solution Markdown file for the problems.

Do not modify the original homework Markdown file.

## Input

- A homework Markdown file, such as `5.md` or `6.md`.
- Optional reference materials, such as textbook excerpts, PDFs, screenshots, or lecture notes.
- Optional previous context about the desired writing style.

## Output File Naming

The output depends on the requested solution mode.

If the user clearly requests one mode, create exactly one solution file:

```text
<root>_solution.md
```

Examples:

- If the homework file is `5.md` and the user asks for concise solutions, write `5_solution.md`.
- If the homework file is `6.md` and the user asks for detailed solutions, write `6_solution.md`.

If the user does not specify a mode clearly, create both versions:

```text
<root>_solution_concise.md
<root>_solution_detailed.md
```

## Solution Modes

The user must indicate the desired mode, but they may not use the exact labels below. Infer the intended mode from meaning, tone, and wording.

### Concise Mode

Use this mode when the user asks for a concise, compact, quick, exam-review, answer-only, or "I already know the basics" version.

Audience: students with some foundation who mainly need the key idea, proof structure, recurrence, complexity, and final conclusion.

Write with these constraints:

- State the key observation directly.
- Give only the necessary algorithm/proof steps.
- Keep correctness arguments tight.
- Show the recurrence or complexity derivation without broad background explanation.
- Avoid long introductions to standard concepts.

### Detailed Mode

Use this mode when the user asks for a detailed, beginner-friendly, zero-foundation, step-by-step, explanatory, or background-heavy version.

Audience: students who may not know the prerequisite concepts and need the reasoning built from basics.

Write with these constraints:

- Explain the relevant algorithmic idea before using it.
- Define terms such as invariant, exchange argument, recurrence, DP state, greedy choice, reduction, and asymptotic bound when needed.
- Show why the algorithm is designed this way.
- Expand correctness proofs and runtime derivations step by step.
- Still avoid unrelated textbook exposition.

### Mode Selection Rule

- If the user clearly requests Concise Mode, generate only the concise version.
- If the user clearly requests Detailed Mode, generate only the detailed version.
- If the user does not specify a mode, or the request is ambiguous, generate both versions using the two-file naming scheme above.
- If the user asks for both, generate both versions.

## Writing Goal

Write a complete, careful, and self-contained solution for every problem, following the selected solution mode.

Start from the basic idea needed for the problem, but avoid unnecessary verbosity. The solution should be detailed enough for a student to understand the reasoning from scratch.

When reference material is provided, follow its style:

- State the key observation first.
- Then give the algorithm, recurrence, or construction.
- Then prove correctness or derive the bound.
- Finally state the running time or conclusion.

## Required Structure

Use this general structure:

```md
# <root> Homework Solutions

## <problem-number>

### Idea

...

### Algorithm / Proof / Analysis

...

### Conclusion

...
```

You may adjust section names when the problem type requires it, but keep the solution organized and easy to scan.

## Rules

- Do not edit the original problem file.
- Do not copy `<enter you answer>` into the solution file.
- Do not leave placeholders.
- Do not skip any problem.
- Keep problems in sorted problem-number order.
- For a problem number of the form `a.b-c`, sort by numeric `a`, then numeric `b`, then numeric `c`.
- For a problem number of the form `a.d`, place it after all `a.b-c` problems with the same leading `a`, but before any `(a+1).b-c` problems.
- Examples: `8.2-4` comes before `8.3-5`; `9.3-1` comes before `9-3`; all `9.x-y` problems come before `9-3`, and `9-3` comes before `10.x-y`.
- Do not invent missing problem statements. If a statement is ambiguous, say what assumption you are using.
- Use Markdown LaTeX for mathematical notation:
  - Prefer inline math `$...$` whenever possible, especially for variables, indices, intervals, asymptotic notation, and short formulas.
  - Display math: `$$...$$`
- Use clear asymptotic notation such as $O(\cdot)$, $\Omega(\cdot)$, and $\Theta(\cdot)$.
- When giving pseudocode, keep it concise and faithful to the algorithm.
- For recurrence proofs, show the recurrence and explain why it solves to the claimed bound.
- For correctness arguments, identify the invariant, counting argument, exchange argument, or reduction being used.
- Prefer precise reasoning over long prose.

## Style Constraints

- Write in the same language as the homework file unless the user asks otherwise.
- If the homework file is in Chinese, write the solution in Chinese.
- Avoid overly casual wording.
- Avoid unnecessary background unrelated to the problem.
- Keep the final answer suitable for submission or study notes.

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

## Important

The goal is to produce solutions, not to reformat the original problem set.

The original Markdown file is the source of problem statements. The new `<root>_solution.md` file is the only file that should contain answers.










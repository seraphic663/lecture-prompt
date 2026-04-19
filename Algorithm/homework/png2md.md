# Prompt: Convert Problem PNGs to Markdown

You are given a set of PNG images, each containing one algorithm homework problem. Your task is to transcribe and organize the problems into a single Markdown file.

Do not solve any problem.

## Input

- One or more PNG files.
- Each PNG file usually corresponds to one problem.
- File names may contain problem numbers, such as `8.2-4.png`, `9.3-1.png`, or `9-3.png`.

## Output File Naming

Create one Markdown file for the whole problem set.

Use the root homework number as the file name:

- If the directory or given root looks like `.\6xxx`, name the file `6.md`.
- If the root homework number is `5`, name the file `5.md`.
- In general, use `<root>.md`.

## Required Markdown Format

Follow this format exactly:

```md
## <problem-number>

<problem statement>

**Answer**

<enter you answer>
```

For example:

```md
## 8.2-4

Design an algorithm that preprocesses a given set of integers and answers a range-count query in constant time.

**Answer**

<enter you answer>
```

## Formatting Rules

- Use one second-level heading `##` for each problem.
- The heading must be the problem number, such as `8.2-4`, `8.3-5`, `9.3-1`, or `9-3`.
- Sort problems by problem number, not by raw file-name string.
- For a problem number of the form `a.b-c`, sort by numeric `a`, then numeric `b`, then numeric `c`.
- For a problem number of the form `a.d`, place it after all `a.b-c` problems with the same leading `a`, but before any `(a+1).b-c` problems.
- Examples: `8.2-4` comes before `8.3-5`; `9.3-1` comes before `9-3`; all `9.x-y` problems come before `9-3`, and `9-3` comes before `10.x-y`.
- Transcribe the problem statement accurately.
- Preserve mathematical notation using Markdown LaTeX:
  - Prefer `$...$` for inline math whenever possible, especially for variables, indices, intervals, asymptotic notation, and short formulas.
  - Use `$$...$$` for displayed equations.
- Preserve subproblem labels such as `a.`, `b.`, `c.`, and `d.`.
- If a problem contains a recurrence, equation, algorithm name, or asymptotic notation, keep it faithful to the image.
- If part of the image is unclear, mark it as `[unclear]` rather than guessing.
- Do not add explanations, hints, solutions, proofs, or comments.
- After every problem statement, copy the placeholder exactly:

```md
**Answer**

<enter you answer>
```

Do not fill in the placeholder.

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

## Important Constraints

- Do not solve the problems.
- Do not summarize the problems.
- Do not rewrite them in your own words unless needed for OCR cleanup.
- Do not remove any required mathematical details.
- Do not add any answer text after `<enter you answer>`.
- The final Markdown file should be ready for a student to fill in answers later.
- Report when you meet difficulties.



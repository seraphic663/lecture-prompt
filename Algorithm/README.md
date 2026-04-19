# Algorithm Prompt Pack

Reusable prompts for algorithm homework and lab workflows.

## Files

### Homework

- `homework/png2md.md`: Convert PNG screenshots of homework problems into a single Markdown problem file, such as `6.md`. It preserves problem numbers, math notation, subproblem labels, and answer placeholders. It must not solve the problems.
- `homework/md_solution.md`: Generate solution files from a homework Markdown file. It does not modify the original problem file.

### Lab

- `lab/md_report.md`: Write a concise algorithm lab report from lab instructions, code, outputs, and related materials.
- `lab/md_solution.md`: Placeholder for future lab-solution prompts.

## Homework Workflow

1. Use `homework/png2md.md` to transcribe screenshots such as `11.2-3.png` and `11-4.png` into `<root>.md`.
2. Review the generated problem statements and fix OCR mistakes if needed.
3. Use `homework/md_solution.md` to generate solution files.

## Solution Modes

`homework/md_solution.md` supports two solution modes:

- Concise Mode: for students with some foundation. It gives the key idea, algorithm/proof structure, recurrence or complexity, and final conclusion with minimal background.
- Detailed Mode: for zero-foundation or beginner-friendly explanations. It explains relevant concepts, proof methods, DP states, greedy choices, recurrences, reductions, and asymptotic bounds step by step.

If the user clearly asks for one mode, generate only one file named `<root>_solution.md`. If the user does not specify a mode, generate both:

```text
<root>_solution_concise.md
<root>_solution_detailed.md
```

## Error Reporting

When a prompt encounters missing files, unclear screenshots, OCR uncertainty, failed commands, or other blockers, it should keep working when possible and write a concise `issues.md` in the working/output directory.

## Notes

- Problem ordering follows the custom rule described in the prompts: `a.b-c` is sorted by numeric `a`, `b`, and `c`; `a.d` comes after all `a.b-c` with the same leading `a`, but before the next leading number.
- Use Markdown LaTeX: prefer `$...$` for inline math and `$$...$$` for displayed equations.
- Do not invent missing problem statements; mark unclear text as `[unclear]`.

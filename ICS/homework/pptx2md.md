# Prompt: Convert ICS Homework PPTX to Markdown

You are given an ICS homework PowerPoint file. Your task is to transcribe and organize the homework problems into a single Markdown file.

Do not solve any problem.

## Input

- One PPTX file, such as `homework5.pptx`.
- Optional previous homework Markdown files, such as `3.md`, `3_solution.md`, or earlier converted homework files.
- Optional extracted images from the PPTX, if slides store tables or figures as images.

## Output File Naming

Create one Markdown file for the homework problem set.

Use the root homework number as the file name:

- If the PPTX is named `homework5.pptx`, write `5.md`.
- If the directory or user instruction indicates homework number `6`, write `6.md`.
- In general, write `<root>.md`.

Do not name the output file after this prompt file.

## Required Markdown Format

Use this general format:

```md
# ICS II Homework <root>

## Problem 1

<problem statement>

**Answer**

<enter your answer>

## Problem 2

<problem statement>

**Answer**

<enter your answer>
```

If the local course style uses only `## Problem n` without a top-level title, follow the local style. Prefer consistency with nearby homework files in the same course directory.

## Workflow

1. Inspect the current directory and identify the target PPTX file.
2. Infer the homework number from the PPTX name, directory name, or user instruction.
3. Check nearby homework Markdown files to learn the expected style, especially heading level, answer placeholder, language, and table format.
4. Extract all visible slide content:
   - ordinary text,
   - problem statements,
   - code snippets,
   - tables,
   - formulas,
   - address bit diagrams,
   - memory dumps,
   - TLB, page table, cache, or register tables.
5. If a slide stores important content as an image, inspect the image and transcribe the meaningful content into Markdown. Do not replace required data with a bare image reference.
6. Preserve all problem numbers and subproblem labels.
7. Preserve blanks in tables that students are expected to fill.
8. Add the `**Answer**` placeholder after each problem unless the local file style clearly differs.
9. Do not include solution reasoning in the problem Markdown file.

## Formatting Rules

- Write in the same language as the original homework. For bilingual ICS slides, Chinese explanations with preserved English technical terms are acceptable.
- Preserve technical terms such as `virtual address`, `VPN`, `VPO`, `TLB`, `PTE`, `PDE`, `cache hit`, `page fault`, `segmentation`, `kernel mode`, and `user mode`.
- Use fenced code blocks for code and specify the language when clear:

````md
```c
int main(void) {
    return 0;
}
```
````

- Use Markdown tables for structured data whenever possible.
- Preserve hexadecimal numbers exactly and wrap them in backticks, such as `0x03FC`.
- Preserve units such as `KB`, `MB`, `B`, and bit ranges such as `VA[13:6]`.
- For address-format diagrams, either use a Markdown table or a compact text diagram.
- If a detail is genuinely unreadable after inspection, mark it as `[unclear]` rather than guessing.

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
- Do not summarize or simplify away required numerical data.
- Do not omit tables just because they came from images.
- Do not invent missing problem statements.
- Do not overwrite previous homework files unless the user explicitly asks.
- The final `<root>.md` file should be ready for the solution prompt to consume.

## Completion Checklist

Before finishing, verify that:

- The output file is named `<root>.md`.
- Every problem in the PPTX appears in the Markdown file.
- All important slide images have been transcribed when they contain problem data.
- Each problem has a clear `**Answer**` placeholder or follows the existing local style.
- No detailed solution text has been added.



# Prompt: Convert a Machine Learning Lab PDF to Markdown

Use this prompt when converting lab assignment PDFs such as `Lab5.pdf` or `Lab6.pdf` into readable Markdown files such as `Lab5.md` or `Lab6.md`.

## Purpose

Create a faithful Markdown version of the lab statement before building notebooks or reports. The Markdown file should make the task requirements easier to quote, inspect, and reuse in later workflows.

Do not modify the original PDF. Do not modify starter scripts. This workflow only creates or updates the Markdown transcription of the lab statement.

## Inputs to Read

- `<LAB_DIR>/Lab*.pdf`: lab assignment PDF.
- Existing `<LAB_DIR>/Lab*.md`, if present.
- Starter script only when needed to cross-check function names or task numbering; keep it read-only.

## Workflow

1. Inspect the lab directory and identify the exact `Lab*.pdf` file name.
2. Extract text from the PDF using the best available local tool, such as `pdftotext`, `pypdf`, or `pdfplumber`.
3. Preserve the task order, task numbering, equations, bullet lists, and important wording.
4. Convert the extracted statement into clean Markdown.
5. Keep mathematical formulas in LaTeX where possible:
   - Inline formulas: `$...$`
   - Display formulas: `$$...$$`
6. Use clear Markdown headings:
   - `# Lab N: <title>`
   - `## Motivation`
   - `## Tasks`
   - `### Task 1: ...`
7. If the PDF extraction loses equation formatting, reconstruct the formula carefully from the visible text or PDF context. Mark uncertain reconstructions in `issues.md`.
8. If figures or diagrams are important but cannot be extracted, add a short placeholder note such as `[Figure: <brief description>]`.
9. Save the Markdown file beside the PDF with the same base name:
   - `<LAB_DIR>/Lab5.pdf` -> `<LAB_DIR>/Lab5.md`
   - `<LAB_DIR>/Lab6.pdf` -> `<LAB_DIR>/Lab6.md`
10. After writing, read the Markdown file once and check that task requirements are complete and readable.

## Output

Create or update:

- `<LAB_DIR>/Lab*.md`

Optional output:

- `<LAB_DIR>/issues.md` if extraction, OCR, equation reconstruction, or figure handling is uncertain.

## Error Reporting

If you run into unreadable PDFs, failed extraction commands, OCR uncertainty, missing dependencies, permission issues, broken formulas, or unclear task text, continue with a reasonable fallback when possible.

Create or update a short issue report named `issues.md` in the lab directory:

```md
# Issues

- Context: <PDF page, formula, figure, command, or task>
  Problem: <what went wrong>
  Impact: <what part of Lab*.md may be incomplete or uncertain>
  Fallback: <what you did to continue>
  Needs user: <yes/no; what input is needed if yes>
```

Do not stop solely because one formula or figure is unclear. Stop only when the PDF cannot be read enough to recover the task requirements.

## Checklist

- `Lab*.md` exists beside `Lab*.pdf`.
- The original PDF was not modified.
- Starter scripts were not modified.
- Lab title, motivation, and tasks are preserved.
- Function names, required outputs, and dependency restrictions are preserved when present.
- Equations are readable as Markdown/LaTeX.
- Any uncertain extraction is documented in `issues.md`.

## Avoid

- Do not summarize away task requirements.
- Do not invent missing requirements.
- Do not turn the statement into a solution.
- Do not add implementation advice unless it is explicitly present in the PDF.
- Do not modify starter scripts or generated notebooks in this workflow.

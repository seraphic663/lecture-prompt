# Prompt Files README

This directory contains two reusable prompt files for preparing algorithm homework Markdown files.

## Files

- `png2md.md`: Use this prompt when the input is a set of PNG screenshots of homework problems. It instructs the AI to transcribe the problems into a single Markdown file, sort problem numbers correctly, preserve math notation, and leave `<enter you answer>` as an empty answer placeholder.
- `md_solution.md`: Use this prompt after the problem Markdown file already exists. It instructs the AI to write a separate solution file named `<root>_solution.md` without modifying the original problem file.

## Recommended Workflow

1. Use `png2md.md` to convert problem screenshots such as `11.2-3.png` and `11-4.png` into a homework file such as `6.md`.
2. Review the generated problem statements and fix any OCR mistakes if needed.
3. Use `md_solution.md` to generate the solution file, such as `6_solution.md`.

## Notes

- `png2md.md` is only for transcription. It must not solve problems.
- `md_solution.md` is only for solutions. It should write answers into a new solution file, not into the original homework file.
- Both prompts require Markdown LaTeX and encourage `$...$` for inline math.
- Problem ordering follows the custom rule described in the prompts: `a.b-c` is sorted by numeric `a`, `b`, and `c`; `a.d` comes after all `a.b-c` with the same leading `a`, but before the next leading number.
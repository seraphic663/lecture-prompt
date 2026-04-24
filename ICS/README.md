# ICS Prompt Pack

Reusable prompts for ICS / ICS II homework workflows.

## Files

### Homework

- `homework/pptx2md.md`: Convert an ICS homework PPTX, such as `homework5.pptx`, into a clean Markdown problem file such as `5.md`. It transcribes slide text, code, tables, figures, address-format diagrams, memory dumps, TLB/page-table/cache tables, and other problem data. It must not solve the problems.
- `homework/md_solution.md`: Generate solution files from an ICS homework Markdown file. It covers common ICS topics such as processes, signals, scheduling, virtual memory, TLB, page tables, cache, segmentation, and protection bits.

### Lab

- `lab/md_report.md`: Placeholder for future ICS lab-report prompts.
- `lab/md_solution.md`: Placeholder for future ICS lab-solution prompts.

## Homework Workflow

1. Use `homework/pptx2md.md` to convert `homework<root>.pptx` into `<root>.md`.
2. If the PPT contains question images that are hard to convert cleanly, save them into a dedicated image folder using `a.b.png` naming, where `a` is the problem number and `b` is the image index within that problem.
3. Review the generated problem Markdown, especially any content transcribed from images.
4. Ensure the end of `<root>.md` includes an extra section titled `利用原图的题目整理`, which reorganizes the problems using the saved source images as reference.
5. Use `homework/md_solution.md` to generate solution files from `<root>.md`.

## Solution Modes

`homework/md_solution.md` supports two solution modes:

- Concise Mode: for students with some foundation. It focuses on essential formulas, intermediate values, final answers, compact tables, and short derivations.
- Detailed Mode: for zero-foundation or beginner-friendly explanations. It explains relevant background concepts, terms, units, address fields, permission bits, and calculation steps before giving answers.

The user may not use the exact mode labels. Infer intent from wording such as "简洁", "关键步骤", "复习版", "详细", "零基础", "小白", or "讲背景".

If the user clearly asks for one mode, generate only one file named `<root>_solution.md`. If the user does not specify a mode, generate both:

```text
<root>_solution_concise.md
<root>_solution_detailed.md
```

## ICS-Specific Expectations

For address translation problems, show the bit split, indexes, tags, offsets, table-entry addresses, flags, hit/miss status, page faults, final physical addresses, and failure reasons.

For process or scheduling problems, track states, interleavings, timelines, response time, turnaround time, and completion time when relevant.

For segmentation and two-level page table problems, show bounds checks, growth direction, permission bits, mode checks, and the table entry that causes a failure.

## Error Reporting

When a prompt encounters missing files, unreadable slides, image/OCR uncertainty, failed commands, missing dependencies, or permission issues, it should keep working when possible and write a concise `issues.md` in the working/output directory.

# Prompt: Write ICS Homework Solutions from a Markdown File

You are given an ICS homework Markdown file that contains problem statements. Your task is to write a separate complete solution Markdown file for the homework.

Do not modify the original homework Markdown file.

## Input

- A homework Markdown file, such as `5.md` or `6.md`.
- Optional previous solution files, such as `3_solution.md`, to learn the desired explanation style.
- Optional reference materials, such as lecture slides, textbook excerpts, screenshots, or PDFs.

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

Do not name any output file after this prompt file.

## Solution Modes

The user must indicate the desired mode, but they may not use the exact labels below. Infer the intended mode from meaning, tone, and wording.

### Concise Mode

Use this mode when the user asks for a concise, compact, quick, exam-review, answer-only, or "I already know the basics" version.

Audience: students with some foundation who mainly need the key reasoning and final answers.

Write with these constraints:

- Keep explanations short and focused on the necessary derivation.
- Skip broad background knowledge unless it is directly needed to avoid a mistake.
- Show essential formulas, intermediate values, and final answers.
- Prefer tables and compact calculation blocks.
- Do not include long conceptual introductions.

### Detailed Mode

Use this mode when the user asks for a detailed, beginner-friendly, zero-foundation, step-by-step, explanatory, or background-heavy version.

Audience: students who may not know the prerequisite concepts and need the reasoning built from basics.

Write with these constraints:

- Explain the relevant background concept before using it.
- Define important terms, symbols, and units when they first appear.
- Show each calculation step and why it is valid.
- Use small examples, diagrams, or tables when they clarify the reasoning.
- Still avoid irrelevant textbook exposition that does not help solve the current problem.

### Mode Selection Rule

- If the user clearly requests Concise Mode, generate only the concise version.
- If the user clearly requests Detailed Mode, generate only the detailed version.
- If the user does not specify a mode, or the request is ambiguous, generate both versions using the two-file naming scheme above.
- If the user asks for both, generate both versions.

## Writing Goal

Write a complete, careful, and self-contained solution for every problem in the homework Markdown file, following the selected solution mode.

The solution should be detailed enough for a student to understand the reasoning from scratch, but it should stay focused on the actual problem. Prefer precise calculations and clear tables over long generic explanations.

When nearby solution files exist, follow their style for language, heading structure, answer tables, and level of detail.

## Required Structure

Use this general structure:

```md
# ICS II Homework <root> - Solution

## Problem 1

### 题目理解 / Idea

...

### 计算过程 / Analysis

...

### Answer

...
```

You may adjust section names when the problem type requires it. Keep the solution organized and easy to scan.

## Rules

- Do not edit the original problem file.
- Do not copy `<enter your answer>` or other placeholders into the solution file.
- Do not leave unsolved placeholders.
- Do not skip any problem or subproblem.
- Keep problem order the same as the original homework file unless the user asks otherwise.
- If a statement is ambiguous, state the assumption you are using before solving.
- Write in the same language as the homework file unless the user asks otherwise.
- If the homework is in Chinese or bilingual Chinese-English, write the solution mainly in Chinese while preserving technical terms in English.
- Use Markdown tables for final tabular answers.
- Use fenced code blocks for code and text-form calculations.
- Use backticks for registers, flags, addresses, filenames, and short code identifiers.

## ICS-Specific Guidance

### Process, Signals, and Scheduling

When solving process or scheduling problems:

- Track parent and child process state separately after `fork()`.
- Explain signal handlers, `waitpid`, and possible interleavings when relevant.
- For scheduling, list arrival time, service time, first response time, finish time, turnaround time, and response time when needed.
- Show the schedule timeline or an equivalent ordered execution list.

### Virtual Address Translation, TLB, Page Tables, and Cache

When solving address translation problems, explicitly compute:

- address bit width,
- page offset bits,
- `VPN`, `VPO`, `PPN`, and `PPO`,
- TLB tag and TLB index,
- TLB hit or miss,
- page table lookup and page fault status,
- physical address construction,
- cache tag, cache index, and byte/block offset,
- cache hit or miss,
- returned byte if the cache hits.

Do not skip intermediate fields even when the final answer is short.

### Multi-Level Page Tables

When solving multi-level page table problems, show:

```text
page offset bits = log2(page size)
VPN bits = virtual address bits - page offset bits
entries per page table page = page size / PTE size
index bits per level = log2(entries per page table page)
levels = ceil(VPN bits / index bits per level)
```

Explain any unused index capacity in the top level if the bits do not divide evenly.

### Segmentation

When solving segmentation problems, show:

- how the segment selector is extracted from the high VA bits,
- how the offset is computed,
- the segment's base, size, and growth direction,
- bounds checking, usually `0 <= offset < size`,
- `base + offset` for positive growth,
- `base - offset` for negative growth,
- which program objects live in code, data, heap, or stack.

### Two-Level Page Tables and Protection Bits

When solving two-level page table problems, show:

- VA split into page directory index, page table index, and offset,
- PDE address and PDE contents,
- present bit check for the PDE,
- page table base extracted from the PDE,
- PTE address and PTE contents,
- `P`, `W`, and `U` permission bits,
- user-mode versus kernel-mode permission checks,
- read versus write permission checks,
- final physical address if the access succeeds,
- `NONE`, the failure reason, and the faulting table-entry address if it fails.

## Style Constraints

- Prefer concise but complete derivations.
- Avoid vague phrases such as "obvious" when a calculation is needed.
- Keep hexadecimal arithmetic readable by showing intermediate values.
- State final answers clearly under an `Answer` section.
- Use Chinese units and explanations naturally when the problem statement is Chinese.
- The final file should be suitable for study notes or submission reference.

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





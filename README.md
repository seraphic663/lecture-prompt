# Lecture Prompt Repository

Reusable prompt files for coursework workflows. These prompts are written for an AI assistant that can inspect local files, transcribe materials, generate Markdown/LaTeX/notebooks, and report issues when a task cannot be completed perfectly.

## Directory Overview

- `Algorithm/`: Algorithm homework and lab prompts.
- `ICS/`: ICS and ICS II homework prompts.
- `ML/`: Machine-learning lab, homework-report, and notebook prompts.
- `Optimization/`: Optimization-course prompts for PDF-to-LaTeX reconstruction and separate LaTeX solution generation.

## Common Workflow Pattern

Most prompt packs follow a two-step flow:

1. Convert source material into a clean problem/task file, such as screenshots or PPTX into `<root>.md`, or PDF into `<root>.tex`.
2. Generate a separate solution/report/notebook file from that cleaned source.

Do not write answers into the original problem file unless a specific prompt says so.

## Solution Modes

Solution-oriented prompts may support two modes:

- Concise Mode: for users with some foundation. The output focuses on key ideas, essential derivations, final answers, and compact tables.
- Detailed Mode: for zero-foundation or beginner-friendly explanations. The output includes background concepts, definitions, step-by-step reasoning, and explanatory diagrams/tables when helpful.

Users do not need to use the exact words `Concise Mode` or `Detailed Mode`; infer intent from phrases such as "简洁", "只要关键步骤", "复习版", "详细", "零基础", or "讲背景".

If the user does not specify a mode, generate both versions when the prompt supports mode selection.

## Error Reporting

Workflow prompts include an `Error Reporting` section. If a task has missing files, unreadable content, OCR uncertainty, failed commands, missing dependencies, permission issues, or similar problems, continue with a reasonable fallback when possible and create or update `issues.md` in the working/output directory.

Use `issues.md` to record the context, problem, impact, fallback, and whether user input is needed.

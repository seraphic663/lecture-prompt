# Prompt: Write a Lab Solution Markdown File

Use this when an algorithm lab asks for code implementation plus a short explanation.

## Implementation Style

- Follow the textbook method used by the lab material or local PDF.
- Prefer the minimal implementation that shows the required algorithm clearly.
- A small demonstration case is enough unless the lab explicitly asks for large experiments.
- Avoid broad engineering scaffolding, generic frameworks, unnecessary validation layers, logging, statistics counters, and ownership machinery that do not help the algorithm.
- Keep code plain and readable. Prefer ordinary structs/classes and direct helper functions.
- Add appropriate Chinese comments at important algorithmic steps, but do not comment every line.

## Output

Create or update:

- `code.cpp` or the requested source file.
- `题解.md` for the algorithm idea and complexity.
- `report.md` for implementation notes, compile command, and sample output.

The code should be minimal and clear; the solution and report should still be complete enough to explain the algorithm, implementation, complexity, and sample output.


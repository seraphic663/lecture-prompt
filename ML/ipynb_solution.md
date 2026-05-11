# Prompt: Build a Machine Learning Notebook Solution

Use this prompt when creating or rebuilding a notebook solution for a machine-learning lab or homework. This is the default workflow for lab tasks unless the user explicitly asks for a report-only workflow.

## Purpose

Create one or more `.ipynb` solution files from the lab statement and starter script. The notebook should contain complete executable implementation code and clear mathematical or algorithmic explanations.

Do not directly modify the starter script unless the user explicitly requests script edits. Starter scripts such as `script_lab*.py` are read-only by default. The notebook may include complete implementations of the required functions, but the original script file should remain unchanged.

Notebook explanations should be written mainly in Chinese, while keeping important technical terms in English when they are standard course vocabulary, such as Kernel PCA, Lasso, ISTA, K-NN graph, Laplacian Eigenmaps, covariance, eigenvalue, and bandwidth. Code identifiers, file names, function names, and required output names should remain unchanged.

## Inputs to Read

- Assignment PDF or markdown instructions.
- Starter script, if present.
- Existing notebook or rebuild script, if present.
- Result files, generated figures, or previous outputs, if present.

## Workflow

1. Inspect the lab directory and verify exact file names.
2. Read the assignment statement and list the required tasks, functions, outputs, and dependency restrictions.
3. Read the starter script and preserve function names, signatures, return values, imports, dependency limits, and required testing flow.
4. Treat the starter script as read-only unless the user explicitly asks for direct script modification.
5. Choose the requested solution mode. The user may not use the exact labels; infer the intended mode from wording:
   - Concise Mode: for users with some foundation, review, quick completion, or submission-focused work. Use short markdown, essential formulas, core shape notes, and executable correctness.
   - Detailed Mode: for beginner-friendly or teaching-focused work. Build a lecture-style teaching notebook rather than a longer answer sheet. For each task, first restate the concrete assignment requirement and function contract, then explain why the method is needed, introduce the course concept, derive the formula or algorithm, map the formula to code variables and shapes, and finally explain expected outputs or figures.
   - If no mode is specified or the request is ambiguous, generate both a concise/submission version and a detailed/teaching version.
6. Organize notebook cells in the same order as the lab tasks.
7. Before each main code cell, add Chinese markdown explaining the objective, key formula, important shapes, and expected behavior. Keep important technical terms in English where appropriate.
8. Interleave explanation and code by task. For each task, place the explanation cell immediately before the code cell that implements that task's function(s). Do not put all task explanations in one section and all implementations in a later monolithic code cell.
9. Implement the required functions inside the notebook while matching the starter script signatures and testing flow. The task code cell should visibly contain the exact starter function signature for that task. Do not hide the main task implementation behind a differently named helper function.
10. Do not create functions that do not exist in the starter script unless the user explicitly asks for extra helpers. Prefer writing small helper logic inline inside the required starter function. If an extra helper is absolutely unavoidable, stop and explain why before adding it.
11. Do not change function names, argument names, default values, return types, or task semantics from the starter script. If the starter script has a misleading comment or docstring, correct the explanation around it rather than changing the contract.
12. Do not add nonessential defensive code by default. If the starter/test flow already passes valid NumPy arrays and valid positive dimensions, avoid extra lines such as `np.asarray(..., dtype=float)`, `dim = max(int(dim), 1)`, clipping, or broad input sanitization. Add such guards only when the assignment requires them, the starter script already uses them, or a real failure in local verification proves they are needed.
13. Keep the implementation close to a clean student submission: minimal, readable, and directly tied to the task. Prefer explaining assumptions in markdown over adding unnecessary defensive branches in code.
14. End with a full testing cell that reproduces the starter script's intended execution path and saves expected figures or outputs.
15. Run all cells if possible. If notebook execution is unavailable, validate the extracted code with a script or syntax check.

## Detailed Mode Style

Detailed Mode should feel like lecture notes built around the lab, not like a direct code answer. Do not start a task with abstract formulas before explaining the concrete task. A good detailed section usually follows this order:

1. Task entry: what the lab asks, which function is implemented, and how it will be used later.
2. Motivation: why the method is needed for this task and what problem it solves.
3. Concept: the relevant course idea, explained in Chinese with important technical terms in English.
4. Mathematical formulation: formulas and constraints, each tied to code variables.
5. Algorithm: practical steps that will become code.
6. Implementation mapping: shapes, function arguments, return values, numerical-stability choices, and edge cases.
7. Expected observation: what to inspect in printed metrics or saved figures.

Avoid turning Detailed Mode into a list of isolated formulas or a generic lecture unrelated to the task. The task should introduce the concept, and the concept should explain the implementation.

Each task section must end with the code cell for that task before moving to the next task. The code cell should implement only the starter function(s) for that task. Avoid a single large implementation cell containing all tasks.

When starter comments or docstrings are obviously copied from another task and conflict with the lab statement, keep the function signature but correct the notebook explanation and implementation comments so they match the actual task. Do not let a wrong starter docstring become the notebook's teaching text.

Detailed Mode must be readable as a coherent lesson. It should explain the cause-and-effect chain:

- What problem did the previous task set up?
- Why is the current task the next natural step?
- What information is available at this point?
- What information is missing and must be estimated?
- Which formula or algorithm fills that gap?
- Which line of code implements that idea?
- What should the student look for after running it?

Do not assume the reader already understands why a method appears. Before introducing a formula, write the plain-language reason for it. After the formula, map every important symbol to the exact code variable and shape. If a design choice is non-obvious, such as using paired samples, regularization, clipping, or a larger experiment setting than a default argument, explain the reason before the code.

Detailed Mode must also include enough mathematical detail for a student to reproduce the derivation, not just recognize the final formula. For every nontrivial formula or algorithm:

1. Define all symbols before using them.
2. State the objective or constraint in words before writing it mathematically.
3. Show the intermediate step that connects the objective to the update rule or implementation.
4. Explain dimensions beside the formula when shape is part of correctness.
5. Explain numerical parameters such as step size, regularization, thresholds, bandwidth, or scaling factors.
6. End the section with a short plain-language summary of what the code cell will do.

For iterative algorithms, write the objective, gradient or update direction, update rule, stopping/iteration choice, and the role of any shrinkage or regularization. For matrix factorization, projection, covariance, or graph methods, explain why the matrix product has the required shape and what each matrix represents.

Readable Detailed Mode should use short paragraphs with local headings such as `这个 task 要解决什么`, `为什么需要这个方法`, `数学形式`, `从公式到代码`, and `运行后看什么`. Avoid long dense paragraphs and avoid jumping from task statement directly to code.

Detailed math should be concrete enough for oral explanation. It should answer: what is known, what is unknown, what objective is being optimized, how the update or closed form follows, why the dimensions match, and what the printed numbers or figures mean. If the code uses a fixed parameter such as `lambda`, number of iterations, scaling by `1/sqrt(dim)`, or a non-default experiment setting such as `n > 1`, explain the reason and whether it is a tuning choice or just a demonstration setting.

Mathematics and code must be connected continuously, not only in a final "formula to code" paragraph. When introducing a formula, immediately name the exact code variable that stores each mathematical object. When explaining a code line, state the formula or algorithmic step it implements. Keep the mapping local and repeated where needed:

- "The formula uses \(K\); in code this is `k_mat`."
- "The centering matrix \(H\) is not built explicitly; `one @ k_mat` and `k_mat @ one` implement the row/column mean subtraction."
- "The term \(C_i = Z_i Z_i^T\) is the code line `cov = z @ z.T`."

If one lab task contains multiple TODO functions, split the task into function-level subsections. Explain each function's purpose, inputs/outputs, math, and code body before moving to the next function. For example, a "Kernel PCA" task with `distance_matrix`, `kernel`, and `kernel_pca` should have separate subsections for each function, because each function implements a different mathematical step.

Pre-knowledge is allowed only when it directly prepares the specific task/function. Avoid detached lecture material. Every concept paragraph should quickly connect back to the current starter function, its variables, or its code.

## Output

Produce one or more of the following depending on the requested mode:

- Single requested Concise Mode: `<LAB_DIR>/<lab>_solution.ipynb` and, if useful, `<LAB_DIR>/rebuild_<lab>_solution.py`.
- Single requested Detailed Mode: `<LAB_DIR>/<lab>_solution.ipynb` and, if useful, `<LAB_DIR>/rebuild_<lab>_solution.py`.
- No clear mode or both requested: `<LAB_DIR>/<lab>_solution_concise.ipynb`, `<LAB_DIR>/<lab>_solution_detailed.ipynb`, and matching rebuild scripts if useful.
- Generated figures or result files when the notebook is expected to produce them.

If a rebuild script already exists, prefer updating it so the notebook can be regenerated. If no rebuild script exists, create one only when it materially improves reproducibility or verification.

## Error Reporting

If you run into missing files, unreadable content, OCR uncertainty, failed commands, missing dependencies, permission issues, unavailable Jupyter execution, or any other blocker, first try to continue with a reasonable fallback and complete as much of the requested output as possible.

Create or update a short issue report named `issues.md` in the working or output directory:

```md
# Issues

- Context: <file, problem, slide, cell, command, or task>
  Problem: <what went wrong>
  Impact: <what part of the output may be incomplete or uncertain>
  Fallback: <what you did to continue>
  Needs user: <yes/no; what input is needed if yes>
```

Do not stop solely because one item is unclear. Stop only when the task cannot be completed safely or the missing information makes the whole output unreliable.

## Checklist

- The starter script was not directly modified unless explicitly requested.
- All required functions are present in the notebook.
- No extra functions are introduced unless explicitly requested.
- Function signatures match the starter script.
- Each task code cell visibly implements the corresponding starter function(s), with no confusing mismatch between task text, function name, and implementation.
- Function names, argument names, default values, return values, and task semantics are not changed.
- Nonessential defensive casting, clipping, and broad input sanitization are avoided unless justified.
- Dependency restrictions are respected.
- The notebook can run top to bottom, or extracted code passes a syntax/source check.
- Random seeds are fixed when deterministic output is expected.
- No local absolute paths are required inside the notebook.
- Figures and printed metrics are produced when expected.
- Markdown includes both code-level and mathematical explanations.
- Markdown explanations are mainly Chinese, with important technical terms kept in English.
- Detailed notebooks are lecture-style: each task introduces the concept before formulas and code.
- Detailed notebooks explain the full cause-and-effect chain so a reader understands why each task exists and how it follows from previous tasks.
- Detailed notebooks include derivation-level mathematical explanations, not just final formulas.
- Detailed notebooks use readable local headings and short paragraphs.
- Detailed notebooks explain parameters, printed metrics, and figures in a way suitable for oral reporting.
- Detailed notebooks continuously connect formulas to code variables and code lines.
- If a task contains multiple TODO functions, each function is explained in its own subsection before its code appears.
- Explanations and implementations are interleaved task by task; no monolithic all-task implementation cell.

## Avoid

- Do not edit starter scripts by default.
- Do not create functions that are not in the starter script unless the user explicitly asks for them.
- Do not create private helper functions by default; keep small helper logic inline inside the required starter function.
- Do not rename, reorder, or change the parameters of starter functions.
- Do not change the meaning of a starter function to fit your own preferred implementation.
- Do not add nonessential lines such as `np.asarray(..., dtype=float)`, `dim = max(int(dim), 1)`, clipping, or broad validation when the starter/test inputs are already valid.
- Do not add dependencies forbidden by the starter script or assignment.
- Do not omit the testing flow from the notebook.
- Do not provide code without explaining the relevant formulas and shapes.
- Do not separate all task explanations from all task code.
- Do not use a single large code cell for all task implementations when the starter script has multiple tasks.
- Do not copy incorrect starter comments/docstrings into the notebook as if they were correct teaching text.
- Do not write Detailed Mode as disconnected formulas or unexplained code. Explain why each formula and code block appears.
- Do not give only a final formula when a derivation, update rule, or shape argument is needed for understanding.
- Do not write long dense markdown blocks without local headings or plain-language summaries.
- Do not isolate math from code by only adding a final "from formula to code" mapping; connect them throughout the explanation.
- Do not group several TODO functions under one vague explanation when their roles differ.
- Do not invent numeric outputs.

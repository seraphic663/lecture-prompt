请为当前 lab 的 Python 脚本生成一份完整可运行的 Jupyter Notebook 教学版讲义。

目标文件：
- 主脚本：`<LAB_DIR>/<SCRIPT_NAME>.py`
- 任务说明：优先参考 `<LAB_DIR>/<LAB_PDF_NAME>.pdf`
- 如果有 lecture PDF，可以参考，但不要照抄 lecture。

总体要求：
1. Notebook 面向基础较弱的学生，但不要写成冗长教材。
2. Notebook 必须严格围绕原始 lab 脚本展开：按原脚本的 task / function 顺序分块讲解。
3. 代码 cell 应尽量复制当前脚本中的代码，不要擅自重构函数签名、返回值或实验流程。
4. 不要为了教学额外创建无关 demo。可以加必要的 markdown 解释，但代码主体应来自原 lab。
5. 如果原 lab 限制第三方包，Notebook 必须遵守同样限制。
6. 图像中的标题、坐标轴、legend 等保持英文，避免中文字体渲染问题；markdown 讲解使用中文。
7. 所有公式使用块公式格式：
   $$
   ...
   $$
8. Notebook 必须能从头运行到尾，不能留未定义变量或伪代码。
9. 如果发现 lab PDF、脚本注释、代码实现之间有细微不一致，需要在 markdown 中温和指出，并说明采用哪个版本以及原因。
10. 不要引入和原 lab 不一致的额外参数，例如原函数没有 `return_history` 就不要添加；原脚本没有单独 objective 函数就不要额外拆出，除非用户明确要求。
11. 例如np的一些少见函数，可以在 cell 中细致解释，在 code 中可以描述，不要搞混了。

Notebook 结构要求：
1. 标题与整体说明
   - 简要说明这个 lab 在做什么。
   - 明确说明 notebook 是按原脚本分块讲解，不是重写一份新代码。

2. 准备部分
   - 复制原脚本中的 import、数据生成、辅助函数、评价函数、可视化函数。
   - 在 markdown 中说明这些函数的作用即可，不要过度讲可视化细节。

3. 按 task 分块讲解
   对每个 task，采用以下结构：
   - 一个 markdown cell：解释该 task 的数学目标、输入输出、关键 shape。
   - 一个 code cell：复制或贴近复制原脚本中对应 task 的代码。
   - markdown 中要解释关键公式“这句话在说什么”，不要只堆公式。
   - 对矩阵或数组运算，尽量标明 shape，例如：
     - `x_train: (N, D)`
     - `y_train: (N, 1)`
     - `K: (N, N)`
     - `prediction: (M, 1)`

4. 核心数学解释
   - 对 closed-form / gradient / coordinate update / dynamic programming / EM / optimization 等核心推导，必须给出精简但完整的推导。
   - 不需要写得像教材，但不能只给结论。
   - 如果推导较难，可以先给结论，再解释直觉。

5. 实验部分
   - 复制原脚本的测试流程。
   - 保持原脚本的输出和图像保存方式。
   - 解释主要实验现象，但不要过度展开可视化代码。
   - 如果有 `result.txt` 或已有输出文件，要结合其中结果做简要解释。

6. 总结与复习清单
   - 用简短中文总结每个 task 的核心。
   - 给出学生交作业前应能回答的问题清单。
   - 不要写太长。

额外限制：
1. 不要修改原脚本，除非用户明确要求。
2. 不要生成大量额外文件。
3. 不要把 notebook 做得过大。
4. 不要使用中文作为 matplotlib 图标题或 label。
5. 不要把代码中的英文函数名、变量名翻译成中文。
6. 如果 notebook 中出现乱码、公式渲染异常，应修复为 UTF-8 和 `$$...$$` 格式。
7. 如果原脚本中保留了 `TODO` 注释但代码已经实现，可以保持原样；如需教学清晰，可在 markdown 中说明“这里虽然保留 TODO 注释，但下面已经是实现代码”。

输出要求：
- 直接生成 `<LAB_DIR>/<LAB_NAME>_teaching_notebook.ipynb`。
- 如需要生成 notebook 的辅助脚本，可以命名为 `<LAB_DIR>/rebuild_<LAB_NAME>_teaching_notebook.py`。
- 生成后必须检查：
  - notebook JSON 可解析；
  - 无乱码字符；
  - 无擅自新增的函数参数；
  - code cells 能按顺序运行；
  - 图中文字为英文。

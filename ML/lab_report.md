请为当前 lab 写一份简洁但完整的 LaTeX report。

输入文件：
- 主脚本：`<LAB_DIR>/<SCRIPT_NAME>.py`
- 任务说明：`<LAB_DIR>/<LAB_PDF_NAME>.pdf`
- 实验输出：`<LAB_DIR>/result.txt`，如果存在
- 调参输出：`<LAB_DIR>/tuning_result.txt`，如果存在
- LaTeX 模板目录：`<TEMPLATE_DIR>`

基本要求：
1. 不要直接修改 template 原件。请先把 template 中的 `main.tex` 复制到当前 lab 目录，命名为 `report.tex`。
2. 如果 template 有 `refs.bib`，也复制到当前 lab 目录。
3. 保留 template 的 preamble、页数限制、基本结构和提交格式。
4. 删除 `Question XX`、`Student Name`、`XXXX` 等占位符。
5. report 使用英文撰写，避免 LaTeX 中文编译问题。
6. 内容要简洁，目标是能放进 template 的 3 页限制内。
7. 不要把代码完整粘贴进 report；只解释关键实现、公式、实验结果。
8. 不要写成教程或 lecture notes，而是写成 lab report。
9. 如果本机不能编译 PDF，要明确说明只能做源码级检查。

内容结构要求：
1. 标题
   - Course / Lab 名称
   - 学生姓名和 ID

2. 按任务分节
   - 使用类似：
     - `Task 1: ...`
     - `Task 2: ...`
     - `Task 3: ...`
     - `Task 4: ...`
   - 每个 task 说明：
     - 实现了什么；
     - 关键数学公式；
     - 关键 shape 或变量含义；
     - 重要实现选择；
     - 如果有数值稳定性处理，也要简要说明。

3. 对 closed-form / gradient / update rule 给出精简但完整推导
   - 例如 closed-form KRR 不能只写最终结论，要简要展开目标函数、写梯度、说明如何得到线性系统。
   - SGD 要写清楚完整梯度和 mini-batch 近似。
   - BCD / coordinate descent 要写清楚二次型重写和单坐标更新公式。
   - 推导要短，但不能跳到让人看不懂。

4. 实验观察部分
   - 必须阅读并引用 `result.txt` 中的实际数字。
   - 不要泛泛说“效果不错”，要结合具体 MSE。
   - 说明哪些结果符合预期，哪些结果异常，以及原因。
   - 如果某个方法数值不稳定，要说明可能原因。

5. 调参部分
   - 如果有 `tuning_result.txt`，必须总结调参设计和关键结果。
   - 不要把完整 tuning 表复制进 report；完整表格只需引用文件名。
   - 简要说明：
     - 每个 task 调了哪些参数；
     - 每个参数大约多少候选值；
     - 总组合规模；
     - 大致运行时间；
     - 最佳参数组合和最佳 MSE。
   - 如果调参用的是 test MSE，要说明这是 lab comparison；严格 ML pipeline 应该使用 validation set。

6. 最后一节可读性
   - 避免长段落堆数字。
   - 更推荐短段落结构，例如：
     - `Fixed grid.`
     - `Tuning setup.`
     - `Best tuned MSE.`
     - `Special cases.`
   - 如果结果多，用一个简短排序公式或简短表述，例如：
     $$
     \text{KRR }(0.5016)
     < \text{BCD }(6.0308)
     < \text{NW }(6.2572)
     < \text{SGD }(7.2197).
     $$
   - 不要在最后塞过大的表格或跨页 bullet list。

风格要求：
1. 英文、简洁、report 风格。
2. 不要过度解释基础概念。
3. 每个公式后要有一句自然语言说明它在实现中对应什么。
4. 实验结论要明确，但不要夸大。
5. 如果某个结果来自调参文件，要写：
   - `Full tables are saved in tuning_result.txt.`
6. 如果某个 PDF 或脚本注释与代码实现有细微差异，要温和说明采用哪个版本。
7. 保持整体在 3 页内。

验证要求：
完成后检查：
1. `report.tex` 是否保留 template preamble。
2. 是否没有修改 template 原件。
3. 是否没有模板占位符：
   - `Question XX`
   - `Student Name`
   - `XXXX`
   - `Date of Submission`
4. 是否没有乱码或 LaTeX 明显错误。
5. 是否引用了 `result.txt` 的关键数字。
6. 如果有 `tuning_result.txt`，是否总结了调参结果。
7. 如果本机有 `pdflatex`，编译并检查页数是否不超过 3 页。
8. 如果没有 `pdflatex`，说明未能编译，只完成源码级检查。

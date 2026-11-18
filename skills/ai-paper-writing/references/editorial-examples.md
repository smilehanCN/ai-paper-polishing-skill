# 四个常见的改稿决定

以下场景和数值均为教学示例。英文示范段落可按作者的真实证据改写。

## 1. 从挑战推导贡献，再决定首页图画什么

设想一篇文档问答论文。系统已经检索到正确的临床试验段落，回答“对照组有多少人”时却抄了治疗组的数字。作者的贡献是先把数值与所属组别配对，再生成答案。这层对应可以用两句英文写进引言。

> A retrieved passage may name the correct trial but report enrollment for several treatment arms. We link each count to its treatment arm before selecting the count that answers the question.

若首页只讲挑战，画出原文、问题和两个容易混淆的数值。若要突出贡献，放大组别与数字的配对过程。若要让读者同时看清挑战和解决思路，就在同一段原文上并排展示错配与修正。如果论文还涉及跨表格匹配，且两种困难同等关键，则可用同一问题的段落版和表格版讲全挑战。

## 2. 用最小例子解释运算顺序

假设一个图像分割方法先将两个增强视图的掩膜变换回原始坐标，再对概率取平均。直接从变换公式写起，读者可能看不出为什么顺序重要。先跟踪一个像素的位置。

> A pixel on the left edge of the original image appears on the right after a horizontal flip. We map both predictions back to the original coordinates before averaging, so each pair of probabilities refers to the same pixel.

方法图中，两条分支都应从各自的坐标对齐步骤连到求平均的节点。这样，两句文字能同时帮助读者理解公式和检查图中的计算流程。

## 3. 把消融写成一个有结论的实验小节

假设一个边界监督方法在两个验证集上取得以下结果。模块与损失、骨干及训练预算均有记录。

| 训练条件 | 验证集 A 的边界 F1 | 验证集 B 的边界 F1 |
| --- | ---: | ---: |
| 标准训练 | 71.0 | 68.2 |
| 增加特征融合模块 | 72.0 | 69.1 |
| 在同一模块上增加边界损失 | 73.1 | 69.2 |

若本节目的是判断边界损失还有没有额外作用，应读后两行。假设前文已经讲过数据集和指标，正文只需交代这一处对照的设置。

> We ask whether boundary supervision still helps once feature fusion is in place. We train the same fusion model with and without the boundary loss, holding the training budget fixed. Adding the loss raises boundary F1 by 1.1 points on A and 0.1 points on B. Boundary supervision thus adds to the gain from fusion in both settings, although its incremental benefit is much smaller on B.

最后一句回答了是否有额外收益，以及收益是否一致。两个数据集的差异本身还不足以解释差异的成因。

## 4. 用分母说明一个百分数的实际含义

设想两个检索子集分别有 20 和 1,000 个相关条目。系统分别多找回 1 个和 10 个，召回率的绝对增幅为 5 和 1 个百分点。读者关心相对覆盖变化还是找回条目的数量，决定正文应保留哪些量。

> Recall rose by 5 percentage points on the smaller subset and by 1 point on the larger subset. These gains correspond to one and ten additional relevant items, respectively.

只有新增计数和分母来自同一评估集合，这样的解释才成立。

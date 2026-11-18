# 方法论文的 Related Work 怎么写

引言交代为什么值得做这项研究。读完独立的 Related Work，读者应能说出哪些工作与本文最接近、它们解决了什么，以及从哪一步开始，本文作出了不同的技术选择。

## 先给每个小节分配一个问题

重读定稿引言，用普通词写下读者进入方法节之前需要弄懂的事。再把已有引用放到相应问题下，检查每组能否围绕一个共同对象展开比较。下面三种问题适合当作起点，实际标题应写出具体任务或机制。

| 小节要回答的问题 | 如何组织 | 在哪里收尾 |
| --- | --- | --- |
| **这项任务通常怎样完成？** | 挑能解释后续方法或基线的技术路线，按输入、求解方式或输出组织。名称后面写一个具体动作。 | 读者能分清后文会出现的几类方法时就可以停。 |
| **和本文最像的工作究竟做了什么？** | 给最接近的方法更多篇幅。逐项比较查询用什么信息、取回什么内容、结果交给哪个步骤。 | 在最容易混淆的那项工作旁写一句本文定位，先交代共享的思路，再指出发生变化的具体操作。 |
| **相邻领域的思路怎样用于这里？** | 写出两个领域共享的对象或约束，再说明它在两个场景中分别作用于哪个环节。 | 如果这里只负责交代背景，可以停在代表工作。如果还有一项独立的技术区别，就用一句话点明。 |

分组也可以跟随任务之间的依赖关系。VGGT 在 §2 中从运动恢复结构（SfM）转到多视图立体重建（MVS），两者通过相机参数联系起来。后者通常需要相机参数，而这些参数常由前者估计。随后介绍可直接从图像对估计稠密点云的工作，读者就能看出它省去了哪个前提。MAPF-GPT 则先梳理多智能体寻路的求解路线，再单列离线强化学习、多智能体模仿学习。前一组帮助理解求解任务，后两组帮助辨认策略从什么训练信号中学到。[VGGT，CVPR 2025，§2](https://openaccess.thecvf.com/content/CVPR2025/papers/Wang_VGGT_Visual_Geometry_Grounded_Transformer_CVPR_2025_paper.pdf#page=2) · [MAPF-GPT，AAAI 2025，Related Works](https://ojs.aaai.org/index.php/AAAI/article/download/34477/36632#page=2)

## 技术路线切换时，把中间那步写出来

先圈出前一句讨论的对象，再问下一句改变了什么。常见的变化有三个：**一个步骤的输出成为下一步的输入**，**同一操作读取的内容改变了**，或者**同一种信息在不同阶段发挥作用**。选最能解释眼前这次转折的一种。段首仅加 *Moreover* 或 *Recently*，读者仍需自己猜两组工作的关系。

以下是教学用的英文改写。

- **从求解步骤转到其输入条件。** “Multi-view stereo typically takes camera parameters as input. Structure-from-motion pipelines supply these estimates, while some learned methods recover dense geometry directly from an image pair.” 这里的衔接靠相机参数完成。读者能沿着同一个量理解两条路线。[VGGT，§2](https://openaccess.thecvf.com/content/CVPR2025/papers/Wang_VGGT_Visual_Geometry_Grounded_Transformer_CVPR_2025_paper.pdf#page=2)
- **从一种机制转到另一种训练方式。** “A consistency model can serve as the student of a pretrained diffusion model. The same type of model can also be trained from scratch, which brings the training objective itself into focus.” 两句都在讲一致性模型，变化的是学生模型如何得到监督。这时再谈端到端训练的差别，比较对象就清楚了。[One Step Diffusion via Shortcut Models，ICLR 2025，§4](https://proceedings.iclr.cc/paper_files/paper/2025/file/559a0998fab1d19b80e7e43a5852401c-Paper-Conference.pdf#page=6)

扩写几十个词时，优先补足这类承接，或给最接近的一篇补上具体操作。核对每个引用所支持的句子，尤其是把一串引文拆开以后，哪篇提出原始机制、哪篇处理它在某种条件下的局限。作者在当前实验中对基线做的改动，归入本文实验设置。

## 本文的定位放在哪里

**第一次可能被误认成已有工作时，就地说明。** 比较双方尽量使用相同主语、输入和动作。LoopFormer 在介绍按循环步编号调节模型的 TMLT 后，直接交代自己同时使用归一化时间和步长，并在多种计算轨迹上训练。这一句能放在这里，是因为上一句刚给出了可比的条件。STCast 在 §2.1 紧接 OneForecast，对比固定邻域拼接和可学习的全球与区域之间的关联。到 §2.2 讨论专家模型时，才解释按月份路由这项独立设计。[LoopFormer，ICLR 2026，§2](https://proceedings.iclr.cc/paper_files/paper/2026/file/4edfc7fb472789e31de455f8735ecbc3-Paper-Conference.pdf#page=3) · [STCast，CVPR 2026，§2](https://openaccess.thecvf.com/content/CVPR2026/papers/Chen_STCast_Adaptive_Boundary_Alignment_for_Global_and_Regional_Weather_Forecasting_CVPR_2026_paper.pdf#page=2)

**差别需要两条路线共同解释时，等两条都交代清楚再定位。** PIR 的 §2.1 写预测方法，停在该领域的进展。§2.2 再说明局部窗口的外生信息与全局历史检索，最后才点明本文先识别可能失准的预测，再利用这两类上下文订正。PFRP 采用另一种安排。第一小节交代预测器能访问的历史范围，第二小节围绕检索方式和与现有预测器的配合，进一步划清与同类方法的关系。两次提及本文，各自回答了新问题。[PIR，NeurIPS 2025，§2](https://papers.neurips.cc/paper_files/paper/2025/file/331c41353b053683e17f7c88a797701d-Paper-Conference.pdf#page=3) · [PFRP，AAAI 2026，Related Work](https://ojs.aaai.org/index.php/AAAI/article/download/39230/43191#page=2)

## 用三次短读检查成稿

1. **只读小标题和每节末句。** 能否给每节写出一个不同的问题？若两节在回答同一个问题，可以合并。若几节最后都落在同一句贡献，保留紧邻最相似工作的那一处，让背景节以领域事实收尾。
2. **只读相邻两段的末句和首句。** 能否指出一个共同的对象，以及发生变化的条件、动作或输出？找不到时，先补中间那层关系，再决定要不要加连接词。
3. **只读最接近工作和本文定位的相邻几句。** 暂时遮住模型名。读者仍应能指出双方共享什么、在哪一步分开。对于“首次”“优于所有方法”等判断，核对原作及本文比较范围，再决定这句话能写多强。

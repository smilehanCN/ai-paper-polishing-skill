# 五段式 Introduction 写作参考

用于起草或重构引言，也可单独用来打磨贡献列表。先让读者理解论文要解决的困难，再解释作者为什么想到这个办法。下表按阅读顺序列出五项写作任务。实际段数由论述需要决定。

| 环节 | 写到这里，读者应该明白什么？ |
| --- | --- |
| **1. 背景** | 任务是什么，解决它有何应用价值或科学意义？选一个能通向后文挑战的场景。例如，多智能体路径规划要让多个智能体在共享空间中无碰撞地抵达各自目标，仓库调度就需要这样的路径。 |
| **2. 相关工作** | 最接近的技术路线已经做到了哪里？选出与核心问题有关的进展，再指出这些做法共享的前提，或至今难以处理的情形。若另设 Related Work 章节，引言只需给出理解挑战所需的文献与比较。 |
| **3. 挑战** | 困难在什么条件下出现，为什么难，会导致什么后果？一般提炼两点。若一个研究问题就能贯穿全文，也可以集中讲清这一点。MAPF-GPT 用一个问题串起后文。仅靠大规模专家示范进行监督学习，能否得到推理时直接选动作的强求解器？[MAPF-GPT，AAAI 2025](https://ojs.aaai.org/index.php/AAAI/article/download/34477/36632) |
| **4. 方法** | 先用一句话交代整体思路，再沿用挑战段的顺序与关键词，解释为什么这样设计、具体做了什么、它怎样解决困难。读者应能从操作本身理解机制。 |
| **5. 贡献** | 用 3–4 点留下最值得记住的原创工作。方法段让读者跟上解题过程，贡献列表从中挑出有独立价值的想法和结果。 |

**什么时候拆段？** 若两个困难可以一起理解，就先讲全挑战，再分别解释回应。PFRP 提出如何检索历史序列、如何把检索结果用于当前预测，随后各用一段介绍设计。若读者必须先理解第一项设计才能看见第二个困难，可以按“挑战一与回应一、挑战二与回应二”展开。T2V-CompBench 先交代如何设置组合式视频生成任务，再引出随之而来的度量问题。怎样判定对象、动作与时序关系是否正确？[PFRP 引言](https://ojs.aaai.org/index.php/AAAI/article/download/39230/43191) · [T2V-CompBench 引言](https://openaccess.thecvf.com/content/CVPR2025/papers/Sun_T2V-CompBench_A_Comprehensive_Benchmark_for_Compositional_Text-to-video_Generation_CVPR_2025_paper.pdf)

## 方法论文的贡献怎么写

1. **整体贡献写研究思路。** 交代提出了什么方法，以及它从什么角度解决核心问题。以 PFRP 为例，预测器在推理时用当前序列查找相似的历史片段，再用那些片段之后实际发生的序列辅助预测。试着遮住方法名，读者仍应能复述这项想法。[PFRP，AAAI 2026](https://ojs.aaai.org/index.php/AAAI/article/download/39230/43191)
2. **技术贡献写最有辨识度的设计。** 把“为什么难”接到“具体怎样做”，再说这个操作带来了什么能力。STCast 要解决区域预报该从哪些域外位置取信息的问题。它用地理距离初始化全球位置对目标区域的影响权重，再在训练中学习这些权重，使区域预报能利用远处的信息。只给出“空间对齐注意力”这个名字，读者就看不到这项设计。若两项技术创新各自回应不同困难，且都能独立讲清，可将这一条拆成两条。[STCast，CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/papers/Chen_STCast_Adaptive_Boundary_Alignment_for_Global_and_Regional_Weather_Forecasting_CVPR_2026_paper.pdf)
3. **实验贡献写本文确立的主要结论。** 先选一项能回答引言核心问题的发现，再给支撑它的比较对象、条件或幅度。MAPF-GPT 在专家轨迹上做模仿学习，所得策略能直接为每个智能体选动作，并在未见地图上展示零样本求解能力。“未见地图”交代了证据的范围，也回答了开头关于这种训练方式能做到什么的疑问。[MAPF-GPT，AAAI 2025](https://ojs.aaai.org/index.php/AAAI/article/download/34477/36632)

三条的顺序可随创新重点调整。PFRP 先写存储历史样本的记忆库，再写建立在它之上的预测方法。STCast 先写自适应区域边界，再写包含时间专家的整体框架。把自己的前两条放在一起读。如果互换“框架名”和“模块名”仍然读得通，给其中一条补上只有它才具备的设计或能力。[PFRP 贡献段](https://ojs.aaai.org/index.php/AAAI/article/download/39230/43191#page=2) · [STCast 贡献段](https://openaccess.thecvf.com/content/CVPR2026/papers/Chen_STCast_Adaptive_Boundary_Alignment_for_Global_and_Regional_Weather_Forecasting_CVPR_2026_paper.pdf#page=2)

## 首页图与论文类型

**先写引言第一次引用首页图的那句话。** 如果读者最难理解的是挑战，就用可比较的案例画出困难。一张图可以聚焦最突出的一点，也可以呈现几个挑战的关系。如果本文的设计最值得先讲，就画出贡献或它们如何配合。挑战和解法能用同一案例串起来时，让读者沿图走一遍。PFRP 图 1(a) 用相隔近一年的相似用电曲线引出历史检索，(b) 和 (c) 接着展示存什么、怎样取用，以及检索结果如何参与预测。缩到最终栏宽，检查读者能否指出哪一处支持引言的那句话。[PFRP 图 1](https://ojs.aaai.org/index.php/AAAI/article/download/39230/43191#page=1)

**按原创成果调整贡献的重心。** 实证分析论文可先写新发现及其成立条件，例如改变采样次数后，强化学习模型与基础模型的推理表现如何变化。理论论文可先写主要定理、关键假设及其含义，例如图结构在什么条件下改变样本复杂度下界。以基准为原创成果的论文，可以依次写评测缺口、基准设计和由此揭示的发现。[实证分析，NeurIPS 2025](https://proceedings.neurips.cc/paper_files/paper/2025/file/537d5aa768c2d534016a4d06f87bc8fb-Paper-Conference.pdf) · [理论研究，ICLR 2026](https://proceedings.iclr.cc/paper_files/paper/2026/file/3f0c8c5dc6b16e601b78e164a70d68a2-Paper-Conference.pdf) · [基准研究，CVPR 2025](https://openaccess.thecvf.com/content/CVPR2025/papers/Sun_T2V-CompBench_A_Comprehensive_Benchmark_for_Compositional_Text-to-video_Generation_CVPR_2025_paper.pdf)

## 改完做两次回读

- **只读挑战段和贡献列表。** 能否复述作者解决了什么、靠什么解决？以 PFRP 为例，两项任务是找到可用的历史序列、把它们融入当前预测。贡献列表里的历史记忆库、检索预测和与局部预报器的融合，分别给出了落点。
- **只读方法段和贡献列表。** 哪些设计值得写进贡献，哪些细节留在方法段就够了？PFRP 的方法段解释查询键、返回值和门控，贡献段提炼出两个能分开陈述的想法。一个设计决定历史库里存什么，推理时怎样查用。另一个设计决定如何把检索得到的预测与局部预报器的输出结合。用这两遍回读检查自己的稿件时，把最难复述的那一条作为下一处改写目标。[PFRP 引言与贡献段](https://ojs.aaai.org/index.php/AAAI/article/download/39230/43191#page=2)

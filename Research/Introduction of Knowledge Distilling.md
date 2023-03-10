#Research #KD #DL 


目的：将大模型简化，以便部署在终端，进行实时的边缘计算
一些可能的库：模型压缩库 MMRazor: Pruning, KD, 神经架构搜索、量化
MMDeploy: 模型部署库
Github. Com/Hobbitlong/RepDistiller

这篇笔记来自*Distilling the knowledge in a neural network*

## Introduction
如何定义知识？一定不是指模型中的权重，因为这样我们根本无法改变模型的结构。我们认为，模型输出值之间的相对大小（正确类别和错误类别的相对大小）已经包含了知识。因此，最简单的学习方式是使用教师网络的 Soft Targets 作为学生网络的输入。如果 Soft targets 里面的熵比较高，那么就可能提取出更丰富的信息，这种方式比 Hard Targets 是更好的。
KD 的一个潜在好处是，如果采用了教师网络-学生网络的模式，那么你可以随意找数据集，让教师网络标注，这样你相当于拥有了无限大的数据集。

因为现在已有的模型建立得太好了，因此我们考虑把模型的操作放松一点。所以我们就可以引入温度。记 $z_i$ 为 logit 分数，那么
$$
q_i = \frac{\exp(z_i/T)}{\sum_i \exp(z_i/T)}
$$
教师网络将生成“蒸馏”后的知识，学生网络将做两件事，首先，学生网络必须使用同样的 $T$ 来拟合教师的知识；其次，学生网络还需要学习一些 ground Truth。

此外，直接拟合 Logit 是知识蒸馏的一个特例。这可以证明。记 $C$ 是 soft loss，那么
$$
\frac{\partial C}{\partial z_i} = \frac{1}{T}({\frac{\exp(z_i/T)}{\sum_i \exp(z_i/T)}}-{\frac{\exp(v_i/T)}{\sum_i \exp(v_i/T)}}) \approx\frac{1}{NT^2}(z_i-v_i)
$$
$z_i$ 是学生网络输出的 logit，$v_i$ 是教师网络输出的 logit，这个近似仅仅在 $z_i,v_i$ 都是 zero- mean，而且 $T$ 非常高的时候。

不同的网络大小可能会影响温度。一般来说，神经网络越大，需要的蒸馏温度也越高。

知识蒸馏可以实现 Few-shots Learning 甚至是 Zero-shot Learning ，你在训练学生网络的时候，把数据集中的一部分移走，学生网络仍然可以学到相应知识，只不过正确率低一些。

## 训练“专才”模型
对于一个超大的数据集，以往的做法通常是使用一个超大的网络，这种网络通常使用数据并行或者模型并行的方式进行长时间的训练。为了解决训练消耗的资源太大、用时太长的问题，我们会使用一个通用模型和专才模型。专才模型只关注一个小类，除了这个小类，其余的类别都是垃圾类。
每个专才模型首先使用通用模型进行初始化，然后被放到特制的数据集上进行计算——一半数据是专用的数据，另一半是随机选出来的。
具体如何选择需要被专才模型再次预测的部分，直接对通用模型预测结果的协方差矩阵进行聚类
在预测的时候，我们希望预测结果既和通用模型有相似的结果，又和专才模型有接近的结果。

## 一些研究方向
- 容易水文章？为什么知识蒸馏真的有用？
![[Pasted image 20230305102509.png|400]]

- 教师网络和学生网络之间是不是可能有互动
- 多个同学是可行的吗？ Teaching Assistant 是可行的吗？
- 多模态的知识蒸馏
- 对知识图谱进行知识蒸馏
- 对预训练的大模型进行知识蒸馏
- 如何表示中间层的特征
- 对比学习

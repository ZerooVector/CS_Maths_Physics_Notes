#NLP 
![[Pasted image 20230928140129.png]]
所有的 NN 都是有线性变换和非线性变换组成的

在 CNN 中，我们发现低频信息实际上保留的是语义信息（复原图像可以被肉眼识别），但是对神经网络没有用；高频信息复原后不可对肉眼识别，但是神经网络可以识别。在机器学习中，神经网络将学习一个滤波器，从而获得特定频率上的信息。CNN 适合数据具有空间相关性的情况。

通用近似定理表明，一个前馈神经网络，如果具有线性输出层和至少一层具有任何一种“挤压”性质的激活函数的隐藏层，只要给予网络足够数量的隐藏单元，它可以以任意的精度来近似任何从一个有限维空间到另一个有限维空间的 Borel 可测函数。

CNN 中由于临近的位置上有较高的相似性，且每个像素只提供非常少量的语义信息，因此我们可以池化。

- 为什么网络越来越深、越来越窄？
- 在增加相同的能力时，增加宽度会带来神经元数目的指数级上升；增加深度只会使得神经元数目多项式级别上升

![[Pasted image 20231009154936.png|400]]
RNN 可以分类句子，可以考虑句子中的某一位置，可以预测下一个位置。RNN 中，历史信息的权重是相等的，容易出现梯度消失/爆炸的问题。

LSTM：将自由度（记忆的时间长度）作为一个自由度，也适合处理输入数据带有时间相关性的情况。
如何让每个词包含上下文的信息？看下面：这样可以一定程度上消除歧义
![[Pasted image 20231009160745.png|400]]

RNN（递归神经网络）是一种类似于 CNN 的网络，只不过，CNN 更加规整而 RNN 不是那么规则。CNN 是一堆滤波器，而 RNN 的结构中有语义信息。


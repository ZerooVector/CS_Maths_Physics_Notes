#NLP 

你将学到什么：
- Foundation: Rucurrent Network, Attention, Transformer
- A big picture of NLP 
- Ability to build system of NLP in pytorch 

语言的意义是什么？语言学家认为，语言作为一种 signifier，其意义是其表征之物。但是，这种方式是主管的，需要大量人力随着时代不断更新，而且我们无法度量两个词直接的精确相似度
在现代 NLP 中，我们将单词视作离散符号，并且通常使用向量对每个词进行编码，这些编码包括：
- One Hot Encoding（作为一种统计学习方法，我们无法在其中编码语义的相似性） ，这种表示被称为局部表示，因为一个词的信息只分布在向量的一个维度上。
- 现代深度学习中，我们的编码基于 Distributional Semantics ，也就是说，一个词的词义是由其相近的词给出的。在这种假设下，我们希望使用一个稠密的实数向量代表每个词的含义。这种表示是一种分布式表示，因为信息分布在向量的每个维度上 Word 2 Vec 方法提供了一种在大量语料库中学习每个词的向量表征的方式
![[Pasted image 20230804102333.png]]

## Word 2 Vec 简介
### 目标函数 
在这里，我们使用的 Word 2 Vec 是利用中心词预测周围词的做法，因此，我们的目标是使得周围词预测的准确率最大。这可以使用极大似然估计写出：
![[Pasted image 20230804102852.png|450]]

### 概率的计算
那么，我们如何从单词的向量表示推出单词出现的概率呢？我们使用 $v_{W}$ 代表一个 $w$ 是中心词时其词向量，在它为周围词时，则使用 $u_{w}$ 代表。那么，在一个中心词 $c$ 出现的情况下，我们使用如下方式计算周围词 $o$ 出现的概率：
$$
P(o|c) = \frac{\exp (u_{o}^{T}v_{c})}{\sum_{w \in V} \exp(u_{w}^{T}v_{c})}
$$

### 优化方式
我们会将所有向量拼成一个大的向量，使用梯度下降的方法同时优化所有参数。我们将计算偏导数。
$$
\begin{align}
\frac{\partial }{\partial v_{c}} \log \frac{\exp(u_{o}^{T}v_{c})}{\exp(\sum_{w} \exp (u_{w}^{T}v_{c}))}\\
= & \frac{\partial }{\partial v_{c}}\log \exp(u_{o}^{T} v_{c}) - \frac{\partial }{\partial v_{c}} \log  \sum_{w} \exp(u_{w}^{T} v_{c}) \\ 
= & \frac{\partial }{\partial v_{c}} u_{o}^{T}v_{c}  - \frac{1}{\sum_{w} \exp (u_{w}^{T} v_{c})} \frac{\partial }{\partial v_{c}} \sum_{x} \exp(u_{x}^{T} v_{c}) \\
= & \frac{\partial }{\partial v_{c}} u_{o}^{T}v_{c} -  \frac{1}{\sum_{w} \exp (u_{w}^{T} v_{c})}  \sum_{x} \exp(u_{x}^{T} v_{c}) \frac{\partial }{\partial v_{c}} u_{x}^{T} v_{c}
\end{align}
$$
简化一下，使用符号 $U_{x} =  \frac{\partial }{\partial v_{c}}u_{x}^{T}v_{c}$，那么：
$$
\frac{\partial }{\partial v_{c}} \log P(o|c) = U_{o} - \frac{\sum_{x} \exp(u_{x}^{T} v_{c})u_{x}}{\sum_{w} \exp(u_{w}^{T}  v_{c})}  = U_{o} - \sum_{x} P(x|c) U_{x} = U_{o} - \mathrm{E}(U_{X})
$$
其中，式中的期望是遍历语料库中的每个词的

### 模型的应用
这个模型可以完成如下的任务：
- 通过计算相似度，完成“寻找最相似的词”任务
- 通过词向量的加减运算，完成类比任务，例如：“铅笔之于素描正如摄像机之于照片”





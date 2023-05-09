#ML/DS 

MOTIVATION : 我们关注高维随机变量的概率密度函数。
在开始推导之前，我们先给出概率论中几个基本的计算法则：
- 加法法则
$$
P(x_{i}) = \int P(x_{i},x_{j})dx_{j}
$$
- 乘法法则
$$
P(x_{i},x_{j}) = P(x_{i}) P(x_{i}|x_{j})
$$
乘法法则的推广会带来链式法则
- Bayes 定理
$$
P(x_{2}|x_{1}) = \frac{P(x_{1},x_{2})}{P(x_{1})} = \frac{P(x_{1},x_{2})}{\int P(x_{1},x_{2})dx_{1}} = \frac{P(x_{1})P(x_{1}|x_{2})}{\int p(x_{1})p(x_{1}|x_{2})dx_{1}}
$$
问题是：高维的联合概率计算复杂，因此，最简的假设是设各个维度之间互相独立（这个假设过于简单）
$$
P(x_{1},\cdots ,x_{n}) = \prod P(x_{i})
$$
将这个放松一点，我们就有 Markov 性质，即：$x_{i+1}$ 仅仅与 $x_{i}$ 有关，而与其他无关。例如，在 HMM 中，我们有其次马尔可夫假设。但是，如果我们觉得这个性质还是太强，我们就有条件独立的假设，也就是说，$P(x_{i}|x_{j})$ 与其他变量是无关的

图模型主要分为表征 (Representation)、推断 （Inference）和学习 (Learning)三部分

## Bayes Network
### Representation

#### 三种经典的图结构
Bayes 网络的作用是使得每个点的概率仅与其父节点相关，也就是说：
$$
P(x_{1},x_{2},\cdots ,x_{n}) = \prod  P(x_{i}|\mathrm{parents (x_{i})})
$$
例如，我们有三种典型的图结构：
![[Details about graph models 2023-04-04 09.10.23.excalidraw]]
对于 tail to tail 的图中，我们有 $a \rightarrow b, a \rightarrow c$，那么，按照上式：
$$
P(a,b,c) = P(a)P(b|a)P(c|a)
$$
按照链式法则：
$$
P(a,b,c) = P(a)P(b|a)P(c|a,b)
$$
那么，我们有
$$
P(c|a) = P(c|a,b)
$$
也就是说，$c$ 和 $b$ 在 $a$ 的条件下是独立的（无论 $b$ 发布发生，都不影响 $c$ 的发生概率），或者，你可以等式两边同时乘以 $P(b|a)$，可以推出：
$$
P(c|a) P(b|a) = P(b,c|a)
$$
这个被叫做 Tail to Tail 是因为对于 $b$ 和 $c$ 来说，都是被指到的。一旦中间的 $a$ 已知那么从 $b$ 连接到 $c$ 的点就被堵塞了，此时 $b$ 和 $c$ 就在 $a$ 已知的条件下独立

对于 head to tail 的图中，使用类似的方法，我们可以得到：
$$
P(c|b) = P(c|a,b) 
$$
也就是说，无论 $a$ 的结果为何，都不影响 $c$ 的发生，因此，我们说 $c$ 和 $a$ 在 $b$ 已知的情况下条件独立

对于 head to head 的图中，默认情况下，$a,b$ 是独立的，但是若 $c$ 被观测，$a,b$ 有关系：
$$
P(a,b,c)  =P(a)P(b)P(c|a,b)
$$
或者
$$
P(a,b,c) = P(a)  P(b|a)P(c|a,b)
$$
因此得到：
$$
P(b) = P(b|a)
$$
为什么知道 $c$ 以后，$a, b$ 反而不（条件）独立呢？这是因为，$c$ 是由 $a, b$ 导出的结果，在结果定下的情况下，$a, b$ 的随机性就丧失了

#### D-Seperation and Markov Blanket
![[Details about graph models 2023-04-04 09.53.39.excalidraw|300]]
我们补充一种情况：如图，如果 $d$ 和 $c$ 中的任意一个被观测，$a$ 与 $b$ 都不再独立
现在，我们给出判断两个集合是否具有条件独立性的方法：D-Seperation  ，实际上就是对上图的泛化
![[Details about graph models 2023-04-04 15.08.36.excalidraw]]
如图，如果我们有两个节点集合 $A, C$，$a\in A, c \in C$ 是 $A,C$ 中的任意节点，且对于任意节点 $b$，对于 Tail to Tail 和 Head to Tail 的情况，节点 $b$ 位于集合 $B$ 之内，否则位于集合 $B$ 之外，那么我们就说 $A,C$ 关于 $B$ 是条件独立的

在计算机中，判断 D-分离的方法是：
- 删除不在 $A, B, C$ 中的节点
- 删除 $B$ 中输出的所有边

此外，更直观的方式是使用 Moral Graph
- 找出有向图中的所有 V 型结构，在 V 型结构的两个父结点之间加上一条无向边；
- 将所有有向边改为无向边。

有两种特殊的条件独立性：
- 父节点已知，该节点与所有非后代的节点条件独立
- 给定一个节点的 Markov Blanket，则这个节点和网络中其他节点条件独立

注意：D-分离是判断条件独立的充分条件，而不是必要条件
那么我们推导
$$
\begin{align*}
P(x_{i}|x_{-i}) &= \frac{P(x_{i},x_{-i})}{P(x_{-i})} \\
&= \frac{P(x)}{\int P(x)dx_{i}}\\
&= \frac{\prod_{j} P(x_{i}|x_{pa(i)})}{\int_{x_{i} } \prod_{j}P(x_{j}|x_{pa(j)})dx_{i}}
\end{align*}
$$
通过这样的方式，你可以将与某一结点 $x_{i}$ 不相关的部分全部从分子、分母上同时约去，最终留下的是 $x_i$ 的父节点（在 $P(x_{i}|x_{pa(i)})$ 一项中）、$x_i$ 的子节点、$x_i$ 的子节点的父节点（在 $P(x_{ch(i)}|x_{i},x_{pa(i)})$ 一项中）。这就是说，一个节点与全图的关系可以简化成与其 Markov Blanket 的关系



### Application
一些典型的 BN 模型包括：
- 单一模型：朴素贝叶斯 $P (x|y) = \prod P(x_{i}|y)$
- 复杂模型：高斯混合模型
- 时序模型：Morkov Chain 、 Gaussian Proecess
- 带有时间的混合模型：HMM （离散的隐变量）、线性动态系统 LDS（连续的隐变量，例如 Kalman Filter）

## HMM 
HMM 的模型参数是 $\lambda = (\pi,A,B)$，其中，$\pi$ 是初始的概率分布和状态，$A$ 是状态转移 (Transision)矩阵，$B$ 是发射 (emition)矩阵，其中
$$
A = [a_{ij}] \ ,\ a_{ij} = P(i_{t+1}= q_{j}|i_{t}= q_{i})
$$
$$
B = [b_{j}(k)]\ ,\ b_{j}(k) = P(o_{t}= v_{k}|i_{t} = q_{j} )
$$
用自然语言来说，$a_{ij}$ 表征了状态 $i$ 转向状态 $j$ 的概率；$b_{jk}$ 表征了状态 $q_{j}$ 下观测变量取 $v_k$ 的概率

两个假设：
- 齐次 Markov 假设：无后效性，当前与历史无关
- 观测独立假设：观测的结果只依赖于目前的状态

三个要解决的问题：
- Evaluation：出现一个序列 $O = (o_{1},\cdots ,o_{t})$，它出现的概率多大？
- Learning：估计模型参数 $\lambda = \arg \max P(O|\lambda)$
- Decoding : 找到观测值背后的“原因”（隐变量）：$I = \arg \max P(I|O)$
	- 预测问题：已知观测序列，求 $P(i_{t+1}|O)$
	- 滤波问题：已知观测序列，求 $P(i_{t}|O)$

### Evaluation Problem
#### 公式推导
$$
\begin{align*}
P(O|\lambda) &= \\
&= \sum_I P(I,O|\lambda)\\
&= \sum_{I}P(O|I,\lambda)P(I|\lambda)\\

\end{align*}
$$
其中
$$
\begin{align*}
P(I|\lambda) &= P(i_{1},\cdots ,i_{T}|\lambda)\\
&= P(i_{T}|i_{1},\cdots,i_{T-1})P(i_{1},\cdots ,i_{T-1}|\lambda)\\
&= P(i_{T}|i_{T-1})P(i_{1},\cdots ,i_{T-1}|\lambda)\\
&= \pi(a_{i_{1}})\prod_{t=2}^{T} a_{i_{t-1},i_{t}}  
\end{align*}
$$
$$
P(O|I,\lambda) = \prod_{t=1}^{T} P(o_{t}|q_{t},\lambda) = \prod _{t=1}^{T} b_{q_{t}}(o_{t}) 
$$
从而
$$
P(O|\lambda) = \sum_{I}\pi(a_{i1})\prod_{t=2}^{T}a_{i_{t-1},i_{t}} \prod_{t=1}^{T}b_{it}(o_{t})
$$
这个算法有着指数级复杂度 $O(N^{T})$，是不可接受的。

#### Forward Algo
我们记 $t$ 时刻以及之前的所有观测变量和 $t$ 时刻的隐变量的联合概率记为 $\alpha_{t}(i) = P(o_{1},\cdots ,o_{t},i_{t}=q_{i}|\lambda)$ ，那么
$$
\alpha_{T}(i) = P(O,i_{t}= q_{i}|\lambda)
$$
那么
$$
P(O|\lambda) = \sum_{i}P(O,i_{T}= q_{i}|\lambda) = \sum_{i}\alpha_T (i)
$$
我们希望找到一个迭代公式来实现算法，于是
$$
\begin{align*}
\alpha_{t+1}(j) &= P(o_{1},\cdots ,o_{t},i_{t+1}=q_{j}|\lambda)\\
&= \sum_{i=1}^{N}P(o_{1},\cdots ,o_{t},i_{t+1}=q_{j},i_{t}=q_{i}|\lambda)\\
&= \sum_{i}P(o_{t+1}|o_{1},\cdots ,i_{t}=q_{i},\lambda) P(o_{1},\cdots o_{t},i_{t}=q_{i},i_{t+1}=q_{j}|\lambda)\\
&= \sum_{i} P(o_{t+1}|i_{t}=q_{i})P(o_{1},\cdots ,o_{t},i_{t}= q_{i},i_{t+1}=q_{j})\\
&= \sum_{i}P(o_{t+1}|i_{t}=q_{i})P(i_{t+1}=q_{j}|o_{1},\cdots ,i_{t}=q_{i},\lambda)P(o_{1},\cdots o_{t},i_{t}=q_{i}|\lambda)\\
&= \sum_{i}P(o_{t+1}|i_{t}=q_{i})P(i_{t+1}=q_{j}|i_{t}=q_{j},\lambda)\alpha_{t}(i)
\end{align*}
$$
由此，我们给出了递归式

#### Backward Algo 
我们也定义一个新的变量：
$$
\beta_{t}(i)=P(o_{t+1},o_{t+2},\cdots ,o_{T}|i_{t}= q_{i},\lambda) 
$$
边界条件：$\beta_{T}(i) = 1,\forall \ i$ 
你可以使用类似的方式推出：
$$
\beta_{t}(i) = \sum_{j}a_{ij}b_{j}(o_{t+1}) \beta_{t+1}(j)
$$

#### 一步概率和两步概率
$$
P(i_{t}= q_{t}|O ,\lambda) = \frac{\alpha_{t}(i) \beta_{t}(i)}{\sum_{j}\alpha_{t}(i)\beta_{t}(i)}
$$
$$
P(i_{t}= 1_{i},i_{t+1}= q_{j},O|\lambda) =
$$

### Decoding Problem 
![[Pasted image 20230411155412.png|600]]

![[Pasted image 20230411164653.png]]

## 无向图模型

### 基础知识和因子分解

### Logistic Regression 
定义：
$$
\phi(x_{q}|w_{q}) = \exp (w_{q}^{T}f_{q}(x_{q}))
$$
那么
$$
P(Y) =\frac{1}{Z} \prod  \exp (w_{q}^{T}f_{q}(x_{q}))
$$
两侧取对数得到：
$$
\log P(Y) = \sum w_{q}^{T}f_{q}(x_{q}) - \log Z
$$
这样的模型被叫做对数线性模型。Logistic 模型是一个典型的对数线性模型。

我们首先定义一个东西 (Sigmoid)的反函数
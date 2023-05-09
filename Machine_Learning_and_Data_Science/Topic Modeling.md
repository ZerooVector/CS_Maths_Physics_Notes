#MLorDS 
主题模型主要是从两个维度被分类（扩展）的：有监督 VS 无监督、层次化 VS 非层次化（主题数是一个超参数）

什么是**主题**？——对于机器来说，它将关注两个概率分布：**doc-topic（文档-主题）分布（一个文档可以有多个主题）；topic-word（主题-单词）分布**，其中，主题-词分布还可以反向看（一个主题下词的分布；一个词在不同主题下的分布）

一般来说，有两种观点看待主题建模：**文档表示** 和 **写作模拟**
写作模拟通常将文档生成的过程看作一个依照概率生成单词的过程：第一步是根据文档确定主题分布，第二类是根据主题分布确定单词

## 概率主题模型——LDA (Latent Dirichlet Allocation)

### 直观理解

也就是含有隐变量的狄利克雷分布模型
![[Topic Modeling 2023-03-07 15.41.06.excalidraw|600]]

我们假设有两箱骰子，第一箱是 doc-topic，第二箱是 topic-word
- 首先，从第二个箱子中抽取编号 $1\sim k$ 的 topic-word骰子
- 每次生成新的文章时，从第一个箱子中抽取一个 doc-topic 骰子 
	- 投掷 doc-topic 骰子，得到 topic 的编号 $z$
	- 投掷编号为 $z$ 的 topic-word 骰子，生成一个词

![[Pasted image 20230307155317.png|400]]

多项分布的参数 $\theta_m$ 服从 Dir 分布，依据多项分布可以生成文章的主题 $z_{m,n}$；另一个多项分布的参数 $phi_k$ 也服从 Dir 分布，依据文章的主题 $z_{m,n}$ 生成文章中的词


对于从 doc 到 topic 的生成，==对域每篇文章，会在多个 topic 张成的空间里面选择一个位置（这可能有问题）==，选定的这个位置就可以由 Dir 分布求出各个主题出现的可能性
![[Pasted image 20230307162259.png|300]]
对于从 topic 到 word 的生成，每个 topic 都在 word 张成的空间内对应一个点，这个点就可以根据 Dir 分布求出不同的词出现的概率
![[Pasted image 20230307161657.png|400]]

因此，每一个词的生成都历经了两次随机选择的过程：首先，依照概率随机选择主题，其次，根据主题抽词。
因为以上的操作都是独立的，因此，我们可以选择先抽取所有的主题，再根据所有主题抽取所有的词

![[Pasted image 20230307162553.png]]

$\theta_m$：第 $m$ 篇文档主题的分布
$N_m$: 第 $m$ 篇文档中的单词数目
$\phi_k$：主题到单词的分布

如果我们知道每个词的主题，我们就可以知道 doc-topic 分布，甚至可以知道 topic-word 分布

## LDA 模型的数学基础
### Gamma 函数
$$
\Gamma (x) = \int_{0}^{\infty} t^{x-1}e^{-t}dt
$$
性质：$\Gamma (x+1) = x\Gamma(x)$，$\Gamma (n) = (n-1)!$
### 多项分布
多项分布是从二项分布引申出来的：
$$
P(k=m) = C_n^mp^m(1-p)^{n-m}
$$
多项分布考虑了多种情况：
$$
P(X_i=m_{i})= C_{n}^{m_{1}}C_{n-m_{1}}^{m_{2}}\cdots \prod \mu_{k}^{m_{k}}= \frac{N}{m_1!m_{2}!\cdots m_{n}!}\prod \mu_{k}^{m_{k}}
$$
### Dir 分布
$$
Dir(\mu|\alpha) = \frac{\Gamma(\sum \alpha_{i})}{\prod \Gamma(\alpha_{i})}\prod \mu_k^{\alpha_{k}-1}
$$
在二维的情况下，显然我们有 $\mu_{2} = 1-\mu_{1}$，那么分布关于 $\mu_{1}$ 的图像是：
![[Pasted image 20230307164909.png|350]]
那么，拿抛硬币来讲，横轴就是扔出正面的概率，$\alpha$ 就是扔出正面的次数，$\beta$ 是扔出反面的次数。Dir 分布试图通过已有的事实 $\alpha_k$，估计一个随机数生成器中的参数 $\mu_k$ 是怎样分布的。

你可以把 Dir 分布写成这样的形式：
$$
Dir(\mu |\alpha) = \frac{1}{\Delta(\alpha)}\prod \mu_{k}^{\alpha_{k}-1}
$$
Dir 分布的期望
$$
\begin{align*}
E(p) &= \int [Constant]\times t \times t^{\alpha-1}(1-t)^{\beta-1} \\
 &=  \frac{\Gamma(\alpha+1)}{\Gamma(\alpha)}\times \frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha+\beta+1)}
\end{align*}
$$
因此，$k$ 维 Dir 分布的期望是：
$$
E(p) = [\frac{\alpha_{k}}{\sum \alpha_{k}}]
$$
### Bayes 公式
$$
P(A|B) = \frac{P(AB)}{P(B)} = \frac{P(B|A)P(A)}{P(B)}
$$
$P (A)$ 成为先验，$P(B|A)$ 是似然，$P(A|B)$ 是后验，$P(AB)$ 是联合，$P(B)$ 是证据
### Dir 多项共轭
可以证明：多项分布和 Dir 分布是共轭的，这使得它们相乘后的后验分布仍然是狄利克雷分布（简化形式：$\beta$ 分布和二项分布是共轭的，也就是说，$\beta$ 分布是用结果推导参数；二项分布则是用参数估计结果）
$$
Dir(\mu|\alpha) \times  Multi(m) = Dir(\mu|\alpha+m)
$$
（观察到事情发生了 $m$ 次，加入到 Dir 分布的参数中）

## LDA 的训练

先抽取了一个 doc-topic 骰子，投掷它很多次，生成文章的 topic 编号，那么，$\beta_{j}\sim Dir (\alpha), z_{i}\sim Mult(\theta_j)$
在第 $j$ 篇文章中，在参数 $\alpha$ 下，生成出主题 $z_{j}$ 的概率是：
$$
P(z_{j} |\alpha) = \frac{\Delta(m_{j}+\alpha)}{\Delta(\alpha)}
$$
其中，$m_{j}$ 是一个多维的向量（有几个主题就有几维），$m_{jk}$ 的意思是第 $j$ 篇文档中属于第 $k$ 个主题的词汇个数
在第 $i$ 篇文档中，在参数 $\beta$ 下，生成出单词 $w_{i}$ 的概率是：
$$
P(w_{k}|\beta ) = \frac{\Delta (n_{k}+\beta)}{\Delta (\beta) }
$$
其中，$n_{k}$ 也是一个多维的向量，$n_{kt}$ 是第 $k$ 个 topic 下面第 $t$ 个单词的个数

现在我们要估计参数：其中，$M$ 个参数为一组——每篇文章里面的各个类型的主题的词汇到底有多少？$K$ 个参数为一组——每个主题下面，每个单词出现的频率到底为何？

为了估计这两个参数，我们使用 Gibbs 采样算法

### Gibbs 采样
Gibbs 采样是 MC 的一个特例，其中心思想是：在采样时，每次冻结所有其他维度，只对一个维度上进行采样。例如，对一个 $n$ 维的随机变量进行采样：
![[Pasted image 20230314160740.png|400]]

在本模型中：
参照 [[Summary of LDA]] 中的讲解
每次改换词的颜色的过程，就是一个 Gibbs 采样的过程
考虑到：
$$
P(z_{jk}|\alpha) = \frac{\Delta (m_{jk}+\alpha)}{\Delta (\alpha)} \qquad  P
$$
















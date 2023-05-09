#MLorDS 

What is the core of ML?  - Tasks, Performances, Experiences
**Def** : Learning is a process through which the subject gains knowledge and increase his abilities. The inner behavior in the learning is gaining knowledge, accumulating experiences, and discovering rules; the outer manifestation of it is improving performance, fitting environment, and achieving self-perfection

Unknown environments and system construction

![[Pasted image 20230227105243.png]]


## 监督学习要学什么？
***表示、目标和优化***

监督学习学的是函数：一共可能有三种函数：point set/explicit/implicit

->Save solutions to problems and retrieve them when encountering the same problem
We try to learn a function: $f: X\rightarrow Y$,but we cannot always find a closed form of $f$

##### Example : Tic-Tac-Toe
最初的时候，评估一个局面的方法是，判断目前自己胜利的可能性减去对手胜利的可能性
例如，以下局面的评分都是 6-4=2
![[Pasted image 20230227110442.png]]

我们可以使用下面的搜索方式：对于每一步，思考其下一步，最大化自己可能得到的最小的收益 ($\max \min$)：
![[Pasted image 20230227110729.png|450]]

有什么可能的方法？ 多想几步？
把当前的状态和当前的估价函数存下来，相当于增加了搜索的深度：
![[Pasted image 20230227111313.png]]
具体估价函数如何设置，请参考强化学习[[Ep.1 Introduction to RL]]

## Def
Supervised Learning is a method which we **learn a function from examples**.
$f$ is the target function, and an example pair is $(x,f(x))$
Then, we find a hypothesis $h$, we should obtain that $h \approx f$ under a given training set.

Two key Prob:
- How to define the form of function?（定义这个函数）
- How to optimize its paras. And even structure?（优化这个函数）

##### Example : Curve Fitting
![[Pasted image 20230227112330.png|400]]
- 模型不能太复杂
- 数据不能太大，也要进行适当的清洗
***Ockham’s razor: prefer the simplest hypothesis consistent with data***

## A Discrete Function——Decision Tree
##### A Demo Problem : The Waiting Time of a Testaurant
![[Pasted image 20230227114049.png|450]]

==考点== 给定离散函数，看会不会使用决策树表达？你只需要使用很简单的函数。
![[Pasted image 20230227114721.png|400]]

在完成对于函数的表达后，问题转成一个最优化问题：在所有决策树中（搜索空间），找到最大化分类准确率的一棵（目标函数）
但是，这个问题的搜索空间太大：有 $2^{2^{10}}$ 个可行解，因此，我们必须使用启发式的优化算法：模拟决策树的生成过程。为了快速地生成决策树，我们可以在每次生成的过程中找到"Most Significant Attribute"。这里，我们使用信息熵来找到最快分类的属性。
信息熵被定义为：
$$
I(P(v_i)) = \sum_i-P(v_i)\log_2 P(v_i)
$$
对于我们这个二分类问题，
$$
I(\frac{p}{p+n},\frac{n}{p+n}) = -\frac{p}{p+n} \log \frac{p}{p+n} -\frac{n}{p+n} \log \frac{n}{p+n}
$$
对于每一次决策时，我们都来计算信息增益 (Information Gain)：
![[Pasted image 20230227120905.png|450]]

分类后的熵为每个节点上数据熵的加权求和，信息增益则是分类前的熵减去分类后的熵。

##### Another Example ：Play Tennis
##### 留做习题答案略，读者自证不难

### Overfitting of Decision Trees
![[Pasted image 20230306101319.png|350]]

目前，人们都会使用大量的数据来解决 Overfitting 的问题，但是无论使用了多么大的数据，目前都不能保证数据中没有噪声。因此，我们可以使用别的手段来预防 Overfitting:
- Stop growing the tree earlier, before it reached the perfect point.（训练集上，通过无限增大模型的复杂度，总可以使得准确率达到 100%）
- Post-prune 
注意：两种方式都需要定义新的优化目标。
实际上，我们需要在函数复杂度 (Function Complexity) 和训练精确度 (Training Accurancy) 之间找到一个平衡。一种目标是 Minimum Description Length（最小描述长度）：Explain the train data under decision tree. The tree with the shortest explanation is the best one.

### MDL 方法
$$
Description\ Length = Size\ of \ Hypothesis + Additional\ Cost
$$
![[Pasted image 20230306103743.png]]
我们需要对决策树的函数本身和不能被决策树解释的变量进行编码。编码的规则是：对树进行 DFS，“1”表示找到非叶节点，“0”表示找到叶节点，“P”代表分类为正，“N”表示分类为负，然后我们可以对这个字符串进行编码：
“1 Outlook 0 P 1 Humidity 0 N 0 P 1 Windy 0 N 0 P 1 Temperature 0 N 0 N 0 P“（这个字符串是从左侧比较复杂的树中提取得到的）

这里，“1”和“0”各需要 1bit 进行编码，“N”和“P”也个需要 1bit 进行编码，"Outlook"需要 $\log_2 4$ bit,"Humidity"需要 $\log_2 3$ bit，以此类推，所需要的编码长度是 24.585bit

如果使用了简单的树，我们需要对例外的数据进行编码：
![[Pasted image 20230306103808.png|400]]
我们需要指出异常数据在所有可能数据中的位置，所有可能的数据是 $3\times 3\times 2\times 3$ 种，因此需要 $\log_2 54$ bit 进行编码；如果再有一个错误，显然需要 $\log_2 53$ bit 进行编码，以此类推。

有两种优化的方法：第一是生成的时候就使得 MDL 最小；另一种方法则是从底端不断剪枝，直到 MDL 不再下降

## A Statistical Function——Bayesian Learning
According to Bayes's rule:
$$
P(h|D) = \frac{P(D,h)}{P(D)} = \frac{P(D|h)P(h)}{P(D)}
$$
$P(D,h)$ is called **Joint Probability**（联合概率）, $P (h)$ is called **Prior Probability** （先验概率）, and $P(h|D)$ is called **Posterior Probability**（后验概率），$P (D|h)$ is called **Class-conditional Probability**（类别条件概率）

Maximum A Posterior (MAP) Criterion is a process finding the most probable hypothesis:
$$
\begin{aligned}
h_{MAP} &= \arg \min_h P(h|D)\\
&= \arg \min_h P(D|h)P(h)
\end{aligned}
$$
直观上，是最大化 $h$ 类出现的先验概率与数据 $D$ 下 $h$ 出现概率的乘积（分母上是数据 $D$ 下出现所有类别的乘积，用于归一化，可以不用管）实际上，$h$ 可以变成函数中的参数，等等

##### Example : Cancer Dig
![[Pasted image 20230306110528.png|400]]
$$
P(cancer|+) = P(cancer ) \times P(+|cancer) = 0.0078 \ \ ,\ \ P(\neg cancer|+) = 0.0298
$$
实际上，在特征非常多的的时候，我们希望对模型进行一些简化（比如，计算联合概率时会相当复杂）。这些简化可能包括：
- 朴素贝叶斯分类器
- 贝叶斯信念网络
- 高斯混合模型：将若干个高斯分布加权组合

### Naive Bayesian Classifiers
核心：**假设变量的条件独立**
$$
P(D|h)=P(d_1,d_2,\cdots,d_n|h) = \prod_i P(d_i|h)
$$
这种情况下，你只需要统计假设 $h$ 出现的情况下，分量 $d_i$ 出现的概率。

##### Example : Junk Emails
找到 1000 篇文章，700 篇不喜欢，300 篇喜欢。现在你要统计所有的类别条件概率：
![[Pasted image 20230306112634.png|400]]

需要统计第 $i$ 个类别的前提下，在第 $j$ 个位置出现了词典里的第 $k$ 个单词的概率，但是这太大了，于是我们转而统计第 $i$ 个类别的前提下，出现了词典里第 $k$ 个单词的概率，忽略了位置信息。
以频率估计概率的时候，分子上+1，防止有未出现的词；分母上加上字典中词语的数目（这一项比较玄学，分母上的 $n$ 是这篇文章里面的总词数）

### Bayes Belief Networks
建立贝叶斯网络模型研究音乐家的相互作用 [[2021 D The Influence of Music]]

如果我们觉得朴素贝叶斯简化的太多了，那么我们还是让 $x_i$ 彼此相关，但是 $x_i$ 和 $y_i$ 却无关，由此，我们有了贝叶斯信念网络：
If X is Conditionally independent of Y given Z, then
$$
P(x_1,\cdots x_l|y_1,\cdots,y_m,z_1,\cdots z_n) = P(x_1,\cdots x_l|z_1,\cdots z_n)
$$
我们用一张图代表这个关系：
$$
P(x_1,\cdots,x_n) = \prod_i P(x_i |Parents(x_i))
$$
![[Pasted image 20230306114306.png|500]]

$$
\begin{aligned}
&P(S,B,L,C,T,F)\\
& = P(S)P(B)P(L|S)P(C|S,B)P(T|L)P(F|L,S,C)\\
& =
\end{aligned}
$$
那么，Campfire 的可能性与 S 和 B 有关，由上面的条件概率表所示。
这个东西仍然是使用统计计算得到的，例如，计算无暴风雨、有旅行团的情况下，点燃篝火的概率是 0.8，这是可以统计的。

##### Example 贝叶斯网络的决策过程
![[Pasted image 20230306115036.png|400]]

联合概率的计算：
$$
P(x_1,\cdots,x_n) = \prod_i P(x_i |Parents(x_i))
$$
展开成概率连乘 ：
![[Pasted image 20230306115441.png]]

基于 BBN 的统计推断：
利用边际概率：
$$
P(x|y)  =\alpha P(x,y) = \alpha \sum_z P(x,y,z)
$$
先利用边际概率增添不包含的变量：
![[Pasted image 20230306115954.png|500]]

再按照网络结构展开：
![[Pasted image 20230306120126.png|500]]

一些计算技巧：
![[Pasted image 20230306120203.png|400]]

先对 $a$（内层）求和，再对 $e$（外层）求和

#### Bayes 网络的学习过程
如果网络结构已知，那么学习是简单的：
- 如果网络中的变量完全被观测，那么只需要简单地统计
- 如果只有部分变量被观测
![[Pasted image 20230306120746.png|400]]
中间的灰色数据是无法直接得到的。我们设计一个算法：
- 目标函数：利用极大似然估计（在**统计模型**中是常用的），找到最合适的分布
$$
P = \prod P_W
$$
取 log，进行连加，得到最大似然估计的目标函数，使用梯度的方法不断提升目标函数
![[Pasted image 20230306121448.png|500]]
展开这个梯度：
![[Pasted image 20230313100902.png|500]]



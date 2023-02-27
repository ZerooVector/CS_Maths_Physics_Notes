#MLorDS 

What is the core of ML?  - Tasks, Performances, Experiences
**Def** : Learning is a process through which the subject gains knowledge and increase his abilities. The inner behavior in the learning is gaining knowledge, accumulating experiences, and discovering rules; the outer manifestation of it is improving performance, fitting environment, and achieving self-perfection

Unknown environments and system construction

![[Pasted image 20230227105243.png]]

## Supervised Learning
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

### Def
Supervised Learning is a method which we **learn a function from examples**.
$f$ is the target function, and an example pair is $(x,f(x))$
Then, we find a hypothesis $h$, we should obtain that $h \approx f$ under a given training set.

Two key Prob:
- How to define the form of function?
- How to optimize its paras. And even structure?

##### Example : Curve Fitting
![[Pasted image 20230227112330.png|400]]
- 模型不能太复杂
- 数据不能太大，也要进行适当的清洗
***Ockham’s razor: prefer the simplest hypothesis consistent with data***

### A Discrete Function——Decision Tree
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

#### Overfit of Decision Trees



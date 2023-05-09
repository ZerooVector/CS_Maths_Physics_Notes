#DL 

符号智能 (Symbolic AI)是一类基于先验知识的人工智能，它们主要关注 AI 的问题解决 (Problem Solving)和归因/知识推理 (Reasoning)的能力

>**Search**: With acceptable costs, find out an optimal or feasible solution in all the possible solutions of the problem.

我们需要考虑算法的完备性（是否能找到一个解）、最优性（找到的解有多好）、复杂度

## 搜索问题的表达 (Representation)

##### Example : Hanoi Tower
首先，我们需要表达所有的解。例如，我们可以表达所有盘片的位置：
![[Pasted image 20230410110728.png|300]]

之后，我们要定义“变化”的函数，例如，我们定义 $A(i,j)$ 代表将 A 盘从第 $i$ 根针移动到第 $j$ 根针上。
在完成定义之后，我们就有状态空间：
![[Pasted image 20230410110954.png|400]]
我们要搜索的解是从初始状态到最终状态的**一条路径**（一种解决方案）

在状态空间的表示中，我们需要表示所有的状态、所有的转移函数、代价、初始状态和目标状态

### 搜索问题的规约 (Reduction)
搜索问题的规约有两种做法：
- 转换成几个问题的“与”，解决全部的子问题后，原问题求解完成
- 转换成几个问题的“或”，解决一个子问题后，原问题求解完成
这样的规约可以使用与或图表示。与或图上的终端节点要么是显然的问题，要么是不可解的问题
**注意：与或图上的节点是问题，而不是状态，与或图表达的是对问题的分解过程，其基本思想不是考虑状态转移的轨迹，而是考虑如何将原问题分解到足够简单的子问题**

>与或图的使用方式：
>- Step1. Represent each problem 
>- Step2. Reduce the problem and represent the reduction process using and/or graph 
>- Step3. Backtrack from end nodes to the root node, labeling nodes solvable or unsolvable 
>- Step4. Output the corresponding solution graph if the root node is labeled solvable

例如，一个 $n$ 阶的汉诺塔可以分解为两个 $n-1$ 阶的汉诺塔问题，只要解决两个低阶子问题，就可以解决原问题（递归）
![[Pasted image 20230410112222.png|400]]

## 图搜索方法 (Graph Search)
最基本的方法中，你需要 open 表和 close 表记录图上的节点。例如，广度优先搜索
![[Pasted image 20230410115520.png|400]]

盲目的搜索算法主要包括：
- 广度优先
- 深度优先
- 深度限制搜索
- 迭代加深搜索

### 启发式方法（A-star 算法）
A-star 算法用于求解状态空间图上的搜索问题，它是 Dijkstra 算法的一种改进。它使用一个“估价函数”
$$
f(n) = g(n)+h(n)
$$
其中，$g (n)$ 是已经发生的代价，而 $h (n)$ 是估算的未发生的代价。如果 $g(n)=0$，算法变成了一个“短视”的贪心算法，如果 $h (n)=0$，算法退化成 Dijkstra 算法。
例如，在搜索地图上的最短路径时，我们使用两个城市的直线距离作为启发式信息。
- 在 $h(n)$ 一定小于实际代价时，A-star 算法保证找到最优解，并且 $h (n)$ 应该尽可能接近真实值！
- 在 $h (n)$ 大于实际代价时，A-star 算法不一定找到最优解,

A-star 算法每次扩展 open 表中估价函数最小的节点，直至目标节点被放入 close 表为止。
![[Pasted image 20230410121621.png|400]]

例如，在华容道小游戏中，我们可以使用错误放置的方块个数，或者当前解与目标解之间的距离。再举一个例子，在游戏 AI 寻路的过程中，可以使用曼哈顿距离作为启发式估价函数

## 博弈搜索
我们现在考虑一些运行在完全信息的序贯零和博弈上的搜索算法。

我们首先考虑一个简单的小游戏：有一堆钱币，两人分别从目前的钱币中选择一堆，将其分成数目不等的两部分，直到游戏无法进行为止。我们使用 MIN 和 MAX 代表两个玩家
![[Pasted image 20230417102710.png|400]]
显然，在自身做决策时，子问题和原问题是 OR 关系（只要做出其中一个决策能赢就可以了）；在对手做决策时，子问题和原问题是 AND 关系（无论对手做出何种决策，我都必须要赢）。因此，这是一张 AND-OR 图。容易分析，由于 (2,2,1,1,1, MIN)对 MIN 是不可解的，那么 (3,2,1,1, MAX)也不可解，那么 (4,2,1, MIN), (3,3,1, MIN)都不可解，从而第二行的所有状态均不可解。因此，先攻的 MIN 实际上是落下风的。

通过这种方式，理论上我们可以求解任意的博弈问题。但是，实际中的博弈问题规模太大。因此，我们通常使用限制树的深度、使用估价函数的方式解决实际问题。

### 最大最小化算法
![[Pasted image 20230417104028.png|400]]

在对手决策时，我们应该认为对手是很强的，因此我们考虑最差的情况（AND）；而当我们自己走棋时，我们则可以选择最好的情况（OR）。

##### Example 求解 tic-tac-toe 问题
我们设计的估价函数是胜利的可能性 - 失败的可能性，但实际上，这个估价函数可以由前馈神经网络表达。显然，搜索的深度可以是无限深的。到达限定的深度后，我们就必须使用评估函数。
![[Pasted image 20230417105708.png|400]]

### $\alpha-\beta$ 剪枝
我们没必要将所有的分支都展开，我们可以只展开对结果可能有影响的。给两个例子：
![[Pasted image 20230417110210.png|400]]

![[Pasted image 20230417110832.png|400]]

**剪枝的根本原则是剪去的东西不能删去更好的解，根据这个原则不断剪枝即可**

### MCST
基本原理是：对于最后一层的叶节点不进行评估，而是随机地进行游戏，模拟多次，看这个节点上的胜负。
>- Selection: a child selection policy is used from the root to reach the most urgent expandable node 
>- Expansion: child nodes are added to expand the tree 
>- Simulation: run from the new nodes according to the default policy to produce and outcome 
>- Backpropagation: the simulation result is backed up to update the statistics of nodes

![[Pasted image 20230417112120.png|400]]
![[Pasted image 20230417112205.png|400]]

在评估节点时，我们会使用一个叫做 UCB 的量。

##### Example  Alpha-Go 中的原理
Alpha-Go 实际上是一个非确定策略的强化学习，它希望学习 $P(action|state)$ ，方法是模仿专家下棋的模式，以及通过自我对弈的方式提升。此外，Alpha-Go 使用了评估函数。
- 在第一部分中，Alpha-Go 试图使用极大似然估计来更新策略网络，从而模仿专家的策略
- 在第二部分中，训练一个 Policy-Network，使用 Policy-Gradient 的方法
- 在第三部分中，训练一个 Value-Network，使用估价和胜率的 MSE 作为目标函数，优化估价网络

- Policy-Network 用来缩小搜索的宽度，不考虑概率太低的策略
- Value-Network 用来缩小搜索的深度，直接评估价值，不用搜得太深













#OPTandOR 

## 多目标优化基础 
- 支配 (Dominate)
- 非支配集合：对于一个集合 $P$，它的非支配集合是 $P$ 的子集，包含所有不被 $P$ 中其他的解所支配的解
- 可行域中的非支配集合称为 Pareto 最优集合 (Pareto-Optimal Set)
- 多目标优化希望找到的解要尽可能地找到 Pareto 前沿

## Method 1: 加权求和法
![[Pasted image 20230504154254.png|500]]
显然，我们只要对不同的目标施加不同的权重：
$$
\min \sum_{i} w_{i}f_{i}
$$
##### 情况 1：目标函数值空间是凸集
![[Pasted image 20230504154813.png|350]]
对于 Pareto front 上的每一个点，总能找到一个权重向量 $\vec w$ 与之对应

##### 情况 2 ：目标函数值空间是非凸集
![[Pasted image 20230504155311.png|350]]
这是，我们发现我们无法找到 Pareto Front 上的所有解。这是因为我们的目标都是线性的，然而一些非线性的目标，例如 $f_{1}^{2}+3f_{2}$ 被忽略了

## NSGA-II Algo (带有精英保留策略的快速非支配多目标遗传算法)
### 三个筛选机制
- 支配深度 (Dominace depth)：一层一层地选择 Pareto 最优解
![[Pasted image 20230504155942.png|500]]




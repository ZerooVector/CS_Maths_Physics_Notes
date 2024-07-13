#RL 

我们的问题可以被展开成一个序列：$s_{0}, a_{0}, r_{0}, s_{1}, a_{1}, r_{1},\cdots$ ，这个序列构成一个随机过程。在 RL 领域中，我们将这个序列称为一个 trajectory。我们有两个假设：
- Stationary Assumption ：系统的动力学规律不随着时间变化（时不变系统），可以表达为：
$$
P(s_{t}|s_{t-1}) = P(s_{t}' | s_{t-1}')
$$
- Markov Assumption：系统的目前状态只依赖于之前的几个状态。一阶马尔可夫过程：
$$
P(s_{t}|s_{t-1},s_{t-2},\cdots) = P(s_{t}|s_{t-1})
$$
我们需要选择合适的 state，使得 Markov 假设得到满足。

- Markov 过程的推断、转移矩阵

## Markov Decision Process 
奖励函数可以被定义在 $\mathbb{S}\times \mathbb{A}$ 上：
$$
r(s,a) = \mathrm{E} [R_{t}|S_{t-1} = s, A_{t-1} = a]
$$
也可以被定义在 $\mathbb{S}\times \mathbb{A}\times \mathbb{S}$ 上：
$$
r(s,a,s') = \mathrm{E}[R_{t}|S_{t-1} = s,A_{t-1} = a,S_{t} = s']
$$
我们的目标是最大化长期回报。通常来说，我们最大化 Discounted Rewards：
$$
R_{d}= \sum_{t}\gamma^{t} R(s_{t},a_{t})
$$

我们定义一个策略 (policy)是 $\mathbb{S} \rightarrow \mathbb{A}$ 的映射 $\pi(s_{t})$ 。

为了评估我们的决策是否有效，我们可以给出一个状态 $s_{0}$ 的价值，这个价值等于我按照既定策略 $\pi$ 进行决策，最终获得的收益期望：
$$
V^{\pi}(s_{0}) =  \sum_{t=0}^{h} \gamma ^{t}  \sum_{s_{t}}  P(s_{t}|s_{0},\pi) R(s_{t},\pi(s_{t}))
$$
我们从固定的状态 $s_{0}$ 开始，要评估各个策略的优劣，我们只需要找到使得上式取值最大的概率 $\pi^\star$，就是最优策略。因此，我们将比较策略优劣的问题转换为数值比大小的问题。

## Policy Optimization 
我们考虑最后一步，显然，我们只需求解一个简单的最优化问题：
$$
V(s_{N}) = \max_{a}   R(s_{N},a_{N})
$$
那么我们可以考虑向前一步。显然，我们已经解决了一个子问题，因此：
$$
V(s_{N-1}) = \max_{a} R(s_{N-1},a_{N-1}) + \gamma \sum_{s_{N}} P(s_{N}|s_{N-1},a) V(s_{N})
$$
这样，如果我们预先确定了系统的动力学模型，我们就可以理论上找到每一步的最优策略。这就是 Bellman 方程。

对于 Finite Horizon 的情况，只要我们的动力学模型已知，我们就可以提前计算好整个序列上的策略，然后我们获得一个开环的动作序列；对于 Infinite Horizon 的情况，我们可以不断向前迭代，直到收敛，然后我们获得一个闭环的策略。在强化学习里面，我们可以将这种收敛简单的解释为 $\gamma^{n}$ 会收敛。










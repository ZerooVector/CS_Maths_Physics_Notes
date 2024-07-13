#RL 

在强化学习中，最大的问题是**模型未知** ，我们需要先学到系统的动力学和奖励模型。（真的需要学吗？）
- Model ： $P(s'|s,a),P(r|s,a)$ 
- 强化学习可以有对环境和奖励的显式建模 (Model-Based)，也可以没有 (Model-Free)
- Value-Based：需要计算每个状态的 Value Function，并找到最优的状态；Policy-Based：只优化 Policy 


### Model Free Evaluation 
为了在模型未知的情况下评估策略的优劣，我们有一些方法：
- Monte Carlo Evaluation:
$$
V^{\pi}(s) =   E_\pi\left[\sum_{t} \gamma^{t} r_{t}\right] \approx \dfrac{1}{n(s)} \sum_{n(s)} [\sum_{t} \gamma^{t} r_{t}]
$$
它的意思是，我们从状态 $s$ 向外采样 $n(s)$ 条轨迹，取这些轨迹上的奖励的平均值。
- TD Evaluation : 根据 Bellman Equation 的定义：
$$
V^{\pi}(s) = \mathrm{E}[r|s,\pi(s)] + \gamma \sum_{s'}  P(s'|s,\pi(s))  \approx r + \gamma V^\pi(s')
$$
我们定义：
$$
G_{k} = \sum_{t} \gamma^{t} r_{t}^{(k)}  
$$
我们展开 Monte Carlo Evaluation 的表达式，显然可以看出：
$$
V^{\pi}_{n}(s) = V_{n-1} ^{\pi}(s) + \dfrac{1}{n(s)} (G_{n(s)} -  V_{n-1}^{\pi}(s))
$$
我们通常也会记一个“学习率” $\alpha_{n}  = \dfrac{1}{n(s)}$，然后它看起来就很像某种学习算法。我们不加证明，不加推导地把这个公式应用到 TD 上：
$$
V_{n}^{\pi}(s) = V_{n-1}^{\pi}(s)  + \alpha_{n} (\gamma V_{n-1}^{\pi}(s')  + r  - V_{n-1}^{\pi}(s) )
$$
这个算法收敛的条件是：
$$
\sum_{n} \alpha_{n} \rightarrow \infty   \quad \sum_{n}(\alpha_{n})^{2}  \rightarrow M
$$
通常，我们就会选择 $\alpha_{n} = \dfrac{1}{n(s)}$，$n(s)$ 是状态 $s$ 被历经的次数

Monte Carlo 是一个 Unbiased Estimate，但是 TD 不是。

## Q Function 
我们考虑 Bellman 方程的右侧，我们将本步奖励+后续价值记为“动作价值函数”：
$$
Q^\pi(s,a) = E[r|s,a] + \gamma \sum_{s'} P(s'|s,a) V^\pi(s')
$$
注意到：
$$
V(s)  = \max_{a}Q(s,a)
$$
我们显然需要执行 $Q^{\pi}(s,a)$ 最大的动作。我们可以类似写出有关 $Q(s,a)$ 的 Bellman 方程：
$$
Q(s,a) = \mathrm{E}[ r(s,a) + \max_{a} Q(s',a') ] 
$$
（推导过程：将 $Q^{\pi}(s,a)$ 的右侧展开即可）



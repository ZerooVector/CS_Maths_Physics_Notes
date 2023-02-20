Chiliu@bit.edu.cn
13718763223

# Evaluation System 
Attendance : 40%
Experiment : 60%
Bonus : 10%

# Introduction to RM
## RL 的特点
- 没有监督信号，只有奖励反馈
- 反馈具有延迟性
- 动作会影响后续数据
- 是一个与时间序列相关的序贯决策过程

## 算法分类
- Model Free：状态转移概率未知 / Model Based ： 状态转移概率已知，在现实中，由于状态太多了，通常是 Model Free
- Policy-Based: 输出动作的概率分布 / Value-Based：输出未来的期望价值
- MC-update ：游戏回合结束才更新 / Temporal-Diffence update：单步更新
- On policy : 同步探索环境和更新策略 / Off policy ：探索环境和更新策略是异步的，今日的前沿是On Policy

## RL 方法的三个部分
- State : 尽可能准确地描述外界的环境，尽可能地包含充足的信息（尤其是时序信息），
- Action : 离散/连续
- Reward : 仅仅代表 Agent 在当前时刻的表现，Agent 的任务是最大化累计奖励。

- **Reward Hypothesis**： 所有的任务目标都可以用最大化期望奖励描述
- 需要注意的是，某些任务的奖励是稀疏的

由 $s, a, r$ 组成的序列称为 History:
$$
H_t= s_1,a_1,r_1,...,s_t,a_t,r_t
$$
于是，
$$
a_{t+1} = f(H(t))
$$

# 马尔可夫性和马尔可夫过程
马尔可夫性假设说明，下一时刻的状态仅仅与目前状态有关（历史都是可以抛却的）：
$$
P(s_{t+1}|s_{t}) = P(s_{t+1}|s_1,\cdots s_n)
$$
马尔可夫过程要求一个有限状态集合 $S$，和转移概率矩阵 $P$，其中，$P_{ij}$ 代表从状态 $i$ 转向 $j$ 的概率



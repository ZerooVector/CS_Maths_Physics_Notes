#DL 

对于一个 Weak AI :
- Situatedness
- Autonomous
- Proactive 
- Reactive
- Social Ability
对于一个 Strong AI :
- Belief
- Desire
- Intention
- Knowledge
- Etc
(BDI 模型)

强化学习任务的特性：
- 没有人告诉模型“对了”或者“错了”（延迟奖励）
- 探索环境并从经验中学习

## Markov Decision Process
对于一个 RL Agent ，它将走出一条轨迹：$s_{0}, a_{0}, r_{0}, s_{1}, a_{1}, r_{1},\cdots$ 
- 状态转移模型 $T(s,a,s')$
- 奖励 $R(s)$
- 策略 $\pi (s)$ 或者 $\pi(s,a)$ 
学习的对象是 $\pi(s,a)$  ，学习的目标是最大化累计（长期）奖励
我们描述长期奖励的方式是 Discounted Reward，也就是：
$$
V^{\pi} (s_{t}) = \sum_{i} \gamma^{i} r_{t+i}
$$
两个重要的函数：状态价值函数 $V^{\Pi}(s)$，动作价值函数 $Q^{\Pi}(s,a)$，二者有关系：
$$
V(s) = \mathrm{E}[ Q(s,a)] 
$$
强化学习的终极目的是求解 Bellman Equation：
$$
V^{\star}(s) = \max_{a} \left(R(s,a) + \gamma \sum_{s'} T(s,a,s') V^{\star}(s')\right)
$$
因此，我们只要找一个策略，使得所有状态的状态价值函数都达到最大值即可，也就是
$$
\pi^{\star} (s)  \Rightarrow  V^{\star}(s) = \max_{\pi}  V^{\pi}  (s)
$$
根据 Bellman 方程，选择动作即可
![[Pasted image 20230605102326.png|400]]

## Q-Learning 

实际上，我们无从得知 $f_{s}$ 和 $f_{R}$，所以我们把中间的函数记为 $Q$ 函数
![[Pasted image 20230605103022.png|400]]
![[Pasted image 20230605103326.png|400]]
Q-Learning 可以解决走迷宫等搜索问题（本来是使用符号智能解决）

## TD-Learning （时序差分学习）
TD-Learning 的作用是使得模型可以单步更新，否则模型只能在最后一刻更新
![[Pasted image 20230605105335.png|400]]

==GPT== 
时序差分学习（Temporal Difference Learning，简称 TD 学习）是一种结合了动态规划（Dynamic Programming）和蒙特卡洛方法（Monte Carlo Methods）的强化学习算法。它既可以处理完全观察到的环境，也可以处理部分观察到的环境。TD 学习的核心思想是使用当前时刻和未来时刻的价值估计来更新价值函数。

时序差分学习的基本形式是TD(0)。在TD(0)学习中，我们使用以下公式进行价值函数的更新：

$$  
V(s_t) \leftarrow V(s_t) + \alpha [r_{t+1} + \gamma V(s_{t+1}) - V(s_t)]  
$$

其中：

- $V(s_t)$ 是状态 $s_t$ 的价值估计。
- $\alpha$ 是学习率（Learning Rate），用于控制智能体在每次迭代时对新信息的接受程度。
- $r_{t+1}$ 是智能体在状态 $s_t$ 采取某个动作后得到的即时奖励。
- $\gamma$ 是折现因子（Discount Factor），用于衡量未来奖励的相对价值。
- $V(s_{t+1})$ 是状态 $s_{t+1}$ 的价值估计。

TD学习的关键在于它使用了时序差分误差（Temporal Difference Error）来更新价值函数。这个误差是由预测的未来状态价值与当前状态价值之间的差值（考虑折现因子和即时奖励）组成的。通过反复迭代，TD学习可以逐渐修正智能体对状态价值函数的估计。

Q-Learning 和 SARSA（State-Action-Reward-State-Action） 算法都是基于时序差分学习的方法。它们分别用于学习动作价值函数（Action Value Function），而不是状态价值函数。这些算法可以应用于许多强化学习问题中，从而帮助智能体学习到一个优秀的策略。

## DRL
### Policy - Gradient 



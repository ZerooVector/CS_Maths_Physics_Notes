#RL 

我们现在希望直接给出一个动作 $\pi_{\theta} (a|s)$，那么，我们可以利用 Softmax 函数：
$$
\pi_{\theta}(a|s) = \dfrac{\exp(h(a,s;\theta ))}{\sum \exp (h(a,s;\theta ))}
$$
我们可以使用任何方法来求解 $h(a,s;\theta)$ 。注意：这里我们已经抛去了值函数的概念，我们只希望通过一组参数 $\theta$ 构造出策略。因此我们希望直接学习 $\theta$ 。
如果动作是连续的，那么我们会以如下方式建模：
$$
\pi (a|s) = N(a|\mu (s;\theta),\Sigma(s;\theta ))
$$

我们回顾之前 Supervised Learning 中的方法。假定我们可以收集专家轨迹中的一些 $(s_{i},a_{i}^{\star})$，那么我们希望进行训练，使得我们的模型尽可能地靠近专家轨迹，我们需要做 MLE：
$$
\theta^{\star}= \arg \max_{\theta} \sum \log \pi_{\theta} (a_{i}^\star|s_{i})
$$
梯度上升过程是：
$$
\theta  \leftarrow  \theta + \alpha \nabla_{\theta} \log \pi_{\theta} (a_{i}^{\star}|s_{i})
$$
这实际上就是模仿学习。

### Reinforce 
现在，我们无法采样到专家轨迹，而是采样到了 $(s_{i},a_{i},r_{i})$ 序列。现在的目标是：
$$
\theta = \arg\max_{\theta} \sum_{i} \gamma^{i} \mathrm{E}_{\theta} [r_{i}|s_{i},a_{i}]
$$
也就是最大化累计折扣奖励。我们首先直接指出，其更新公式为：
$$
\theta \leftarrow  \theta  + \alpha \gamma^{n} G_{n} \nabla_{\theta}  \log \pi_{\theta}(a_{n}|s_{n})
$$
其中 $G_{n}$ 是从第 $n$ 步开始的折扣奖励。

这里我们直接引入 Stochastic Gradient Policy Theorem 
$$
\nabla V(\theta ) \propto  \sum_{s} \mu_{\theta}(s) \sum_{a} \nabla \pi_{\theta}(a|s) Q_{\theta}(s,a)
$$
这个是很符合直觉的。


## Actor-Critic ：融合 Policy-Based 和 Value-Based
对于上面的定理，我们显然可以引入一些不会引起梯度的项。那么：
$$
\nabla V(\theta ) = \sum_{s}  \mu_{\theta} (s) \sum_{a} \nabla \pi_{\theta} (a|s) (Q_{\theta}(s,a) - b(s))
$$
Reinforce 中的 $G_{n}$ 就是通过一次采样，对 $Q$ 函数进行的一次估计。我们现在希望使得 $G_{n}$ 的估计更加准确，而不只是通过一次采样来估计。那么简单的一个想法是构造一个 Advantage Function：$A (s, a) = Q (s, a) - V^{\pi}(s)$ 。这个情况下，（经验地）算法收敛更快。因为 $A(s,a)$ 的方差可能更小一些。  

还有另一种方式。既然现在我们已经有了 $V$，那么我们可以直接使用 $r_{i}+ \gamma V(s_{i+1})$ 来代替 $G_{i}$ 这个算法可以减小方差。这个情况下，我们就可以进化到 AC 算法：**专门使用一个网络估计 $V$ 值，另一个网络产生策略**









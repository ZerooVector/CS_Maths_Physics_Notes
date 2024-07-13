#RL 

在前一节中，我们提到了 Policy Evaluation 使用的算子和 Policy Improvment 使用的算子，我们可以将这两步操作结合起来。我们使用几步 Policy Evaluation 和一步 Policy Improvement 。 

##### 引理 1 
在引理 1 中，我们将证明：策略迭代将使得策略单调提升。也就是说，对于两次策略迭代得到的状态价值函数 $V^{i},V^{i+1}$，我们有：
$$
V^{i+1} \ge V^{i} 
$$

##### 定理 1 
可以证明，在 Policy Iteration 运行足够多次时，策略和值函数将收敛到最优值


所以，我们有两种求解 MDP 问题的方法：
- 进行 Value Iteration，并根据状态值函数得到策略
- 进行 Policy Iteration，并直接得到最优策略

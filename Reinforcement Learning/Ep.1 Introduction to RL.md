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
- MC-update ：游戏回合结束才更新 / Temporal-Diff update：单步更新
- On policy : 
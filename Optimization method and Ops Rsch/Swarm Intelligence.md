#OPTandOR 

## Ant Colony Optimization 
基本思想：蚂蚁是通过信息素 (Pheromone)进行通信的。某路径的信息素浓度越高，该路径被选择的概率越大！
![[Pasted image 20230423155514.png|600]]
![[Pasted image 20230423161058.png|400]]

### 改进：基于排序的蚁群系统
![[Pasted image 20230423161706.png|500]]

这个算法也可以用于求解类似的问题。例如背包问题。但是需要将其他问题转化成一个图上的问题。

## Particles Swarm Optimization
总体思想：结合个体经验和群体经验
![[Pasted image 20230423164034.png|600]]

其中，惯性是探索 (Exploration)，其余两项都是利用 (Exploitation)

粒子群优化可以解决聚类问题。典型的目标函数是最小化离差平方和：
$$
\min \sum_{j}\sum_{x_{i}} ||x_{i}-\mu_{j}||^{2}
$$
实际上，可以将多个类的中心编码到一个粒子。

一些变式：
- Gbest 换成 Lbest ：每个粒子只能得到附近的粒子的信息
- 离散变量：

--- 
--- 


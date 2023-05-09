#OPTandOR 

## 线性规划的定义
线性规划要求目标函数和约束条件都是线性的！
初步地，我们可以将线性规划写成下面这个标准形式：
$$
\begin{aligned}
\min & \quad a_0^Tx + b\\
\mathrm{s.t.}&  \quad a_i^Tx+b_i \leq 0\\
& \quad d_j^Tx+c_j=0\\
\mathrm{var.} & \quad x
\end{aligned}
$$
但是，线性规划可以写成标准形式：
$$
\begin{aligned}
\min & \quad c^Tx\\
\mathrm{s.t.}&  \quad Ax=b \\
\mathrm{var.} & \quad x \geq 0
\end{aligned}
$$
这是因为我们引入了松弛变量。
![[Pasted image 20230302171119.png|450]]

同时，为了使得所有的变量都大于 0，我们还可以引入人工变量。
![[Pasted image 20230302171243.png|450]]

## 线性规划的例子
### 直接依赖自然语言建模获得线性规划问题
![[Pasted image 20230302171412.png|450]]

### 产销平衡的货物调度问题
![[Pasted image 20230302171617.png|450]]

### 排班问题
![[Pasted image 20230302171727.png|450]]

### 混合策略纳什均衡
![[Pasted image 20230302172654.png|450]]

### 选址问题（将非线性规划问题改写成线性规划问题）
例如，我们需要
$$
\min |x-3|
$$
那么我们可以转成
$$
\min u \ ,\ u\geq x-3\ ,\ u\geq 3-x
$$
## 求解线性规划的算法
### 单纯形法


Obsidian 黑曜石
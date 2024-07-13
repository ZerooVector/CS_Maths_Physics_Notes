#DL 
- Interlligent collective behavior , emerge and self-organization   
##### Example ： 鸟群的飞行规则
- Seperation ：避免局部的密度过高
- Alignment ： 所有鸟的方向一致
- Cohesion： 所有鸟希望走到群体的中心

##### Composition of SI 
- Agents : Can interact with the world and each other 
- Simple behaviors 
- Communication between of Agents 

## Communication
- 直接的交流：定义 Agent Conmmunication laguage
- 非直接的交流：Signals, BlackBoard System
- 

## ACO
蚁群算法中的交流是信息素


## PSO 
假定每一个粒子都在寻找最优解，粒子群算法主要关注如何更新每个粒子的速度，从而达到探索和利用的平衡。在 PSO 中，每一个粒子的位置携带着可能的最优解（利用），而速度则导致位置的变化（探索）
- $pBest$：自己找到的最优值
- $gBest$：群体最优值
- $lBest$：局部最优值
![[Pasted image 20230529102650.png|450]]

例如，我们在一个凸函数上面来展示这样的算法：
![[Pasted image 20230529103050.png|400]]

在实际应用中：
- 惯性系数可以随着时间降低
- 控制最大速度
- PSO 是一种带动量的算法

## Quantum Calculating 
量子计算机的作用是超大的并行存储能力。对于 $n$ 个量子比特，它可以**同时**存储 $2^{n-1}$ 个值。此外，两个量子比特是可以通过纠缠 (Entanglement)进行超距的作用。可以用于模运算、傅里叶变换、大数的质因数分解等等。
我们举一个例子：例如，我们要对 15 进行质因数分解，我们可以构造一个函数：
$$
F(a) = x^{a} \mathrm{mod} N
$$
其中 $x$ 是一个与 $N$ 互质的数。求出该函数的周期，就可以进行质因数分解。
- 选择一个整数，使得 $N < q < 2^{N}$，例如，我们选择 256
- 选择与 $N$ 互质的数，例如，我们选择 7
- 选择两个寄存器，使得它们纠缠在一起：输入寄存器需要足够存储 $q-1$，而输出寄存器需要存储 $N-1$。这种纠缠中反映了上面 $F(a)$ 的函数关系

- 现在，输出寄存器应当是 1，4，7，13 的叠加。
- 我们对输出寄存器进行观测。例如我们观测到 1，则输入寄存器也会“坍缩”，此时输入寄存器是一些周期性的数字的叠加
- 进行一些量子傅里叶变换，得到这种频率特性
#RL 

## Review of Deterministic OC 
- Linear Problems or "Local" Control Problems（例如倒立摆）
- 对于无约束问题：LQR（时变/TV LQR、时不变/TI LQR）
- 对于有约束问题：MPC
	- 若约束是线性的：QP 
	- 若约束是锥：SOCP（二阶锥规划）


- 如果出现了非线性问题：
- DDP 
- 直接配点（DIRCOL）
注意：DDP 中真正地使用了动力学方程，但是 DIRCOL 中我们将动力学方程作为约束对待。DDP 难以添加额外约束，但是 DIRCOL 很容易添加额外约束，并使用增广拉格朗日方法解决。在实际中，DDP 通常运行得很快，适合在嵌入式系统上实施；DIRCOL 常常用于离线设计轨迹，特别是在 Horizon 很长并且有着复杂约束的时候。
另外有一种方法叫做 Multiple Shooting，这大概是在将轨迹切成几段，在每一段上进行 DDP Rollout，然后使用约束将这几段轨迹连接在一起。


## Description of Rotation
之前，我们可能使用欧拉角来描述转动，但是这其实有一些弊端。例如万向节死锁。我们首先指出，我们现在研究的旋转通常是在一个惯性坐标系（使用 $x^{N},y^{N},z^{N}$ 表示）和一个刚体的本体坐标系 S（使用 $x^{B},y^{B},z^{B}$ 表示）之间的旋转。也就是说，这个旋转是：
$$
v^{N} = Qv^{B}
$$
这个旋转有三个自由度，但是很不幸的是我们无法使用全局无奇异点的三个参数来描述它。

### Rotation Matrix / Direction Cosine Matrix
可以证明，一个旋转矩阵由三个互相正交的单位列（行）向量组成，它们是一组正交基。显然，该旋转矩阵是正交矩阵。由于该矩阵的变换是保范数的，因此其行列式为 1. 
对于这样的一类矩阵，我们称 $Q \in SO(3)$ 

### Kinematics 
我们希望求出刚体上某点的运动。那么：
$$
x^{N} = Q(t) x^{B}  \quad  \dot x^{N} = \omega^{N} \times x^{N}  = Q(t)(\omega^{B} \times x^{B})
$$
又因为
$$
\dot x^{N}= \dot Q x^{B} + Q \dot x^{B} = \dot Q  x^{B}
$$
那么:
$$
\dot Q x^{B} = Q(\omega^{B }\times x^{B}) 
$$





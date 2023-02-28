#MLorDS 
***目的：一种基于极大似然估计，求解未知模型中参数的算法***

## Maximum Likelihood Estimator
Likelihood 是一个关于模型参数的函数。在数值上：
$$
L(\theta) = P(x|\theta)
$$
但是，似然是给定 $x$ 后，关于 $\theta$ 的函数
极大似然估计的先决条件是给定数据集 $x$ 中数据的分布！

## EM——如果数据分布未知，应该怎么做
### Jensen 不等式
对于凸函数
$$
E[f(x)] \geq f(E[x])
$$
进一步地，如果 $f$ 严格凸，那么取等条件：
$$
P(X=E[x]) =1
$$
### 极大似然估计到 EM 算法
我们在传统的 MLE 中引入一个参数 $z_i$，控制这组数据满足的分布：
$$
\theta^\dagger,z^\dagger_i= \arg \max \sum_i \log(p_i(x|\theta,z_i))
$$
这里的 $z_i$ 是我们人为引入的变量，称为 Hidden Variable。
实际上，我们可以选择不同的 $z_i$，我们要把一个样本选择不同 $z_i$ 时的概率全部加起来，才得到了这个样本出现的概率：
$$
\theta^\dagger,z^\dagger_i= \arg \max \sum_i \log(\sum_{z_i}p_i(x|\theta,z_i))
$$

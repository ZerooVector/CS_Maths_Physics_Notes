---
banner: 
title: PSAVE
creation_date: 2024-03-21
domain: 机器学习可解释性
publish: 未发表
tags:
  - Research
---
## 基础信息区
### 本文面对了什么挑战？
某些特征对神经网络的预测结果有负的效应，这些特征导致了特征重要性的不正确估计（低估）

### 一句话概括本文的内容？
使用 Shap 值评价特征重要性
提出了一种“正面的”联盟结构 $\mathcal{F}$，使得其中任意一个联盟 $S$ 加入另一个联盟 $T$ 时不 带来负面的边际效用：
$$
v(S \cup T) \ge v(S) + v(T)
$$
定义了某个联盟的“联盟红利”，是该联盟的值函数扣除所有子联盟的“联盟红利”，是一个递归定义的函数：
$$
\Delta (S,N,v)  = 
\begin{cases}
v(S) - \sum_{T \subset S} \Delta (T,N,v) & |S| = 2 \\
v(S) & |S| = 1  \\
0 & |S| = 0 
\end{cases}
$$
每个特征的重要性由包含它的集合带来的“联盟红利”评价：
$$
\phi_{i}(N,\mathcal{F},v) = \sum_{S \in \mathcal{F}, i \in S} \dfrac{p_{i}}{Z} \Delta (S,\mathcal{F},v)
$$
其中 $p_{i}$ 是特征 $i$ 的某种 Priority，$Z$ 是配分函数
### 你对本文作何评价？
可能是草稿。符号混乱，$p_{i}$ 似乎是强行引入的。全文在讲故事，但是逻辑性不强。
## 笔记区


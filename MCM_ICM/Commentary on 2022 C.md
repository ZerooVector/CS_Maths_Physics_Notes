---
banner: "![[banner6.png]]"
---
#MCM 

## Triage
->这一阶段就是不要落下东西，落下一项直接 S

## 模型的目标是什么？
本题的目标是最大化收益，而大多数队伍在考虑时平衡了收益与风险。裁判认为，这是可行的。

## 模型缺东西
每年都有缺东西的同志死在 Triage 里面，今年，缺的最多的是：证明一个队伍的策略为什么是最好的，这也是整个问题最为困难的一部分。
证明一个策略是最好的是困难的，一些队伍说，自己使用了最好的算法来估计参数，这是不恰当的。一个合理的方法是，将现有的策略和一大堆 baseline 进行比较。

![[Pasted image 20230213170951.png]]

## 控制不确定性
只有很少的队伍考虑了不确定性（e.g. 使用标准差衡量不确定性，给出预测值的置信区间，等等）。更少的队伍表达了结果的不确定性。这些内容会使得裁判对你刮目相看。

## 关于手续费
一些队伍交易次数太多了，造成了高昂的手续费，这是他们失败的原因！一支队伍， #2229059 ，设置了每笔交易的最小持仓时间。

## 完美的交易策略
完美的交易策略是你的策略优秀程度的标杆，还可以用于检测你的策略是否有错。

## 好好写小文章
小文章应该包含对模型的解释

## 哪些文章才是优胜者？
- 解决了全部问题
- 包含很好的图，总结了自己的结果
![[Pasted image 20230213172834.png]]
- 总结和摘要中均包含了结果
- 很好地分析了强弱点
- 结果合理

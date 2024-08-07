#Econometrics  #MCM 

**DID Estimation**被用来研究某种处理行为的效应
- 处理行为：某项政策，我们可以使用 0/1 变量描述这一处理行为。例如：*封城*是不是降低了新冠感染率
- 效应对象：研究问题关注的一个或多个结果。例如：让王宏洲变成一个猫娘会不会提高*北理工的建模竞赛成绩*

在使用 DID Est 时，我们选择的数据必须：
- 使用**观测数据**：数据包括观测数据 (Observation Data)和实验数据 (Experimental Data)。观测数据是真实发生的数据，而不是人为地通过实验获得的；实验数据则是化学、生物实验中通过人为的实验设计得到的数据。例如：统计不同的催化剂组合-乙醇制 C 4 烯烃的收率的数据->实验数据；统计一只 ENTP 和一只 INTP 的每周平均社交时间->观测数据。实验数据不需要 DID，是因为实验数据通常非常精确，可以直接对比（或者使用假设检验，ANOVA 等方法处理）
- **包含处理组和非处理组个体** ：
- 在时间上，必须包含**处理前和处理后的数据** 

## DID 的基本原理
在两期 DID 中，我们假定所有的处理行为发生在同一时间点。另外的方法包括渐进 DID（处理行为发生在不同时间点）
例如：研究催更是否加快了 UP 主的更新频率
![[Pasted image 20230502135134.png|400]]
显然，我们不可以使用催更组组内进行比较
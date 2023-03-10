---
banner: "![[banner16.png]]"
---
#Algo 
DP 的适用条件：**无后效性——已经求解好的子问题的结果，在后续求解中不再改变、最优子结构性
质——下一阶段的最优解可以从前面所有子问题的最优解中导出**
**DP 的转移顺序在状态空间中构成 DAG**

## 线性 DP

### 例题 1
给定数组 $a$，从中选取元素，但是不能选取两个相邻的数值，求选取元素的最大和。
状态转移方程：
$$
dp[i] = \max(a[i]+dp[i-2],dp[i-1])
$$
思路：对于第 $i$ 个位置，要么选择第 $i$ 个位置，但是不选择第 $i-1$ 个位置，此时问题化为 $i-2$ 的子问题；要么不选 $i$，问题华为 $i-1$ 的子问题

### 例题 2 
求最长上升子序列
定义 $dp[i]$ 为以下标 $i$ 结尾的子序列最长的长度

定义 $tail[i]$ 为 $i+1$ 长度 LIS 上的最小的末尾

### 例题 3：最长公共子序列
定义  $dp[i][j]$ 为第一个串的第 $i$ 个和第二个的第 $j$ 个，那么

## 背包 DP

### 例题 1 ：0-1 背包
$$
dp[i][j] = \max(dp[i-1][j],dp[i-1][j-w[i]]+v[i])
$$
由于 $i$ 层只与 $i-1$ 层有关，因此可以只开两层。另一种做法是滚动数组

### 例题 2 ：完全背包

### 多重和分组背包

## 状态机 DP


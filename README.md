# blue-bridge

蓝桥杯竞赛代码

## 动态规划

### 题目

问题描述

　　题目很简单，给出N个数字，不改变它们的相对位置，在中间加入K个乘号和N-K-1个加号，（括号随便加）使最终结果尽量大。因为乘号和加号一共就是N-1个了，所以恰好每两个相邻数字之间都有一个符号。例如：
  
　　N=5，K=2，5个数字分别为1、2、3、4、5，可以加成：
  
　　1*2*(3+4+5)=24
  
　　1*(2+3)*(4+5)=45
  
　　(1*2+3)*(4+5)=45
  
　　……
  
输入格式

　　输入文件共有二行，第一行为两个有空格隔开的整数，表示N和K，其中（2<=N<=15, 0<=K<=N-1）。第二行为 N个用空格隔开的数字（每个数字在0到9之间）。
输出格式

　　输出文件仅一行包含一个整数，表示要求的最大的结果
  
样例输入

5 2

1 2 3 4 5

样例输出

120

样例说明

(1+2+3)*4*5=120

### 思路

是动态规划的典型例题

不要考虑括号，只从乘号来考虑，设dp[i][j]表示，i个元素里有j个乘号时算式的最大值。sum[i]表示前i个元素的和。

因此动态规划状态转移方程为：dp[i][j]=max(dp[i][j]，dp[l-1][j-1]*(sum[i]-sum[l-1]])，思路：假设最后一个乘号出现在第l个元素之前，所以问题就转化为了求前l-1个数加j-1个乘号最大的算式值载乘上第l个元素到第i个元素的和，而l-1个元素加j-1个乘号又可以按相同的方法分解为更小的子问题。只要找出一个l使得最后一个乘号出现在这个位置上时的值最大，就可以存入dp[i][j]中。

![Image text](https://github.com/naginoasukara/machinelearninginaction/blob/master/%E6%9C%BA%E5%99%A8%E5%AD%A6%E4%B9%A0%E5%AE%9E%E6%88%98/ch4/image/1.png)

[力扣](https://leetcode-cn.com/problems/na-ying-bi/)

# 题目描述

桌上有 n 堆力扣币，每堆的数量保存在数组 coins 中。我们每次可以选择任意一堆，拿走其中的一枚或者两枚，求拿完所有力扣币的最少次数。

示例 1：

```
输入：[4,2,1]
输出：4
解释：第一堆力扣币最少需要拿 2 次，第二堆最少需要拿 1 次，第三堆最少需要拿 1 次，总共 4 次即可拿完。
```

示例 2：

```
输入：[2,3,10]
输出：8
```

# 解体思路

1. 求出每堆的拿的次数(i + 1) / 2，因为每堆最少一个硬币。+1可以处理少于2的次数为0的边界问题。
2. 累加每堆的次数

# 实现代码

```cpp
class Solution {
public:
    int minCount(vector<int>& coins) {
        int ans = 0;
        for (int coin: coins) {
            ans += (coin + 1) / 2;
        }
        return ans;
    }
};
```

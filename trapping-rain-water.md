[力扣](https://leetcode-cn.com/problems/trapping-rain-water/)

# 题目描述

给定 n 个非负整数表示每个宽度为 1 的柱子的高度图，计算按此排列的柱子，下雨之后能接多少雨水。

上面是由数组 [0,1,0,2,1,0,1,3,2,1,2,1] 表示的高度图，在这种情况下，可以接 6 个单位的雨水（蓝色部分表示雨水）。 

示例:

```
输入: [0,1,0,2,1,0,1,3,2,1,2,1]
输出: 6
```

# 解体思路

1. 先遍历一遍，找到最高点，记录高度和坐标
2. 再分别从两边两个指针往中间扫，以当前遍历中遇到的最高点的高度为标准s
3. 再往中间走，如果当前的坐标高度小于s，就说明当前坐标能接的雨水为s-height[i]

# 实现代码

```cpp
class Solution {
public:
    int trap(vector<int>& height) {
        int ans = 0, maxIndex = 0, maxHeight = 0;
        for (int i = 0; i < height.size(); ++i) {
            if (height[i] > maxHeight) {
                maxHeight = height[i];
                maxIndex = i;
            }
        }

        int tempMax = 0;
        for (int i = 0; i < maxIndex; ++i) {
            if (height[i] > tempMax) {
                tempMax = height[i];
            } else {
                ans += tempMax - height[i];
            }
        }
        tempMax = 0;
        for (int i = height.size() - 1; i >= maxIndex; --i) {
           if (height[i] > tempMax) {
                tempMax = height[i];
            } else {
                ans += tempMax - height[i];
            } 
        }
        return ans;

    }
};
```

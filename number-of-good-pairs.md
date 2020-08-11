[力扣](https://leetcode-cn.com/problems/number-of-good-pairs/)

# 题目描述

给你一个整数数组 nums 。

如果一组数字 (i,j) 满足 nums[i] == nums[j] 且 i < j ，就可以认为这是一组 好数对 。

返回好数对的数目。

示例 1：

```bash
输入：nums = [1,2,3,1,1,3]
输出：4
解释：有 4 组好数对，分别是 (0,3), (0,4), (3,4), (2,5) ，下标从 0 开始
```

示例 2：

```bash
输入：nums = [1,1,1,1]
输出：6
解释：数组中的每组数字都是好数对
```

示例 3：

```bash
输入：nums = [1,2,3]
输出：0
```

# 解体思路

本题使用数学法：用哈希表统计每个数在序列中出现的次数，假设数字在序列中出现的次数为 v，那么出现好数对的个数是 v * (v - 1) / 2。

# 实现代码

```cpp
class Solution {
public:
    int numIdenticalPairs(vector<int>& nums) {
        int ans = 0;
        map<int, int> m;
        for (int num: nums) m[num] += 1;
        for (auto &[k, v]: m) ans += (v * (v - 1) / 2);
        return ans;
    }
};
```

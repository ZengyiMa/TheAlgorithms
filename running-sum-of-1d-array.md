[力扣](https://leetcode-cn.com/problems/running-sum-of-1d-array/)

# 题目描述

给你一个数组 nums 。数组「动态和」的计算公式为：runningSum[i] = sum(nums[0]…nums[i]) 。

请返回 nums 的动态和。

示例 1：

```bash
输入：nums = [1,2,3,4]
输出：[1,3,6,10]
解释：动态和计算过程为 [1, 1+2, 1+2+3, 1+2+3+4] 。
```

示例 2：

```bash
输入：nums = [1,1,1,1,1]
输出：[1,2,3,4,5]
解释：动态和计算过程为 [1, 1+1, 1+1+1, 1+1+1+1, 1+1+1+1+1] 。
```

示例 3：

```bash
输入：nums = [3,1,2,10,1]
输出：[3,4,6,16,17]
```

# 解体思路

比较简单，循环求合即可。

# 实现代码

```cpp
class Solution {
public:
    vector<int> runningSum(vector<int>& nums) {
        vector<int> ans;
        int sum = 0;
        for (int num: nums) {
            sum += num;
            ans.push_back(sum);
        }
        return ans;
    }
};
```

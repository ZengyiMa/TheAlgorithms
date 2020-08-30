[力扣](https://leetcode-cn.com/problems/merge-sorted-array/)

# 题目描述

给你两个有序整数数组 nums1 和 nums2，请你将 nums2 合并到 nums1 中，使 nums1 成为一个有序数组。

说明:

初始化 nums1 和 nums2 的元素数量分别为 m 和 n 。
你可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。

示例:

输入:

```
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6], n = 3
输出: [1,2,2,3,5,6]
```

# 解体思路

已知num1的数量是 m + n的组合并且有序，我们使用双指针，从2者后往前遍历比较大小，把2者中的大的提取出来，在num1后往前排放即可。

# 实现代码

```cpp
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int index1 = m - 1;
        int index2 = n - 1;
        for (int i = nums1.size() - 1; i >= 0; --i) {
            if (index1 < 0 || index2 < 0) break;
            if (nums1[index1] <= nums2[index2]) {
                nums1[i] = nums2[index2];
                index2--;
            } else {
                nums1[i] = nums1[index1];
                index1--;
            }
        }
        if (index1 < 0 && index2 >= 0) {
            for (int i = 0; i <= index2; ++i) {
                nums1[i] = nums2[i];
            }
        } else if (index1 >= 0 && index2 < 0) {
            for (int i = 0; i <= index1; ++i) {
                nums1[i] = nums1[i];
            }
        }

    }
};
```

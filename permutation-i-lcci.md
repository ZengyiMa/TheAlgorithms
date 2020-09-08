[力扣](https://leetcode-cn.com/problems/permutation-i-lcci/)

# 题目描述

无重复字符串的排列组合。编写一种方法，计算某字符串的所有排列组合，字符串每个字符均不相同。

示例1:

```jsx
输入：S = "qwe"
输出：["qwe", "qew", "wqe", "weq", "ewq", "eqw"]
示例2:
```

输入：S = "ab"
输出：["ab", "ba"]

# 解体思路

回溯算法

# 实现代码

```cpp
class Solution {
public:
    vector<string> result;
    vector<string> permutation(string s) {
        if (s.size() == 0) return result;
        backtrace(s, 0);
        return result;
    }

    void backtrace(string &s, int index) {
        if (index == s.size()) {
            result.push_back(s);
            return;
        }
        for (int i = index; i < s.size(); ++i) {
            swap(s[index], s[i]);
            backtrace(s, index + 1);
            swap(s[index], s[i]);
        }
    }
};
```

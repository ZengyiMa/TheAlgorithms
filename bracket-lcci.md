[力扣](https://leetcode-cn.com/problems/bracket-lcci/)

# 题目描述

括号。设计一种算法，打印n对括号的所有合法的（例如，开闭一一对应）组合。

说明：解集不能包含重复的子集。

例如，给出 n = 3，生成结果为：

```jsx
[
"((()))",
"(()())",
"(())()",
"()(())",
"()()()"
]
```

# 解体思路

回溯算法

# 实现代码

```cpp
class Solution {
public:
    vector<string> result;
    vector<string> generateParenthesis(int n) {
        backtrace(n, n, "");
        return result;
    }

    void backtrace(int l, int r, string s) {
        if (l == 0 && r == 0) {
            result.push_back(s);
            return;
        }
        if (l > 0) {
            backtrace(l - 1, r, s+"(");
        }
        if (r > l) {
            backtrace(l, r - 1, s+")");
        }
    }
};
```

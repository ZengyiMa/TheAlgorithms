[力扣](https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number/)

# 题目描述

给定一个仅包含数字 2-9 的字符串，返回所有它能表示的字母组合。

给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。

示例:

```
输入："23"
输出：["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```

# 解体思路

使用回朔算法

# 实现代码

```cpp
class Solution {
public:

    vector<string> result;
    string letterMap[10] = {
        "", // 0
        "", // 1
        "abc", // 2
        "def", // 3
        "ghi", // 4
        "jkl", // 5
        "mno", // 6
        "pqrs", // 7
        "tuv", // 8
        "wxyz", // 9
    };

    void backtrace(string &digits, int index, string &s) {
        if (index >= digits.size()) {
            result.push_back(s);
            return;
        }
        string letter = letterMap[(digits[index] - '0')];
        for (int i = 0; i < letter.size(); ++i) {
            s.push_back(letter[i]);
            backtrace(digits, index + 1, s);
            s.pop_back();
        }
    }

    vector<string> letterCombinations(string digits) {
        if (digits.size() == 0) return result;
        string s = "";
        backtrace(digits, 0, s);
        return result;
    }
};
```

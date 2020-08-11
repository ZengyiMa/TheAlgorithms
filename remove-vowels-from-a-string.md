[力扣](https://leetcode-cn.com/problems/remove-vowels-from-a-string/)

# 题目描述

给你一个字符串 S，请你删去其中的所有元音字母（ 'a'，'e'，'i'，'o'，'u'），并返回这个新字符串。

示例 1：

```bash
输入："leetcodeisacommunityforcoders"
输出："ltcdscmmntyfrcdrs"
```

示例 2：

```bash
输入："aeiou"
输出：""
```

# 解体思路

过滤下字符串即可

# 实现代码

```cpp
class Solution {
public:
    string removeVowels(string S) {
        string ans;
        for (char s: S) {
            if (s == 'a' || s == 'e' || s == 'i' || s == 'o' || s == 'u') continue;
            ans.push_back(s);
        }
        return ans;
    }
};
```

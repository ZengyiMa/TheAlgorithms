[力扣](https://leetcode-cn.com/problems/reverse-words-in-a-string/)

# 题目描述

给定一个字符串，逐个翻转字符串中的每个单词。

示例 1：

```
输入: "the sky is blue"
输出: "blue is sky the"
```

示例 2：

```
输入: " hello world! "
输出: "world! hello"
解释: 输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。
```

示例 3：

```
输入: "a good example"
输出: "example good a"
解释: 如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。
```

说明：

- 无空格字符构成一个单词。
- 输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。
- 如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。

# 解体思路

1. 去除左右空格
2. 去除多余空格
3. 反转字符串
4. 反转单词

# 实现代码

```cpp
class Solution {
public:
    void reverseString(string &s, int start, int end) {
        for (; start <= end; ++start, --end) {
            char tmp = s[start];
            s[start] = s[end];
            s[end] = tmp;
        }
    }
    string reverseWords(string &s) {
        int start = 0, end = s.size() - 1;
        //去除头部空格
        for (; start <= end; ++start) {
            if (s[start] != ' ') break;
        }
        for (; end >= start; --end) {
            if (s[end] != ' ') break;
        }
        //去除多余空格
        string ans;
        bool lastIsSpace = false;
        for (int i = start; i <= end; ++i) {
            if (lastIsSpace && s[i] == ' ') {
                continue;
            } else {
                if (s[i] == ' ') lastIsSpace = true;
                else lastIsSpace = false;
                ans.push_back(s[i]);
            }
        }
        // 反转字符串
        reverseString(ans, 0, ans.size() - 1);
        // 反转单词
        int wordStart = 0, wordEnd = 0;
        while (wordEnd < ans.size()) {
            if (ans[wordEnd] == ' ') {
                // 找到了单词
                reverseString(ans, wordStart, wordEnd - 1);
                wordStart = wordEnd + 1;
                wordEnd = wordStart;
            } else {
                wordEnd++;
                if (ans[wordEnd] == '\0') {
                    // 到了末尾
                    reverseString(ans, wordStart, wordEnd - 1);
                }
            }
        }
        return ans;
    }
};
```

[力扣](https://leetcode-cn.com/problems/jewels-and-stones/)

# 题目描述

给定字符串J 代表石头中宝石的类型，和字符串 S代表你拥有的石头。 S 中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。

J 中的字母不重复，J 和 S中的所有字符都是字母。字母区分大小写，因此"a"和"A"是不同类型的石头。

示例 1:

```
输入: J = "aA", S = "aAAbbbb"
输出: 3
```

示例 2:

```
输入: J = "z", S = "ZZ"
输出: 0
```

# 解体思路

1. 使用hashmap存储宝石的类型
2. 遍历字符串，判断是否是宝石

# 实现代码

```cpp
class Solution {
public:
    int numJewelsInStones(string J, string S) {
        map<char, bool> m;
        int ans = 0;
        for (char c: J) {
            m[c] = true;
        }
        for (char c: S) {
            if (m[c]) {
                ans++;
            }
        }
        return ans;
    }
};
```

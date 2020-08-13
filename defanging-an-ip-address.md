[力扣](https://leetcode-cn.com/problems/defanging-an-ip-address/)

# 题目描述

给你一个有效的 IPv4 地址 address，返回这个 IP 地址的无效化版本。

所谓无效化 IP 地址，其实就是用 "[.]" 代替了每个 "."。

示例 1：

```ruby
输入：address = "1.1.1.1"
输出："1[.]1[.]1[.]1"
```

示例 2：

```ruby
输入：address = "255.100.50.0"
输出："255[.]100[.]50[.]0"
```

# 解体思路

变量字符串，遇到 . 则添加[.]即可

# 实现代码

```cpp
class Solution {
public:
    string defangIPaddr(string address) {
        string ans;
        for (char c: address) {
            if (c == '.') {
                ans.push_back('[');
                ans.push_back('.');
                ans.push_back(']');
            } else{
                ans.push_back(c);
            }
        }
        return ans;
    }
};
```

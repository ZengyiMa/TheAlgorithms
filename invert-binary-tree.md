[力扣](https://leetcode-cn.com/problems/invert-binary-tree/)

# 题目描述

翻转一棵二叉树。

示例：

输入：

```
 4
/ \
2 7
/ \ / \
1 3 6 9
输出：
```

```
 4
/ \
7 2
/ \ / \
9 6 3 1
```

# 解体思路

递归的方式依次替换替换左右2个节点

# 实现代码

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* invertTree(TreeNode* root) {
        if (!root) return root;
        TreeNode *left = invertTree(root->left);
        TreeNode *right = invertTree(root->right);
        root->left = right;
        root->right = left;
        return root;
    }
};
```

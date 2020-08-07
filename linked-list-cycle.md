[力扣](https://leetcode-cn.com/problems/linked-list-cycle/)

# 题目描述

给定一个链表，判断链表中是否有环。

为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。

示例 1：

```cpp
输入：head = [3,2,0,-4], pos = 1
输出：true
解释：链表中有一个环，其尾部连接到第二个节点。
```

示例 2：

```cpp
输入：head = [1,2], pos = 0
输出：true
解释：链表中有一个环，其尾部连接到第一个节点。
```

示例 3：

```cpp
输入：head = [1], pos = -1
输出：false
解释：链表中没有环。
```

# 解体思路

双指针找交点

# 实现代码

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
        if (!head) return head;
        ListNode *low = head;
        ListNode *fast = head->next;
        while (fast && fast->next) {
            if (low->val == fast->val) return true;
            low = low->next;
            fast = fast->next->next;
        }
        return false;
    }
};
```

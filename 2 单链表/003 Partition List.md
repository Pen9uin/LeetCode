## - Partition List

### 描述

```
    Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater
than or equal to x.
    You should preserve the original relative order of the nodes in each of the two partitions.
    For example, Given 1->4->3->2->5->2 and x = 3, return 1->2->2->4->3->5.
```

### 分析

将所有小于给定值的节点取出组成一个新的链表

### 代码

```C++
// 时间复杂度O(n)，空间复杂度O(1)
class Solution {
public:
    ListNode* partition(ListNode* head, int x) 
    {
        ListNode left_dummy = new ListNode(-1);
        ListNode right_dummy = new ListNode(-1);
        ListNode *left_cur = left_dummy;
        ListNode *right_cur = right_dummy;

        for (ListNode *cur = head; cur; cur = cur->next) 
        {
            if (cur->val < x) {
                left_cur->next = cur;
                left_cur = cur;
            } else {
                right_cur->next = cur;
                right_cur = cur;
            }
        }

        left_cur->next = right_dummy.next;
        right_cur->next = nullptr;

        return left_dummy.next;
    }
};
```

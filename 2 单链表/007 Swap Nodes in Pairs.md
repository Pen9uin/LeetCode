## - Swap Nodes in Pairs

### 描述

```
    Given a linked list, swap every two adjacent nodes and return its head.
    For example, Given 1->2->3->4, you should return the list as 2->1->4->3.
Your algorithm should use only constant space. You may not modify the values in the list, only nodes
itself can be changed.
```

### 分析

先建立dummy节点，注意在连接节点的时候，最好画个图，以免把自己搞晕了

### 代码

```C++
class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
        ListNode *dummy = new ListNode(-1), *pre = dummy;
        dummy->next = head;
        while (pre->next && pre->next->next) 
        {
            ListNode *t = pre->next->next;
            pre->next->next = t->next;
            t->next = pre->next;
            pre->next = t;
            pre = t->next;
        }
        return dummy->next;
    }
};
```

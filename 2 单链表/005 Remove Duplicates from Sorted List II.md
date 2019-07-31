## - Remove Duplicates from Sorted List II

### 描述

```
    Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers
from the original list.
    For example,
    Given 1->2->3->3->4->4->5, return 1->2->5.
    Given 1->1->1->2->3, return 2->3.
```

### 分析
无

### 代码

```C++
class Solution {
public:
    ListNode *deleteDuplicates(ListNode *head) 
    {
        if(!head || !head->next)    return head;
        ListNode *dummy = new ListNode(-1);
        ListNode *dummy->next = head;
        ListNode *pre = dummy;
        while(pre->next)
        {
            ListNode *cur = pre->next;
            while(cur->next && cur->next->val = cur->val)
                cur = cur->next;
                
            if(cur == pre->next)
                pre = pre->next;
            else
                pre->next = cur->next;
            
            return dummy->next;
        }
    }
};
```
       
            

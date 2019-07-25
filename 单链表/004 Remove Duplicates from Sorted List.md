## - Remove Duplicates from Sorted List

### 描述
```
Given a sorted linked list, delete all duplicates such that each element appear only once.
For example,
Given 1->1->2, return 1->2.
Given 1->1->2->3->3, return 1->2->3.
```

### 分析
无

### 代码

```C++
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) 
    {
        ListNode *cur = head;
        while (cur && cur->next) {
            if (cur->val == cur->next->val) {
                cur->next = cur->next->next;
            } else {
                cur = cur->next;
            }
        }
        return head;
    }
};
```

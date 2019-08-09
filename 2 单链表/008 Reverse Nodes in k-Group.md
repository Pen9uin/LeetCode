## - Reverse Nodes in k-Group

### 描述

```
Given a linked list, reverse the nodes of a linked list k at a time and return its modified list.

k is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of k then left-out nodes in the end should remain as it is.

Example:
Given this linked list: 1->2->3->4->5
For k = 2, you should return: 2->1->4->3->5
For k = 3, you should return: 3->2->1->4->5

Note:
Only constant extra memory is allowed.
You may not alter the values in the list's nodes, only nodes itself may be changed.
```

###
递归解法

### 代码
```
class Solution{
public:
	ListNode* reverseKGroup(ListNode* head, int k) {
    ListNode* temp = head;
    for (int i = 1; i < k && temp != null; i++) {
        temp = temp.next;
    }
    //判断节点的数量是否能够凑成一组
    if(temp == null)
        return head;

    ListNode* t2 = temp.next;
    temp.next = null;
    //把当前的组进行逆序
    ListNode* newHead = reverseList(head);
    //把之后的节点进行分组逆序
    ListNode* newTemp = reverseKGroup(t2, k);
    // 把两部分连接起来
    head.next = newTemp;

    return newHead;
}

//逆序单链表
private:
	static ListNode* reverseList(ListNode* head) {
		if(head == null || head.next == null)
			return head;
		ListNode* result = reverseList(head.next);
		head.next.next = head;
		head.next = null;
		return result;
	}
};
```



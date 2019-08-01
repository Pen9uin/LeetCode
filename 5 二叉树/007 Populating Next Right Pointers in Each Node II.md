## - 117 Populating Next Right Pointers in Each Node II

### 描述

```
Given a binary tree

struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.

Initially, all next pointers are set to NULL.

Example: Given the following binary tree,

         1
       /  \
      2    3
     / \    \
    4   5    7
After calling your function, the tree should look like:

         1 -> NULL
       /  \
      2 -> 3 -> NULL
     / \    \
    4-> 5 -> 7 -> NULL
```

### 分析

用到queue来辅助，由于是层序遍历，每层的节点都按顺序加入queue中，而每当从queue中取出一个元素时，将其next指针指向queue中下一个节点即可，我们对于每层的开头元素开始遍历之前，先统计一下该层的总个数，用个for循环，这样for循环结束的时候，我们就知道该层已经被遍历完了。

### 代码
```
class Solution {
public:
    Node* connect(Node* root) {
        if (!root) return NULL;
        queue<Node*> q;
        q.push(root);
        while (!q.empty()) {
            int size = q.size();
            for (int i = 0; i < size; ++i) {
                Node *t = q.front(); q.pop();
                if (i < size - 1) {
                    t->next = q.front();
                }
                if (t->left) q.push(t->left);
                if (t->right) q.push(t->right);
            }
        }
        return root;
    }
};
```

### 参考

https://www.cnblogs.com/grandyang/p/4288151.html

https://www.cnblogs.com/grandyang/p/4290148.html





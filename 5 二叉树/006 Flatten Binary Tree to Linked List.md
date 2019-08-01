## - 114 Flatten Binary Tree to Linked List

### 描述

```
Given a binary tree, flatten it to a linked list in-place.

For example,
Given

         1
        / \
       2   5
      / \   \
     3   4   6
 

The flattened tree should look like:

   1
    \
     2
      \
       3
        \
         4
          \
           5
            \
             6
```

### 分析

据展开后形成的链表的顺序分析出是使用先序遍历。

1. 先 flatten 左右子树，再合并
2. 先序遍历，保存前一个节点

### 代码1
```C++
class Solution {
public:
    void flatten(TreeNode *root) {
        if (!root) return;
        if (root->left) flatten(root->left);
        if (root->right) flatten(root->right);
        TreeNode *tmp = root->right;
        root->right = root->left;
        root->left = NULL;
        while (root->right) root = root->right;
        root->right = tmp;
    }
};

```
例如，对于下面的二叉树，上述算法的变换的过程如下：

```
     1
    / \
   2   5
  / \   \
 3   4   6

     1
    / \
   2   5
    \   \
     3   6
      \    
       4

   1
    \
     2
      \
       3
        \
         4
          \
           5
            \
             6
```

### 代码2
```
class Solution {
public:
    void flatten(TreeNode* root) {
        if (root == NULL)
            return;
        
        TreeNode *last = NULL;
        flattenTree(root, last);
    }
    
    void flattenTree(TreeNode *root, TreeNode* &last)
    {
        if (root == NULL)
            return;
        
        if (last != NULL)
        {
            last->right = root;
            last->left = NULL;
        }
        last = root;
        
        TreeNode *left = root->left;
        TreeNode *right = root->right; //root的右节点会改变
        
        flattenTree(left, last);
        flattenTree(right, last);
    }
};
```

## 参考

https://www.cnblogs.com/grandyang/p/4293853.html

https://cuijiahua.com/blog/2017/12/basis_26.html











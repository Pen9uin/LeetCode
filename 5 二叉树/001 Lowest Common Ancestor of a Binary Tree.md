## - 236 Lowest Common Ancestor of a Binary Tree

### 描述

```
Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.
According to the definition of LCA on Wikipedia: 
    “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow a node to be a descendant of itself).”
Given the following binary tree:  root = [3,5,1,6,2,0,8,null,null,7,4]
```

![](https://assets.leetcode.com/uploads/2018/12/14/binarytree.png)

### 代码

```C++
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
       if (!root || p == root || q == root) 
           return root;
       TreeNode *left = lowestCommonAncestor(root->left, p, q);
       TreeNode *right = lowestCommonAncestor(root->right, p , q);
       if (left && right)
           return root;
       return left ? left : right;
    }
};
```

### 参考

https://www.cnblogs.com/grandyang/p/4641968.html

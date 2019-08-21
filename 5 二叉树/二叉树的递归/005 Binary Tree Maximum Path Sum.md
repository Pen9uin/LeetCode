## - Binary Tree Maximum Path Sum

### 描述

```
Given a non-empty binary tree, find the maximum path sum.

For this problem, a path is defined as any sequence of nodes from some starting node to any node in the tree along the parent-child connections. The path must contain at least one node and does not need to go through the root.

Example 1:
Input: [1,2,3]

       1
      / \
     2   3

Output: 6

Example 2:
Input: [-10,9,20,null,null,15,7]

   -10
   / \
  9  20
    /  \
   15   7

Output: 42
```

### 代码
```
class Solution {
public:
    int maxPathSum(TreeNode* root) {
        int res = INT_MIN;
        helper(root, res);
        return res;
    }
    int helper(TreeNode* node, int& res) {
        if (!node) return 0;
        int left = max(helper(node->left, res), 0);
        int right = max(helper(node->right, res), 0);
        res = max(res, left + right + node->val);
        return max(left, right) + node->val;
    }
};
```

### 参考

https://www.cnblogs.com/grandyang/p/4280120.html

![MaxPath Between Two Nodes](https://github.com/Pen9uin/LeetCode/blob/master/5%20%E4%BA%8C%E5%8F%89%E6%A0%91/008%20MaxPath%20Between%20Two%20Nodes.md)



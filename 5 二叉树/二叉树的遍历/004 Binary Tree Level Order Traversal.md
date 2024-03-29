## - Binary Tree Level Order Traversal

### 描述

```
    Given a binary tree, return the level order traversal of its nodes’ values. (ie, from left to right, level by
level).
    For example: Given binary tree {3,9,20,#,#,15,7},
     3
    / \
   9  20
     /  \
    15   7
    return its level order traversal as:
    [
     [3],
     [9,20],
     [15,7]
    ]
```

### 代码
```C++
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        if (!root) return {};
        vector<vector<int>> res;
        queue<TreeNode*> q;
        q.push(root);
        while (!q.empty()) {
            vector<int> oneLevel;
            for (int i = q.size(); i > 0; --i) {
                TreeNode *t = q.front(); q.pop();
                oneLevel.push_back(t->val);
                if (t->left) q.push(t->left);
                if (t->right) q.push(t->right);
            }
            res.push_back(oneLevel);
        }
        return res;
    }
};
```

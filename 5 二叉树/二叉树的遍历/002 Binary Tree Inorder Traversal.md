## - Binary Tree Inorder Traversal

### 代码
```C++
class Solution {
public:
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> res;
        stack<TreeNode*> s;
        TreeNode *p = root;
        while (!s.empty() || p) {
            if (p) {
                s.push(p);
                p = p->left;
            } else {
                p = s.top(); s.pop();
                res.push_back(p->val);
                p = p->right;
            }
        }
        return res;
    }
};
```

### 参考

https://www.cnblogs.com/grandyang/p/4297300.html

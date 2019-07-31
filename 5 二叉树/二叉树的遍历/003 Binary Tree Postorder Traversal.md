## - Binary Tree Postorder Traversal

### 分析

先将先序遍历的根-左-右顺序变为根-右-左，再翻转变为后序遍历的左-右-根，翻转通过改变结果res的加入顺序来实现。

### 代码
```C++
class Solution {
public:
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> res;
        stack<TreeNode*> s;
        TreeNode *p = root;
        while (!s.empty() || p) {
            if (p) {
                s.push(p);
                res.insert(res.begin(), p->val);
                p = p->right;
            } else {
                TreeNode *t = s.top(); s.pop();
                p = t->left;
            }
        }
        return res;
    }
};
```

### 参考

https://www.cnblogs.com/grandyang/p/4251757.html

## - Path Sum II

### 描述

```
Given a binary tree and a sum, find all root-to-leaf paths where each path's sum equals the given sum.

For example:
Given the below binary tree and sum = 22,
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
return
[
   [5,4,11,2],
   [5,8,4,5]
]
```

### 代码

```
class Solution {
public:
    vector<vector<int> > FindPath(TreeNode* root,int expectNumber){
        if(root == NULL){
            return result;
        }
        
        tmp.push_back(root->val);
        if((expectNumber - root->val ) == 0 && root->left == NULL && root->right == NULL){
            result.push_back(tmp);
        }
        
        //遍历左子树
        FindPath(root->left, expectNumber - root->val);
        //遍历右子树
        FindPath(root->right, expectNumber - root->val);
        
        tmp.pop_back();
        return result;
    }
private:
    vector<vector<int> > result;
    vector<int> tmp;
};
```

### 参考

https://cuijiahua.com/blog/2017/12/basis_24.html

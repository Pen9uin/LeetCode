## - 99 Recover Binary Search Tree

### 描述

```
Two elements of a binary search tree (BST) are swapped by mistake.
Recover the tree without changing its structure.

Example 1:
Input: [1,3,null,null,2]
   1
  /
 3
  \
   2
Output: [3,1,null,null,2]

   3
  /
 1
  \
   2
   
Example 2:
Input: [3,1,4,null,null,2]
  3
 / \
1   4
   /
  2
Output: [2,1,4,null,null,3]

  2
 / \
1   4
   /
  3
  
Follow up:
A solution using O(n) space is pretty straight forward.
Could you devise a constant space solution?
```

### 分析

1. 用中序遍历树，并将所有节点存到一个一维向量中，把所有节点值存到另一个一维向量中，然后对存节点值的一维向量排序，在将排好的数组按顺序赋给节点。这种最一般的解法可针对任意个数目的节点错乱的情况。

2. 这里需要三个指针，first，second分别表示第一个和第二个错乱位置的节点，pre指向当前节点的中序遍历的前一个节点。这里用传统的中序遍历递归来做，不过再应该输出节点值的地方，换成了判断pre和当前节点值的大小，如果pre的大，若first为空，则将first指向pre指的节点，把second指向当前节点。这样中序遍历完整个树，若first和second都存在，则交换它们的节点值即可。

### 代码1
```C++
class Solution {
public:
    void recoverTree(TreeNode* root) {
        vector<TreeNode*> list;
        vector<int> vals;
        inorder(root, list, vals);
        sort(vals.begin(), vals.end());
        for (int i = 0; i < list.size(); ++i) {
            list[i]->val = vals[i];
        }
    }
    void inorder(TreeNode* root, vector<TreeNode*>& list, vector<int>& vals) {
        if (!root) return;
        inorder(root->left, list, vals);
        list.push_back(root);
        vals.push_back(root->val);
        inorder(root->right, list, vals);
    }
};
```

### 代码2
```C++
class Solution {
public:
    TreeNode* first, *second, *prev;
    void inorder(TreeNode* root) {
        if(!root) return;
        inorder(root->left);
        if(prev && prev->val > root->val) {
            if(!first) first = prev;
            second = root;
        }
        prev = root;
        inorder(root->right);
    }
    void recoverTree(TreeNode* root) {
        inorder(root);
        swap(first->val, second->val);
    }
};
```


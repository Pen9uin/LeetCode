### 编程之美3.8

### 分析

距离最大的两个节点可能是一个在左子树，一个在右子树，也可能是在一个子树上。

我试着把这个问题转化一下：树中的每一个节点都是一颗子树的根，对于这棵子树而言，它左边的最长路径是Lm，右边的最长路径是Rm，求所有子树中(Lm + Rm)的最大值是多少？

### 代码

```
int maxPath(TreeNode* root) {  
    //如果树是空的或叶子节点，则返回0  
    //这里与求节点的高度有些差异，叶子节点的高度为1，路径长度为0
    if(root == NULL || (!root.left && !root.right)  
        return 0;  
        
    int lm = maxDist(root->left);  
    int rm = maxDist(root->right);  
    
    //如果以该节点为根的子树中有最大的距离，那就更新最大距离  
    int sum = lm + rm;  
    if(sum > max) {  
        max = sum;  
    }  
  
    return max(lm,rm)+1;  
} 
```

### 参考

https://caoxyemail.iteye.com/blog/2129866

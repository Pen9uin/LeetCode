## - N-Queens II

### 描述

```
Given an integer n, return the number of distinct solutions to the n-queens puzzle.
```

### 代码

```
class Solution {
public:
    int totalNQueens(int n) {
        int res = 0;
        vector<int> pos(n, -1);
        helper(pos, 0, res);
        return res;
    }
    void helper(vector<int>& pos, int row, int& res) {
        int n = pos.size();
        if (row == n) {++res; return;}
        for (int col = 0; col < n; ++col) {
            if (isValid(pos, row, col)) {
                pos[row] = col;
                helper(pos, row + 1, res);
                pos[row] = -1;
            }
        }
    }
    bool isValid(vector<int>& pos, int row, int col) {
        for (int i = 0; i < row; ++i) {
            if (col == pos[i] || abs(row - i) == abs(col - pos[i])) {
                return false;
            }
        }
        return true;
    }
};
```

### 参考

https://www.cnblogs.com/grandyang/p/4380706.html

https://www.cnblogs.com/grandyang/p/4377782.html

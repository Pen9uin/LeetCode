## - Longest Palindromic Substring

### 描述

```
    Given a string S, find the longest palindromic substring in S. You may assume that the maximum length
of S is 1000, and there exists one unique longest palindromic substring.
```

### 分析

思路一：暴力枚举，以每个元素为中间元素，同时从左右出发，注意奇偶，复杂度 $O(n^2)$。

思路二：动规，复杂度 $O(n^2)$。设状态为 dp(i,j) ，表示区间 [i,j] 是否为回文串，则状态转移方程为


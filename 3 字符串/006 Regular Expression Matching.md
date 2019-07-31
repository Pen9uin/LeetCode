## - Regular Expression Matching

### 描述

```
    Implement regular expression matching with support for '.' and '*'.
    '.' Matches any single character. '*' Matches zero or more of the preceding element.
    The matching should cover the entire input string (not partial).
    The function prototype should be:
        bool isMatch(const char *s, const char *p)
        
    Some examples:
isMatch("aa","a") → false
isMatch("aa","aa") → true
isMatch("aaa","aa") → false
isMatch("aa", "a*") → true
isMatch("aa", ".*") → true
isMatch("ab", ".*") → true
isMatch("aab", "c*a*b") → true
```

### 分析

可以用二维 DP, 其中 dp[i][j] 表示 s[0...i-1] 和 p[0....j-1] 是否 match，有下面三种情况

1. ``P[i][j] = P[i - 1][j - 1]``, if ``p[j - 1] != '*' && (s[i - 1] == p[j - 1] || p[j - 1] == '.')``;
2. ``P[i][j] = P[i][j - 2]``, if ``p[j - 1] == '*'`` and the pattern repeats for 0 times;
3. ``P[i][j] = P[i - 1][j] && (s[i - 1] == p[j - 2] || p[j - 2] == '.')``, if ``p[j - 1] == '*'`` and the pattern repeats for at least 1 times.

### 代码

```C++
class Solution {
public:
    bool isMatch(string s, string p) {
        int m = s.size(), n = p.size();
        vector<vector<bool>> dp(m + 1, vector<bool>(n + 1, false));
        
        dp[0][0] = true;
        for (int i = 0; i <= m; ++i) 
        {
            for (int j = 1; j <= n; ++j) 
            {
                if (j > 1 && p[j - 1] == '*') {
                    dp[i][j] = dp[i][j - 2] || (i > 0 && (s[i - 1] == p[j - 2] || p[j - 2] == '.') && dp[i - 1][j]);
                } else {
                    dp[i][j] = i > 0 && dp[i - 1][j - 1] && (s[i - 1] == p[j - 1] || p[j - 1] == '.');
                }
            }
        }
        return dp[m][n];
    }
};
```

### 参考

https://www.cnblogs.com/grandyang/p/4461713.html

https://leetcode.com/problems/regular-expression-matching/discuss/5684/c-on-space-dp



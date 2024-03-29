## - Distinct Subsequences

### 描述
```
Given a string S and a string T, count the number of distinct subsequences of S which equals T.

A subsequence of a string is a new string which is formed from the original string by deleting some (can be none) of the characters 
without disturbing the relative positions of the remaining characters. (ie, "ACE" is a subsequence of "ABCDE" while "AEC" is not).

Example:
Input: S = "rabbbit", T = "rabbit"
Output: 3
```

### 代码
```
class Solution {
public:
    int numDistinct(string s, string t) {
        int m = s.size(), n = t.size();
        vector<vector<long>> dp(n + 1, vector<long>(m + 1));
        for (int j = 0; j <= m; ++j)
            dp[0][j] = 1;
        for (int i = 1; i <= n; ++i) {
            for (int j = 1; j <= m; ++j) {
                dp[i][j] = dp[i][j - 1] + (t[i - 1] == s[j - 1] ? dp[i - 1][j - 1] : 0);
            }
        }
        return dp[n][m];
    }
};
```

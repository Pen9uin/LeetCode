## - Palindrome Partitioning II

### 描述
```
Given a string s, partition s such that every substring of the partition is a palindrome.
Return the minimum cuts needed for a palindrome partitioning of s.

Example:
Input: "aab"
Output: 1
Explanation: The palindrome partitioning ["aa","b"] could be produced using 1 cut.
```

### 代码
```
class Solution {
public:
    int minCut(string s) {
        if (s.empty()) return 0;
        int n = s.size();
        vector<vector<bool>> p(n, vector<bool>(n));
        vector<int> dp(n);
        for (int i = 0; i < n; ++i) {
            dp[i] = i;
            for (int j = 0; j <= i; ++j) {
                if (s[i] == s[j] && (i - j < 2 || p[j + 1][i - 1])) {
                    p[j][i] = true;
                    dp[i] = (j == 0) ? 0 : min(dp[i], dp[j - 1] + 1);
                }
            }
        }
        return dp[n - 1];
    }
};
```

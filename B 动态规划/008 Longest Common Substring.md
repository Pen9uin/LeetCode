## - Longest Common Substring

### 分析

子串要求连续，dp[i][j]表示以 A 中第 i 个字符结尾的**子串**和 B 中第 j 个字符结尾的子串的的最大公共子串

### 代码

```
class LongestSubstring {
public:
    int findLongest(string A, int n, string B, int m) {
         if(n == 0 || m == 0)
            return 0;
        int rs = 0;
        int dp[n + 1][m + 1];
        for(int i = 0 ; i <= n; i++)//初始状态
            dp[i][0] = 0;
        for(int i = 0; i <= m; i++)
            dp[0][i] = 0;
        for(int i = 1; i <= n; i++)
            for(int j = 1; j<= m; j++)
            {
                if(A[i - 1] == B[j - 1])
                {
                    dp[i][j] = dp[i -1][j - 1] + 1;
                    rs = max(rs,dp[i][j]);//每次更新记录最大值
                }
 
                else//不相等的情况
                    dp[i][j] = 0;
            }
            return rs;//返回的结果为rs
    }
};
```

### 参考

https://www.cnblogs.com/wangkundentisy/p/9346376.html



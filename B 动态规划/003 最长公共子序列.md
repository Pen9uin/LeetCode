## - 最长公共子序列

### 描述
```
给定两个字符串A和B，长度分别为m和n，要求找出它们最长的公共子序列，并返回其长度。例如：
A = "HelloWorld"
B = "loop"
return: l o o
```

### 代码
```
class LCS
{
public:
    int findLCS(string A, int n, string B, int m)
    {
        if(n == 0 || m == 0)//特殊输入
            return 0;
        int dp[n + 1][m + 1];//定义状态数组
        for(int i = 0 ; i <= n; i++)//初始状态
            dp[i][0] = 0;
        for(int i = 0; i <= m; i++)
            dp[0][i] = 0;
        for(int i = 1; i <= n; i++)
            for(int j = 1; j<= m; j++)
            {
                if(A[i - 1] == B[j - 1])//判断A的第i个字符和B的第j个字符是否相同
                    dp[i][j] = dp[i -1][j - 1] + 1;
                else
                    dp[i][j] = max(dp[i - 1][j],dp[i][j - 1]);
            }
            return dp[n][m];//最终的返回结果就是dp[n][m]
    }
};
```

### 参考

https://www.cnblogs.com/wangkundentisy/p/9346376.html

https://www.cnblogs.com/wkfvawl/p/9362287.html


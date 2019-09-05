## - Edit Distance

### 描述
```
Given two words word1 and word2, find the minimum number of operations required to convert word1 to word2.

You have the following 3 operations permitted on a word:
1.Insert a character
2.Delete a character
3.Replace a character
```

### 代码
```
class Solution {
public:
    int minDistance(const string &word1, const string &word2) {
        const size_t n = word1.size();
        const size_t m = word2.size();
        int f[n + 1][m + 1];
        for (size_t i = 0; i <= n; i++)
            f[i][0] = i;
        for (size_t j = 0; j <= m; j++)
            f[0][j] = j;

        for (size_t i = 1; i <= n; i++) {
            for (size_t j = 1; j <= m; j++) {
                if (word1[i - 1] == word2[j - 1])
                    f[i][j] = f[i - 1][j - 1];
                else 
                    f[i][j] = 1 + min(f[i - 1][j - 1], min(f[i - 1][j], f[i][j - 1]));
            }
        }
        return f[n][m];
    }
};
```

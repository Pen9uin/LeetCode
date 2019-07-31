## - Longest Palindromic Substring

### 描述

```
    Given a string S, find the longest palindromic substring in S. You may assume that the maximum length
of S is 1000, and there exists one unique longest palindromic substring.
```

### 分析

思路一：暴力枚举，以每个元素为中间元素，同时从左右出发，注意奇偶，复杂度 $O(n^2)$。

思路二：动规，复杂度 $O(n^2)$。设状态为 $dp(i,j)$，表示区间 [i,j] 是否为回文串，则状态转移方程为

![](https://github.com/Pen9uin/LeetCode/blob/master/imgs/Longest%20Palindromic%20Substring.png)

思路三：Manacher’s Algorithm, 复杂度 $O(n)$。详细解释见 https://www.cnblogs.com/grandyang/p/4475985.html

### 代码1

```C++
class Solution {
public:
    string longestPalindrome(string s) {
        if (s.size() < 2) return s;
        int n = s.size(), maxLen = 0, start = 0;
        for (int i = 0; i < n - 1; ++i) {
            searchPalindrome(s, i, i, start, maxLen);
            searchPalindrome(s, i, i + 1, start, maxLen);
        }
        return s.substr(start, maxLen);
    }
    void searchPalindrome(string s, int left, int right, int& start, int& maxLen) {
        while (left >= 0 && right < s.size() && s[left] == s[right]) {
            --left; ++right;
        }
        if (maxLen < right - left - 1) {
            start = left + 1;
            maxLen = right - left - 1;
        }
    }
};
```

### 代码2

```C++
// 动规，时间复杂度O(n^2)，空间复杂度O(n^2)
class Solution {
public:
    string longestPalindrome(const string& s) {
        const int n = s.size();
        bool f[n][n];
        fill_n(&f[0][0], n * n, false);
        // 用 vector 会超时
        //vector<vector<bool> > f(n, vector<bool>(n, false));
        int max_len = 1, start = 0;  // 最长回文子串的长度，起点

        for (int i = 0; i < s.size(); i++) {
            f[i][i] = true;
            for (size_t j = 0; j < i; j++) {  // [j, i]
                f[j][i] = (s[j] == s[i] && (i - j < 2 || f[j + 1][i - 1]));
                if (f[j][i] && max_len < (i - j + 1)) {
                    max_len = i - j + 1;
                    start = j;
                }
            }
        }
        return s.substr(start, max_len);
    }
};
```



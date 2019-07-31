## - Longest Common Prefix 最长共同前缀

### 描述

  Write a function to find the longest common prefix string amongst an array of strings.

### 分析

无

### 代码

```C++
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if (strs.empty()) return "";
        for (int j = 0; j < strs[0].size(); ++j) {
            for (int i = 1; i < strs.size(); ++i) {
                if (j >= strs[i].size() || strs[i][j] != strs[0][j]) {
                    return strs[i].substr(0, j);
                }
            }
        }
        return strs[0];
    }
};
```

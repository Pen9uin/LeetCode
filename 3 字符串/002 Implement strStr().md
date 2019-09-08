## - Implement strStr()

### 描述

```
  Implement strStr().
  Returns a pointer to the first occurrence of needle in haystack, or null if needle is not part of haystack.
```

### 分析

暴力算法的复杂度是 O(m*n)，代码如下。更高效的的算法有 KMP 算法、Boyer-Mooer 算法和 Rabin-Karp 算法。面试中暴力算法足够了，一定要写得没有BUG。

### 代码

```C++
class Solution {
public:
    int strStr(string haystack, string needle) {
        if (needle.empty()) return 0;
        int m = haystack.size(), n = needle.size();
        if (m < n) return -1;
        
        for (int i = 0; i <= m - n; ++i) 
        {
            for (int j = 0; j < n; ++j) 
            {
                if (haystack[i + j] != needle[j]) break;
                if (j == n-1) return i;
            }
        }
        return -1;
    }
};
```


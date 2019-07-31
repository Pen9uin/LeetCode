## - Roman to Integer

### 描述

```
Given a roman numeral, convert it to an integer.
Input is guaranteed to be within the range from 1 to 3999.
```

### 分析

1. 如果当前数字是最后一个数字，或者之后的数字比它小的话，则加上当前数字。

2. 其他情况则减去这个数字。

### 代码

```C++
class Solution {
public:
    int romanToInt(string s) {
        int res = 0;
        unordered_map<char, int> m{{'I', 1}, {'V', 5}, {'X', 10}, {'L', 50}, {'C', 100}, {'D', 500}, {'M', 1000}};
        for (int i = 0; i < s.size(); ++i) 
        {
            int val = m[s[i]];
            if (i == s.size() - 1 || m[s[i+1]] <= m[s[i]]) res += val;
            else res -= val;
        }
        return res;
    }
};
```

### 参考

https://www.cnblogs.com/grandyang/p/4120857.html


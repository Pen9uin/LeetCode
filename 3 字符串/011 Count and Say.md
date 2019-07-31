## - Count and Say

### 描述

```
The count-and-say sequence is the sequence of integers beginning as follows:
1, 11, 21, 1211, 111221, ...
1 is read off as "one 1" or 11.
11 is read off as "two 1s" or 21.
21 is read off as "one 2", then "one 1" or 1211.
Given an integer n, generate the nth sequence.
Note: The sequence of integers will be represented as a string
```

### 分析

对于前一个数，找出相同元素的个数，把个数和该元素存到新的string里。

### 代码

```C++

class Solution {
public:
    string countAndSay(int n) {
        if (n <= 0) return "";
        string res = "1";
        while (--n) 
        {
            string cur = "";
            for (int i = 0; i < res.size(); ++i) 
            {
                int cnt = 1;
                while (i + 1 < res.size() && res[i] == res[i + 1]) {
                    ++cnt;
                    ++i;
                }
                cur += to_string(cnt) + res[i];
            }
            res = cur;
        }
        return res;
    }
};
```

### 参考

https://www.cnblogs.com/grandyang/p/4086299.html

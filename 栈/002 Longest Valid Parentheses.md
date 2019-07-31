## - 32 Longest Valid Parentheses

### 描述

```
  Given a string containing just the characters '(' and ')', find the length of the longest valid (wellformed)
parentheses substring.
  For "(()", the longest valid parentheses substring is "()", which has length = 2.
  Another example is ")()())", where the longest valid parentheses substring is "()()", which has
length = 4.
```

### 分析
1. 一维dp,  dp[i]表示以i为**子字符串末尾**时的最大长度

2. 借助栈来求解，需要定义个start变量来记录合法括号串的起始位置，我们遍历字符串，如果遇到左括号，则将当前下标压入栈；

如果遇到右括号，如果当前栈为空，则将下一个坐标位置记录到start，如果栈不为空，则将栈顶元素取出，此时若栈为空，则更新结果和i - start + 1中的较大值，否则更新结果和i - 栈顶元素中的较大值

### 代码1
```C++
class Solution {
public:
    int longestValidParentheses(string s) {
        int n = s.size(), maxLen = 0;
        vector<int> dp(n,0);
        for(int i=1; i<n; i++) 
        {
            if(s[i]==')') 
            {
                int j = i-1-dp[i-1];
                if(j >= 0 && s[j] == '(')
                {
                    dp[i] = dp[i - 1] + 2;
                    if(j-1 >= 0)
                        dp[i] += dp[j - 1];
                    
                    maxLen = max(maxLen, dp[i]);
                }
            }
        }
        return maxLen;
    }
};
```

### 代码2
```C++
class Solution {
public:
    int longestValidParentheses(string s) {
        int res = 0, start = 0;
        stack<int> m;
        for (int i = 0; i < s.size(); ++i) {
            if (s[i] == '(') 
                m.push(i);
            else if (s[i] == ')') {
                if (m.empty()) start = i + 1;
                else {
                    m.pop();
                    res = m.empty() ? max(res, i - start + 1) : max(res, i - m.top());
                }
            }
        }
        return res;
    }
};
```

### 参考

https://www.cnblogs.com/grandyang/p/4424731.html

https://blog.csdn.net/qqxx6661/article/details/77876647

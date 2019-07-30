## - Longest Substring Without Repeating Characters

### 描述

```
Given a string, find the length of the longest substring without repeating characters.

Example 1:
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 

Example 2:
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.

Example 3:
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

### 代码1
```C++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int maxlen = 0, l = 0;
        map<char,int> mp;
        for(int i = 0; i < s.size(); i++)
        {
            if(mp.find(s[i]) != mp.end())
                l = max(l,mp[s[i]] + 1);
            
            maxlen = max(maxlen,i-l+1);
            mp[s[i]] = i;
        }
        return maxlen;
    }
};
```

### 代码2

```C++
class Solution {
public:
	int lengthOfLongestSubstring(string s) {
        vector<int> dict(256, -1);
        int maxLen = 0, start = -1;
        for (int i = 0; i != s.length(); i++) {
            if (dict[s[i]] > start) //IsVisited
                start = dict[s[i]];
            dict[s[i]] = i;
            maxLen = max(maxLen, i - start);
        }
        return maxLen;
    }
};
```

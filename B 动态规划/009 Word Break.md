## - Word Break

### 描述
```
Given a non-empty string s and a dictionary wordDict containing a list of non-empty words, 
determine if s can be segmented into a space-separated sequence of one or more dictionary words.

Note:
The same word in the dictionary may be reused multiple times in the segmentation.
You may assume the dictionary does not contain duplicate words.

Example 1:
Input: s = "leetcode", wordDict = ["leet", "code"]
Output: true
Explanation: Return true because "leetcode" can be segmented as "leet code".

Example 2:
Input: s = "applepenapple", wordDict = ["apple", "pen"]
Output: true
Explanation: Return true because "applepenapple" can be segmented as "apple pen apple".
             Note that you are allowed to reuse a dictionary word.
Example 3:
Input: s = "catsandog", wordDict = ["cats", "dog", "sand", "and", "cat"]
Output: false
```

### 代码1
```
class Solution {
public:
    bool wordBreak(string s, vector<string>& wordDict) {
        unordered_set<string> wordSet(wordDict.begin(), wordDict.end());
        vector<bool> dp(s.size() + 1);
        dp[0] = true;
        for (int i = 0; i < dp.size(); ++i) {
            for (int j = 0; j < i; ++j) {
                if (dp[j] && wordSet.count(s.substr(j, i - j))) {
                    dp[i] = true;
                    break;
                }
            }
        }
        return dp.back();
    }
};
```

### 代码2
```
class Solution {
public:
    bool wordBreak(string s, unordered_set<string> &dict) {
        vector<bool> dp(s.length() + 1, false);
        dp[0] = true;
        int min_len = INT_MAX, max_len = INT_MIN;
        for (auto &ss : dict) {
            min_len = min(min_len, (int)ss.length());
            max_len = max(max_len, (int)ss.length());
        }
        for (int i = 0; i < s.length(); ++i)
        {
            if(dp[i]) 
            {
                for (int len = min_len; i + len <= s.length() && len <= max_len; ++len)
                    if (dict.find(s.substr(i, len)) != dict.end()) 
                        dp[i + len] = true;
                        
                if (dp[s.length()]) 
                    return true;
        }
        return dp[s.length()];
    }
};
```

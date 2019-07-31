## - 76 Minimum Window Substring

### 描述

```
    Given a string S and a string T, find the minimum window in S which will contain all the characters in
T in complexity O(n).
    For example, S = "ADBANC", T = "ABC"
    Minimum window is "BANC".
    Note:
  • If there is no such window in S that covers all characters in T, return the emtpy string "".
  • If there are multiple such windows, you are guaranteed that there will always be only one unique
minimum window in S.
```

### 分析

滑动窗口

### 代码

```C++
class Solution {
public:
    string minWindow(string s, string t) {
        string ans = "";
        vector<int> letter_count(128, 0);
        int left = 0;
        int count = 0; 
        int minLen = INT_MAX;
        
        for (char c : t)
            letter_count[c]++;
        
        for (int i = 0; i < s.size() ; i++){
            if(letter_count[s[i]] > 0)
                count++;
            
            //s可能会有重复字符，如果包含在if里会出错
            letter_count[s[i]]--;
            
            while(count == t.size()){
                if(minLen > i - left + 1){
                    minLen = i - left + 1;
                    ans = s.substr(left, minLen);
                }
                
                ++letter_count[s[left]];
                if(letter_count[s[left]] > 0){
                    --count;
                }
                ++left;
            }
        }
        return ans;
    }
};
```

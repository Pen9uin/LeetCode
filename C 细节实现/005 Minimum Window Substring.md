## - Minimum Window Substring

### 描述
```
Given a string S and a string T, find the minimum window in S which will contain all the characters in T in complexity O(n).

Example:
Input: S = "ADOBECODEBANC", T = "ABC"
Output: "BANC"

Note:
If there is no such window in S that covers all characters in T, return the empty string "".
If there is such window, you are guaranteed that there will always be only one unique minimum window in S.
```

### 代码
```
class Solution {
public:
    string minWindow(string s, string t) {
        string ans = "";
        vector<int> letter_count(128, 0);        
        for (char c : t)
            letter_count[c]++;
        
        int left = 0;
        int count = 0; 
        int minLen = s.size()+1;
        
        for (int i = 0; i < s.size() ; i++){
            if(letter_count[s[i]] > 0)
                count++;
            letter_count[s[i]]--;
            
            while(count == t.size()){
                if(minLen > i - left + 1){
                    minLen = i - left + 1;
                    ans = s.substr(left, minLen);
                }
                
                ++letter_count[s[left]];
                if(letter_count[s[left++]] > 0){
                    --count;
                }
            }
        }
        return ans;
    }
};
```

## - Longest Substring Without Repeating Characters

### 代码
```
class Solution {
public:
    int lengthOfLongestSubstring(string s) 
    {
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

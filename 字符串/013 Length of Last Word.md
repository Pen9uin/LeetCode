## - 58 Length of Last Word

### 描述
```
Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length
of last word in the string.
If the last word does not exist, return 0.
Note: A word is defined as a character sequence consists of non-space characters only.
For example, Given s = "Hello World", return 5.
```

### 代码1
```C++
class Solution {
public:
    int lengthOfLastWord(string s) {
        int right = s.size() - 1, res = 0;
        while (right >= 0 && s[right] == ' ') --right;
        while (right >= 0 && s[right] != ' ' ) {
            --right; 
            ++res;
        }
        return res;
    }
};
```

### 代码2
```C++
class Solution {
public:
    int lengthOfLastWord(const char *s) {
        int len = strlen(s);
        int left = 0;
        int right = len - 1;
        int count = 0;
        while (s[left] == ' ') ++left;
        while (s[right] == ' ') --right;
        for (int i = left; i <= right; ++i) {
            if (s[i] == ' ') count = 0;
            else ++count;
        }
        return count;
    }
};
```

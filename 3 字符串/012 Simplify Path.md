## - 71 Simplify Path

### 描述
```
  Given an absolute path for a file (Unix-style), simplify it.
  For example,
path = "/home/", => "/home"
path = "/a/./b/../../c/", => "/c"

Corner Cases:
• Did you consider the case where path = "/../"? In this case, you should return "/".
• Another corner case is the path might contain multiple slashes '/' together, such as "/home//foo/".
In this case, you should ignore redundant slashes and return "/home/foo".
```

### 代码
```C++
class Solution {
public:
    string simplifyPath(string path) {
        string res, tmp;
        vector<string> stk;
        stringstream ss(path);
        while(getline(ss,tmp,'/')) {
            //tmp == "" when occurs '//' or path[0] = '/'
            if (tmp == "" || tmp == ".")
                continue;
            if (tmp == ".." && !stk.empty()) 
                stk.pop_back();
            else if (tmp != "..") 
                stk.push_back(tmp);
        }
        for(auto str : stk)
            res += "/"+str;
        return res.empty() ? "/" : res;
    }
};
```


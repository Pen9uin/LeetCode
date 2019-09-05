## - Jump Game

### 描述

```
Given an array of non-negative integers, you are initially positioned at the first index of the array.
Each element in the array represents your maximum jump length at that position.
Determine if you are able to reach the last index.

For example:
A = [2,3,1,1,4], return true.
A = [3,2,1,0,4], return false.
```

### 分析

由于每层最多可以跳 A[i] 步，也可以跳 0 或 1 步，因此如果能到达最高层，则说明每一层都可以到达。有了这个条件，说明可以用贪心法。

思路一：从 0 出发，一层一层往上跳，看最后能不能超过最高层，能超过，说明能到达，否则不能到达。

思路二：用动规，设状态为 f[i]，表示从第 0 层出发，走到 A[i] 时剩余的最大步数，则状态转移方程为：

    f[i] = max(f[i-1], A[i-1])-1, i > 0

### 代码1
```
class Solution {
public:
    bool canJump(const vector<int>& nums) {
        int reach = 1; // 最右能跳到哪里
        for (int i = 0; i < reach && reach < nums.size(); ++i)
            reach = max(reach,  i + 1 + nums[i]);
        return reach >= nums.size();
    }
};
````

### 代码2
```
class Solution {
public:
    bool canJump(vector<int>& nums) {
        vector<int> dp(nums.size(), 0);
        for (int i = 1; i < nums.size(); ++i) 
        {
            dp[i] = max(dp[i - 1], nums[i - 1]) - 1;
            if (dp[i] < 0)
                return false;
        }
        return true;
    }
};
```




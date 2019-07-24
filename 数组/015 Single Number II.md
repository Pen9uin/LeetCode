## - Single Number II

### 描述

```
    Given an array of integers, every element appears three times except for one. Find that single one.
    Note: Your algorithm should have a linear runtime complexity. Could you implement it without using
extra memory?
```

### 代码
```C++
时间复杂度O(n)，空间复杂度O(1)
class Solution {
public:
    int singleNumber(vector<int>& nums) 
    {
        const int W = sizeof(int) * 8; // 一个整数的bit数，即整数字长
        int count[W];  // count[i]表示在在i位出现的1的次数
        fill_n(&count[0], W, 0);
        for (int i = 0; i < nums.size(); i++) 
            for (int j = 0; j < W; j++) 
                count[j] += (nums[i] >> j) & 1;

        int result = 0;
        for (int i = 0; i < W; i++) 
        {
            if(count[j] %3 != 0)
                result += (count[i] << i);
        }
        return result;
    }
};
```

## - Remove Duplicates from Sorted Array

### 题目描述

```
Given a sorted array, remove the duplicates in place such that each element appear only once
and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.
For example, Given input array A = [1,1,2],

Your function should return length = 2, and A is now [1,2].

时间复杂度O(n),空间复杂度O(1)
```

### 参考答案

```C++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) 
    {
        if (nums.empty()) return 0;
        int index = 0;
        for (int i = 1; i < nums.size(); i++) 
        {
            if (nums[index] != nums[i])
                nums[++index] = nums[i];
        }
        return index + 1;
    }
};
```

## -Remove Duplicates from Sorted Array II

### 题目描述

```
Follow up for ”Remove Duplicates”: What if duplicates are allowed at most twice?
For example, Given sorted array A = [1,1,1,2,2,3],
Your function should return length = 5, and A is now [1,1,2,2,3]
```

### 参考答案

```C++
class Solution {
public:
    int removeDuplicates(vector<int>& nums)
    {
        if (nums.size() <= 2) return nums.size();
        int index = 2;
        for (int i = 2; i < nums.size(); i++)
        {
            if (nums[i] != nums[index - 2])
                nums[index++] = nums[i];
        }
        return index;
    }
};
```











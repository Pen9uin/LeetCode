## - Two Sum

### 描述

```
    Given an array of integers, find two numbers such that they add up to a specific target number.
    The function twoSum should return indices of the two numbers such that they add up to the target, where
index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not
zero-based.
    You may assume that each input would have exactly one solution.
    Input: numbers={2, 7, 11, 15}, target=9
    Output: index1=1, index2=2
```

### 代码

```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int n = nums.size(), l = 0, r = n - 1;
        unordered_map<int, int> mp;
        for (int i = 0; i < n; i++) {
            if (mp.find(target - nums[i]) != mp.end()) {
                l = mp[target - nums[i]];
                r = i;
                break;
            }
            mp[nums[i]] = i;
        }
        return {l, r};
    }
};
```

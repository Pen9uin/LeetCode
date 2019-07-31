## - Trapping Rain Water

### 描述

```
  Given n non-negative integers representing an elevation map where the width of each bar is 1, compute
how much water it is able to trap after raining.
  For example, Given [0,1,0,2,1,0,1,3,2,1,2,1], return 6.
```

![Trapping Rain Water](https://github.com/soulmachine/leetcode/blob/master/C++/images/trapping-rain-water.png?raw=true)

### 分析

对于每个柱子，找到其左右两边最高的柱子，该柱子能容纳的面积就是  min(max_left, max_right) - height 。所以，
1. 从左往右扫描一遍，对于每个柱子，求取左边最大值；
2. 从右往左扫描一遍，对于每个柱子，求最大右值；
3. 再扫描一遍，把每个柱子的面积并累加。

也可以，
1. 扫描一遍，找到最高的柱子，这个柱子将数组分为两半；
2. 处理左边一半；
3. 处理右边一半。

### 代码1
```C++
// 思路1，时间复杂度O(n)，空间复杂度O(n)
class Solution {
public:
    int trap(const vector<int>& A) 
    {
        const int n = A.size();
        vector<int> max_left(n,0); //初始为0
        vector<int> max_right(n,0);

        for (int i = 1; i < n; i++) {
            max_left[i] = max(max_left[i - 1], A[i - 1]);
            max_right[n - 1 - i] = max(max_right[n - i], A[n - i]);

        }

        int sum = 0;
        for (int i = 0; i < n; i++) {
            int height = min(max_left[i], max_right[i]);
            if (height > A[i])
                sum += height - A[i];
        }

        return sum;
    }
};
```

### 代码2
```C++
// 思路2，时间复杂度O(n)，空间复杂度O(1)
class Solution {
public:
    int trap(const vector<int>& A) 
    {
        const int n = A.size();
        int max = 0; // 最高的柱子，将数组分为两半
        for (int i = 0; i < n; i++)
            if (A[i] > A[max]) max = i;

        int water = 0;
        for (int i = 0, peak = 0; i < max; i++)
            if (A[i] > peak) peak = A[i];
            else water += peak - A[i];
        for (int i = n - 1, top = 0; i > max; i--)
            if (A[i] > top) top = A[i];
            else water += top - A[i];
        return water;
    }
};
```

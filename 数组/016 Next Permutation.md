## - Next Permutation

### 描述

```
    Implement next permutation, which rearranges numbers into the lexicographically next greater permutation
of numbers.
    If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending
order).
    The replacement must be in-place, do not allocate extra memory.
    Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the
right-hand column.
    1,2,3 → 1,3,2
    3,2,1 → 1,2,3
    1,1,5 → 1,5,1
```

### 分析

我们再来看下面一个例子，有如下的一个数组

1　　2　　7　　4　　3　　1

下一个排列为：

1　　3　　1　　2　　4　　7

那么是如何得到的呢，我们通过观察原数组可以发现，如果从末尾往前看，数字逐渐变大，到了2时才减小的，称改点为**替换点**然后我们再从后往前找第一个比2大的数字，是3，那么我们交换2和3，再把此时**替换点**后面的所有数字转置一下即可，步骤如下：

1　　``2``　　7　　4　 　3　　  1

1　　``2``　　7　　4　　``3``　　1

1　　``3``　　7　　4　　``2``　　1

1　　 3　　``1　　 2　　 4　　    7``

### 代码1

```C++
class Solution {
public:
    void nextPermutation(vector<int> &num) {
        int i, j, n = num.size();
        for (i = n - 2; i >= 0; --i)
        {
            if (num[i + 1] > num[i]) 
            {
                for (j = n - 1; j > i; --j)
                    if (num[j] > num[i]) break;
                    
                swap(num[i], num[j]);
                reverse(num.begin() + i + 1, num.end());
                return;
            }
        }
        reverse(num.begin(), num.end());
    }
};
```

### 代码2

```C++
class Solution {
public:
    void nextPermutation(vector<int>& nums) 
    {
        int n = nums.size(), i = n - 2,;
        while (i >= 0 && nums[i] >= nums[i + 1]) 
            --i;
        if (i >= 0) {
            int j = n - 1;
            while (nums[j] <= nums[i]) --j;
            swap(nums[i], nums[j]);
        }
        reverse(nums.begin() + i + 1, nums.end());
    }
};
```

### 参考

https://www.cnblogs.com/grandyang/p/4428207.html

https://blog.csdn.net/MoreWindows/article/details/7370155










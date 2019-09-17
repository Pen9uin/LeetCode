## - 84 Largest Rectangle in Histogram

### 描述
```
    Given n non-negative integers representing the histogram’s bar height where the width of each bar is 1,
find the area of largest rectangle in the histogram.
```

![](https://github.com/Pen9uin/LeetCode/blob/master/imgs/Largest%20Rectangle%20in%20Histogram%201.png)

```
Above is a histogram where width of each bar is 1, given height = [2,1,5,6,2,3].
```

![](https://github.com/Pen9uin/LeetCode/blob/master/imgs/Largest%20Rectangle%20in%20Histogram%202.png)

```
The largest rectangle is shown in the shaded area, which has area = 10 unit.

For example, Given height = [2,1,5,6,2,3], return 10.
```

### 分析

1. 遍历数组，每找到一个局部峰值（只要当前的数字大于后面的一个数字，那么当前数字就看作一个局部峰值，跟前面的数字大小无关），然后向前遍历所有的值，算出共同的矩形面积，每次对比保留最大值。。

2. 使用栈

### 代码1
```C++
class Solution {
public:
    int largestRectangleArea(vector<int> &height) {
        int res = 0;
        for (int i = 0; i < height.size(); ++i) 
        {
            if (i + 1 < height.size() && height[i] <= height[i + 1])
                continue;
            
            int minH = height[i];
            for (int j = i; j >= 0; --j) {
                minH = min(minH, height[j]);
                int area = minH * (i - j + 1);
                res = max(res, area);
            }
        }
        return res;
    }
};
```

### 代码2
```C++
class Solution {
public:
    int largestRectangleArea(vector<int> &height) {
        int res = 0;
        stack<int> st;
        height.push_back(0);
        for (int i = 0; i < height.size(); ++i) {
            if (st.empty() || height[st.top()] < height[i]) {
                st.push(i);
            } else {
                int cur = st.top(); st.pop();
                res = max(res, height[cur] * (st.empty() ? i : (i - st.top() - 1)));
                --i;
            }     
        }
        return res;
    }
};
```

### 参考

https://www.cnblogs.com/grandyang/p/4322653.html

https://www.cnblogs.com/lichen782/p/leetcode_Largest_Rectangle_in_Histogram.html


## - Best Time to Buy and Sell Stock III

### 描述
```
Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete at most two transactions.

Note: You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).
```

### 代码
```
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        length = len(prices)
        if length==0: 
            return 0
        f1 = [0 for __ in range(length)]
        f2 = [0 for __ in range(length)]
        # 从前往后最大利润
        minPrice = prices[0]
        for i in range(1, length):
            f1[i] = max(f1[i-1], prices[i]-minPrice)
            minPrice=min(minPrice, prices[i])
        # 从后往前则是最小利润
        maxPrice = prices[length-1]
        for i in range(length-2,-1,-1):
            f2[i] = max(f2[i+1], maxPrice-prices[i])
            maxPrice = max(maxPrice, prices[i])

        maxProfit=0
        for i in range(length):
            if f1[i]+f2[i] > maxProfit: 
                maxProfit = f1[i]+f2[i]
        return maxProfit
```

### 参考

https://blog.csdn.net/qqxx6661/article/details/78463652

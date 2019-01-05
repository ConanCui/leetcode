# 121. Best Time to Buy and Sell Stock

Easy

Say you have an array for which the *i*th element is the price of a given stock on day *i*.

If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.

Note that you cannot sell a stock before you buy one.

**Example 1:**

```
Input: [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
             Not 7-1 = 6, as selling price needs to be larger than buying price.
```

**Example 2:**

```
Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

# 思路：



对每天的价格遍历一遍，实时更新最小值，并每天的价格和当前最小值做差，和当前最大的profit取max。因为最大的利润会在valley和peak之差出现。我们不能反过来不停的实时更新peak，拿当前的价格和peak做差，因为股票是先购买，再抛售，所以只能先找valley，再一个一个试peak。



# 解题：



```python
class Solution:
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        valley = float('inf')
        profit = 0
        
        for i, price in enumerate(prices):
            valley = min(valley, price)
            profit = max(profit, price - valley)
            
        return profit
            
        
```

其他解题：

```python

```


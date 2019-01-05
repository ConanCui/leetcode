# Remove Linked List Elements

Easy

You are climbing a stair case. It takes *n* steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**Note:** Given *n* will be a positive integer.

**Example 1:**

```
Input: 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```

**Example 2:**

```
Input: 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

# 思路：

Fibonacci number, 

Fib(n)=Fib(n−1)+Fib(n−2)

所以只需要三个变量来记录，空间复杂度为$O(1)$，时间复杂度为$O(n)$。还有时间复杂度更小的算法，日后再学。

# 解题：



```python
class Solution:
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n == 1:
            return 1
        
        first = 1
        second = 2
        
        for i in range(2,n):
            
            third = first + second
            first = second 
            second = third
            
        return second
```

其他解题：

```python

```


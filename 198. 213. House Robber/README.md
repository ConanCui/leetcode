# 198. House Robber

Easy

ou are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and **it will automatically contact the police if two adjacent houses were broken into on the same night**.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight **without alerting the police**.

**Example 1:**

```
Input: [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
             Total amount you can rob = 1 + 3 = 4.
```

**Example 2:**

```
Input: [2,7,9,3,1]
Output: 12
Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
             Total amount you can rob = 2 + 9 + 1 = 12.
```

# 思路：

这是一道动态规划的题目，我们需要找出题目当中的 recursive 关系。

对于robber，面对房子i，他有两个选择，抢或不抢。如果抢房子i的话，i-1的房子就不能抢了。如果不抢的话，则他可以抢房子i-1。所以面对房子i，如何将利益rob(i)最大化？两种选择分别对应的利益为

- 抢：rob(i-2) + 房子i的value
- 不抢：rob(i-1)

所以房子i的价值可以通过如下递推关系来表达：

$$rob(i) = max(rob(i-2) + current\_house\_value, rob(i-1))$$

这样的话，保证每一步都是再做利益最大化的选择(贪心的感觉？)。我们观察上边的递推，发现当前的价值仅仅和前两步有关系，所以只需要两个变量即可，有点类似斐波那契数的感觉，所以空间复杂度为$O(1)$，时间复杂度为$O(n)$.

# 解题：



```python
class Solution:
    def rob(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return 0
        # 最开始的两个节点应该是为0，因为从第一家房子开始算，前边没有抢，所以为0
        rob_first = 0
        rob_second = 0
        
        for i in range(0,len(nums)):
            rob_i = max(rob_first + nums[i], rob_second)
            rob_first = rob_second
            rob_second = rob_i
        
        return rob_i
```

其他解题：

```python

```

# 213. House Robber

Medium

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are **arranged in a circle.** That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have security system connected and **it will automatically contact the police if two adjacent houses were broken into on the same night**.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight **without alerting the police**.

**Example 1:**

```
Input: [2,3,2]
Output: 3
Explanation: You cannot rob house 1 (money = 2) and then rob house 3 (money = 2),
             because they are adjacent houses.
```

**Example 2:**

```
Input: [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
             Total amount you can rob = 1 + 3 = 4.
```

# 思路：

相比于上一题，这里对房子的顺序更加苛刻，房子由row的排列顺序变成了一个circle，即首尾也算作邻居。但是我们可以把这个circle蜕化到row。如1，2，3，4四座房子，房子1和房子4相邻。如果1可以被rob，那么4不能被rob，则我们仅考虑1，2，3这个row。如果4可以被rob，那么1不能被rob，因此仅考虑2，3，4这个row。

# 解题：



```python
class Solution:
    def rob(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if  len(nums) ==1:
            return nums[0]
        
        return max(self.rob_rows(nums[1:]), self.rob_rows(nums[:-1]))
    
    
    def rob_rows(self,nums):
        # 抢rows的房子
        if not nums:
            return 0
        # 最开始的两个节点应该是为0，因为从第一家房子开始算，前边没有抢，所以为0
        rob_first = 0
        rob_second = 0
        
        for i in range(0,len(nums)):
            rob_i = max(rob_first + nums[i], rob_second)
            rob_first = rob_second
            rob_second = rob_i
        
        return rob_i
```

其他解题：

```python

```


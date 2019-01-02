# Two sum

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target. You may assume that each input would have **exactly** one solution, and you may not use the *same* element twice.

**Example:**

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```



# 思路：

建立一个哈希表，key是 target- num， value是num的index。因为需要对整个list进行遍历，建立哈希表，所以空间复杂度为$O(n)$，而哈希表的查询时间为$O(1)$，所以对整个list遍历的空间复杂度为$O(n)$。

# 解题：

```python
class Solution:
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        buffer_dict = {}
        for i, num in enumerate(nums):
            
            if num in buffer_dict.keys():
                return [buffer_dict[num], i]
            else:
                buffer_dict[target-num] = i
                
```


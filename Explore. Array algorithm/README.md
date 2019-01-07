# [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)

Easy

Given an array `nums`, write a function to move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

**Example:**

```
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```

**Note**:

1. You must do this **in-place** without making a copy of the array.
2. Minimize the total number of operations.

# 思路：

利用双指针问题，一个指针a用来遍历数组，另外一个指针b在遍历时，用来记录最后一个非零元素的位置。因为 a>=b, 遍历时，遇到非零元素，交换数组两个位置的值即可把非零元素置前。

# 解题：



```python
class Solution:
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        
        NonZeroPoint = 0

        
        for CurPoint in range(len(nums)):
            if nums[CurPoint] != 0:
                nums[CurPoint], nums[NonZeroPoint] = nums[NonZeroPoint], nums[CurPoint]
                NonZeroPoint = NonZeroPoint + 1
                
```



# [283. Remove Element](https://leetcode.com/problems/remove-element/)

Easy

1. Given an array *nums* and a value *val*, remove all instances of that value [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) and return the new length.

   Do not allocate extra space for another array, you must do this by **modifying the input array in-place** with O(1) extra memory.

   The order of elements can be changed. It doesn't matter what you leave beyond the new length.

   **Example 1:**

   ```
   Given nums = [3,2,2,3], val = 3,
   
   Your function should return length = 2, with the first two elements of nums being 2.
   
   It doesn't matter what you leave beyond the returned length.
   ```

   **Example 2:**

   ```
   Given nums = [0,1,2,2,3,0,4,2], val = 2,
   
   Your function should return length = 5, with the first five elements of nums containing 0, 1, 3, 0, and 4.
   
   Note that the order of those five elements can be arbitrary.
   
   It doesn't matter what values are set beyond the returned length.
   ```

# 思路：

可以像上一个题目一样，只不过这里的零变成了某个特定的元素罢了



# 解题：



```python
class Solution:
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        
        nz_point = 0
        for cur_point in range(len(nums)):
            if nums[cur_point] != val:
                nums[cur_point], nums[nz_point] = nums[nz_point], nums[cur_point]
                nz_point = nz_point + 1
        return nz_point

                
```





# [26. Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

Easy

Given a sorted array *nums*, remove the duplicates [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) such that each element appear only *once* and return the new length.

Do not allocate extra space for another array, you must do this by **modifying the input array in-place** with O(1) extra memory.

**Example 1:**

```
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.

It doesn't matter what you leave beyond the returned length.
```

**Example 2:**

```
Given nums = [0,0,1,1,1,2,2,3,3,4],

Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively.

It doesn't matter what values are set beyond the returned length.
```

# 思路：

 还是利用双指针，不同点在于我们对于第二个指针unique_point的累加方式变得不同了。具体累加方式可见下算法中，我们这里的判断条件由if nums[cur_point] != val: 变为if nums[cur_point] != last_value:。 last_value记录了上个不同的值，因此只有当出现新的不同的值，我们才会数组操作，对值进行交换。



# 解题：



```python
 class Solution:
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        unique_point = 0
        last_value = None
        
        for cur_point in range(len(nums)):
            if nums[cur_point] != last_value:
                last_value = nums[cur_point]
                nums[cur_point], nums[unique_point] = nums[unique_point], nums[cur_point]
                unique_point = unique_point + 1
        return unique_point
```


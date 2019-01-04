# Add Two Numbers 

Medium

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order** and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example:**

```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```



# 思路：

两个数加和，计算规则为每一位上的两个数超过10则进一位。需要对两个数的每一位进行便遍历，两个数的位数可能不一致，所以时间复杂度为$O(max(n,m))$。同时还需要创建一个链表用来存储结果，所以空间复杂度为$O(max(n,m))$。

# 解题：

```python
class Solution:
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        result_list = next_list = ListNode(0)
        carry = 0
        
        while l1 or l2 or carry:
            
            val = carry
            if l1:
                val = l1.val + val
                l1 = l1.next
            if l2:
                val = l2.val + val
                l2 = l2.next
                
            carry = 0
            
            if val>=10:
                carry = 1
                val = val -10
            
            next_list.next = ListNode(val)
            next_list = next_list.next
        
        return result_list.next
```


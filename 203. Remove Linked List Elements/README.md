# Remove Linked List Elements

Easy

Remove all elements from a linked list of integers that have value **val**.

**Example:**

```
Input:  1->2->6->3->4->5->6, val = 6
Output: 1->2->3->4->5
```



# 思路：

关于链表的题目，常见的作法有，在链表头再添加一个节点，然后制作两个指针，分别指向前一个节点和当前节点，对整个链表进行遍历。如果碰到需要删除的节点，那么让上一个节点跳过当前节点，直接指向下一个节点即可。时间复杂度为$O(n)$，空间复杂度为$O(1)$.

# 解题：



```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def removeElements(self, head, val):
        """
        :type head: ListNode
        :type val: int
        :rtype: ListNode
        """

        dummy = ListNode(-1)
        dummy.next = head
        
        pre = dummy
        cur = dummy.next
        
        while cur:
            if cur.val == val:
                cur = cur.next
                pre.next = cur
            else:
                pre = pre.next
                cur = cur.next
        
        return dummy.next
                
```

其他解题：

```python

```


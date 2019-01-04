# Palindrome Linked List

Easy

Given a singly linked list, determine if it is a palindrome.

**Example 1:**

```
Input: 1->2
Output: false
```

**Example 2:**

```
Input: 1->2->2->1
Output: true
```

**Follow up:**
Could you do it in O(n) time and O(1) space?

# 思路：

关于回文串的判断，可以通过双指针来判断。大致思路为：如果我们将字符串的前半段进行反转，将其与后半段进行一一对比即可。

具体实现思路为：

- 第一阶段：设定一个快指针和慢指针，让快指针以每次跳两个点的速度，慢指针以每次跳一个点的速度，这样快指针到达字符串末尾时，慢指针恰好到达字符串中间(如果字符串为奇数，要求跨过中间点)，在此同时，恰好完成对前半段字符串的反转。

- 第二阶段：将反转后的字符串和慢指针进行一一对比。

```python
class Solution:
    def isPalindrome(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        rev = None
        slow = fast = head
        
        # 第一阶段
        while fast and fast.next:
            fast = fast.next.next
            
            # 这样的tuple assignment，前两个实现为反转，后一个即为slow向后移动一位，需要特别注意，slow指针的重新赋值(slow = slow.next)不会影响到rev=slow
            rev, rev.next, slow = slow, rev, slow.next 
        
        # 用来将slow跨过middle点
        if fast:
            slow = slow.next
        
        # 将前半段字符串反转后，和后半段字符串进行一一对比
        while rev and rev.val == slow.val:
            slow = slow.next
            rev = rev.next
        
        return not rev
```



相同的思路，不同的实现方式，可以参考其字符串是如何反转的

```python
class Solution:
    def isPalindrome(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        # find length of the list
        # reverse first half of the list
        # compare
        
        
        if not head or not head.next:
            return True
        
        # find length
        pointer = head
        length = 0
        while pointer:
            pointer = pointer.next
            length += 1
            
        # reverse first half of the ll
        prev = None
        curr = head
        for i in range(length//2):
            next = curr.next
            curr.next = prev
            prev = curr
            curr = next
            
        firstPointer = prev
        secondPointer = curr
        
        # skip first element of second ll if length is odd
        if length % 2 != 0:
            secondPointer = secondPointer.next
        
        # compare the two ll's
        for i in range(length//2):
            if firstPointer.val != secondPointer.val:
                return False
            firstPointer = firstPointer.next
            secondPointer = secondPointer.next
            
        return True
```



# 解题：



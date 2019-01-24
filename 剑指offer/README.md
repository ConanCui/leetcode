# 56 .  数组中出现的次数



https://www.cnblogs.com/CarrieCui/p/5119597.html

https://blog.csdn.net/yl_mouse/article/details/80576263

https://blog.csdn.net/Koala_Tree/article/details/79617607





## # 18. 题目描述



在一个排序的链表中，存在重复的结点，请删除该链表中重复的结点，重复的结点不保留，返回链表头指针。 例如，链表1->2->3->3->4->4->5 处理后为 1->2->5

```python
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution:
    def deleteDuplication(self, pHead):
        # write code here
        if pHead == None or pHead.next == None:
            return pHead
        
        next = pHead.next
        if pHead.val == next.val:
            while next != None and pHead.val == next.val:
                next = next.next
            # 始终让前一个节点和后面比当前节点值大的节点相连
            return self.deleteDuplication(next) 
        else:
            # 始终让前一个节点和后面比当前节点值大的节点相连
            pHead.next = self.deleteDuplication(next)
            return pHead
```



数组：

面试题3：数组中重复的数字 (p41) (n个数字，在0~n-1范围内。对应值放在数组中对应位置。或者类似二分查找)

面试题4：二维数组中的查找  (从右上角或者左下脚移动行坐标和列坐标)

面试题5：替换空格（从后向前，双指针解法，和合并数组等算法一样，从后往前比较方便）

面试题6：从尾到头打印链表（用栈实现即可）

面试题7：重建二叉树（preorder确定root，inorder确定左子树和右子树节点个数，递归实现）

面试题8：二叉树下一个节点（中序遍历的下一个节点，分情况讨论，会给指向父节点指针）

面试题9：用两个栈实现队列（举例子找规律）

面试题10：斐波那契数列（青蛙跳台阶，一次可以跳n，数学归纳共2^(n-1)）

面试题11：旋转数组的最小数字 （二分查找的改进版，需要注意特别例子）



面试题14：剪绳子（动态规划，问题分解为子问题，自下而上）

面试题15：二进制中1的个数（把一个整数减去1，再和原整数做与运算，会把该整数最右边的1变为0）

面试题18：删除链表的节点（在O(1) 时间内删除，考虑用下个节点内容覆盖要删除节点，如果要删除的是末尾指针需要特别注意）



面试题21：调整数组顺序使奇数位于偶数前面（双指针实现，一个指向头部，一个指向尾部）







双指针：

面试题 22：链表中倒数第k个结点 （一个指针比另外一个慢k步即可，需要特别注意）

面试题18：删除排序链表中的重复节点 （确保每一个prenode始终与下一个没有重复的节点连接在一起）

面试题24：[反转链表](https://leetcode.com/problems/reverse-linked-list/solution/)（三个指针，把当前指针指向前一个结点前，需要先把右边的节点取出来，否则会断开）





面试题24：[反转链表](https://leetcode.com/problems/reverse-linked-list/solution/)

面试题25:  [合并两个有序链表](https://leetcode.com/problems/merge-two-sorted-lists/)（迭代或者递归都可解决，）

面试题26 (p148): [树的子结构](https://leetcode.com/problems/subtree-of-another-tree/solution/)

面试题27 (p157):  二叉树的镜像 (交换每个节点的两个子节点)

面试题28 (p159): [对称的二叉树](https://leetcode.com/problems/symmetric-tree/) BFS(观察树的例子，root.right.value == root.left.value)

面试题29 (161): 顺时针打印矩阵（画图，按照circle来进行打印）

面试题30 (p165): 包含min函数的栈 （辅助栈压入当前最小值）

面试题31 (p168): 栈的压入、弹出序列 （举例子，找出规律，用一个辅助栈来模拟）

面试题32 (p171): [ 从上到下打印二叉树 ](https://www.nowcoder.com/practice/91b69814117f4e8097390d107d2efbe0?tpId=13&tqId=11212&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)(使用队列容器来对树遍历，之字形打印需要两个stack)

![1547177876683](C:\Users\kncue\AppData\Roaming\Typora\typora-user-images\1547177876683.png)

面试题33：二叉搜索树的后序遍历序列（递归解法，后序遍历的特点是root在尾，并且root值大于左子树节点值，大于右子树节点值）

面试题34：二叉树中和为某一值的路径（要求打印出来路径，可以用递归完成前序遍历）

![1547182122211](C:\Users\kncue\AppData\Roaming\Typora\typora-user-images\1547182122211.png)
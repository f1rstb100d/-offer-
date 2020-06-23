剑指 Offer 52. 两个链表的第一个公共节点


输入两个链表，找出它们的第一个公共节点。

示例 1：
```
输入：intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3
输出：Reference of the node with value = 8
输入解释：相交节点的值为 8 （注意，如果两个列表相交则不能为 0）。从各自的表头开始算起，链表 A 为 [4,1,8,4,5]，链表 B 为 [5,0,1,8,4,5]。在 A 中，相交节点前有 2 个节点；在 B 中，相交节点前有 3 个节点。
 ```
示例 2：
```
输入：intersectVal = 2, listA = [0,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
输出：Reference of the node with value = 2
输入解释：相交节点的值为 2 （注意，如果两个列表相交则不能为 0）。从各自的表头开始算起，链表 A 为 [0,9,1,2,4]，链表 B 为 [3,2,4]。在 A 中，相交节点前有 3 个节点；在 B 中，相交节点前有 1 个节点。
```
示例 3：
```
输入：intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
输出：null
输入解释：从各自的表头开始算起，链表 A 为 [2,6,4]，链表 B 为 [1,5]。由于这两个链表不相交，所以 intersectVal 必须为 0，而 skipA 和 skipB 可以是任意值。
解释：这两个链表不相交，因此返回 null。
```

[题目链接](https://leetcode-cn.com/problems/liang-ge-lian-biao-de-di-yi-ge-gong-gong-jie-dian-lcof/)

```
1. 先从头到尾遍历一遍链表，统计出各自的长度
2. 把长的链表向后缩，使两个链表一样长，分别对比每一个节点，遇到第一个相同指针就输出，否则到结尾还没有就输出None
```

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        tmpA = headA
        tmpB = headB
        lenA = 0
        lenB = 0
        while tmpA:
            lenA += 1
            tmpA = tmpA.next
        while tmpB:
            lenB += 1
            tmpB = tmpB.next
        
        if(lenB>lenA):
            gap = lenB-lenA
            for _ in range(gap):
                headB = headB.next
            while headA and headB:
                if(headA == headB):
                    return headA
                else:
                    headA = headA.next
                    headB = headB.next
            return None

        elif(lenA>lenB):
            gap = lenA-lenB
            for _ in range(gap):
                headA = headA.next
            while headA and headB:
                if(headA == headB):
                    return headA
                else:
                    headA = headA.next
                    headB = headB.next
            return None

        else:
            while headA and headB:
                if(headA == headB):
                    return headA
                else:
                    headA = headA.next
                    headB = headB.next
            return None
```
剑指 Offer 54. 二叉搜索树的第k大节点

给定一棵二叉搜索树，请找出其中第k大的节点。
```
示例 1:

输入: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
输出: 4
```
示例 2:
```
输入: root = [5,3,6,2,4,null,null,1], k = 3
       5
      / \
     3   6
    / \
   2   4
  /
 1
输出: 4
```

[题目链接](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)

```
题目已经说了这是二叉搜索树，所以中序遍历的序列就是递增的，要第k大的节点，就返回递增数列的倒数第k个
```

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def traverseInOrder(self, root):
        if root.left:
            self.traverseInOrder(root.left)
        self.L.append(root.val)
        if root.right:
            self.traverseInOrder(root.right)

    def kthLargest(self, root: TreeNode, k: int) -> int:
        self.L = []
        if root:
            self.traverseInOrder(root)
        return self.L[-k]
```
剑指 Offer 28. 对称的二叉树


请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。
```
例如，二叉树 [1,2,2,3,4,4,3] 是对称的。

    1
   / \
  2   2
 / \ / \
3  4 4  3
但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:

    1
   / \
  2   2
   \   \
   3    3
```
示例 1：
```
输入：root = [1,2,2,3,4,4,3]
输出：true
```
示例 2：
```
输入：root = [1,2,2,null,3,null,3]
输出：false
```

[题目链接](https://leetcode-cn.com/problems/dui-cheng-de-er-cha-shu-lcof/)

```
判断左子树与右子树的翻转是不是同一棵树
使用递归判断左子树的左节点是否和右子树的右节点相同，判断左子树的右节点是否和右子树的左节点相同
```

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isSameTree(self, p, q):
        if not p and not q: return True
        if p and q and p.val == q.val:
        	# 注意 left 和 right 进行了交换
            return self.isSameTree(p.left,q.right) and self.isSameTree(p.right,q.left)
        
        return False

    def isSymmetric(self, root: TreeNode) -> bool:
        if not root: 
            return True
        else:
            return self.isSameTree(root.left, root.right)
```
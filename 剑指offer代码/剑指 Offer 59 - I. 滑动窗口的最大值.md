剑指 Offer 59 - I. 滑动窗口的最大值


给定一个数组 nums 和滑动窗口的大小 k，请找出所有滑动窗口里的最大值。

示例:
```
输入: nums = [1,3,-1,-3,5,3,6,7], 和 k = 3
输出: [3,3,5,5,6,7] 
解释: 

  滑动窗口的位置                最大值
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
```

[题目链接](https://leetcode-cn.com/problems/hua-dong-chuang-kou-de-zui-da-zhi-lcof/)

```
1. 求前k个数的最大值，放到最后结果L中
2. 往后逐个遍历，去掉临时滑动窗的第一个数字，后面加上刚遍历的数字，再求临时数组的最大值，添加到L中
```

```python
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        if not nums:
            return []
        temp = []
        L = []
        for i in range(k):
            temp.append(nums[i])
        L.append(max(temp))
        for i in range(k, len(nums)):
            temp = temp[1:]
            temp.append(nums[i])
            L.append(max(temp))
        return L
```
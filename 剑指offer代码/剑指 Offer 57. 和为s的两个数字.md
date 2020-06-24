剑指 Offer 57. 和为s的两个数字

输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可。

示例 1：
```
输入：nums = [2,7,11,15], target = 9
输出：[2,7] 或者 [7,2]
```
示例 2：
```
输入：nums = [10,26,30,31,47,60], target = 40
输出：[10,30] 或者 [30,10]
```

[题目链接](https://leetcode-cn.com/problems/he-wei-sde-liang-ge-shu-zi-lcof/)

```
因为list是递增的，使用头尾两个指针逐渐往中间缩，当两指针之和大于target时，说明后面的数大了，j要往中间减；当两指针之和小于target时，说明前面的数小了，i要往大里增，直到和为target
```

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        i = 0
        j = len(nums) - 1
        while i < j:
            sum = nums[i] + nums[j]
            if target > sum:
                i += 1
            elif target < sum:
                j -= 1
            else:
                return [nums[i],nums[j]]
```
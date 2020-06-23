剑指 Offer 53 - II. 0～n-1中缺失的数字


一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字。

示例 1:
```
输入: [0,1,3]
输出: 2
```
示例 2:
```
输入: [0,1,2,3,4,5,6,7,9]
输出: 8
```

[题目链接](https://leetcode-cn.com/problems/que-shi-de-shu-zi-lcof/)

```
因为提供的是递增数列，所以使用二分法更快
每个数组正确值应该和其编号一样
如果中间值正确，那么缺失点应该在后面；反之中间值错误，那么缺失点在前面
```

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        i = 0
        j = len(nums) - 1
        while(i<=j):
            mid = i + (j-i)//2
            if(nums[mid] != mid):
                j = mid - 1
            else:
                i = mid + 1
        return i
```
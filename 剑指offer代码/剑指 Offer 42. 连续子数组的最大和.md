剑指 Offer 42. 连续子数组的最大和


输入一个整型数组，数组里有正数也有负数。数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。

要求时间复杂度为O(n)。

示例1:
```
输入: nums = [-2,1,-3,4,-1,2,1,-5,4]
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```

[题目链接](https://leetcode-cn.com/problems/lian-xu-zi-shu-zu-de-zui-da-he-lcof/)

```
1. 一个当前和还有一个曾经最大的和
2. 把下一个值加进去，当当前和小于0，意味着要重新选择开始头，把当前和重置为0，取两个和较大值赋给曾经最大值
以[1,-2,3,10,-4,7,2,-5为例：
```
|  步骤   | 操作  |  累加的子数组和   | 最大的子数组和  |
|  ----  | ----  |  ----  | ----  |
| 1  | 加1 | 1  | 1 |
| 2  | 加-2 | -1  | 1 |
| 3  | 舍弃前面的和-1,加3 | 3  | 3 |
| 4  | 加10 | 13  | 13 |
| 5  | 加-4 | 9  | 13 |
| 6  | 加7 | 16  | 16 |
| 7  | 加2 | 18  | 18|
| 8  | 加-5 | 13  | 18 |

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        currSum, maxSum = 0, float('-inf')
        for num in nums:
            currSum = num + currSum
            maxSum = max(currSum, maxSum)
            if currSum < 0:
                currSum = 0
        return maxSum
```
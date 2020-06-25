剑指 Offer 57 - II. 和为s的连续正数序列


输入一个正整数 target ，输出所有和为 target 的连续正整数序列（至少含有两个数）。

序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。

示例 1：
```
输入：target = 9
输出：[[2,3,4],[4,5]]
```
示例 2：
```
输入：target = 15
输出：[[1,2,3,4,5],[4,5,6],[7,8]]
```

[题目链接](https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)

```
因为是连续的递增数列，定义两个指针，一个指队头，一个指队尾，当和小于target，队头往后移一位；当和大于target，队尾往后移一位；当和等于target，输出队尾到队头之前的数，然后队头往后移一位
```

```python
class Solution:
    def findContinuousSequence(self, target: int) -> List[List[int]]:
        i = 1
        j = 2
        s = i+j
        LL = []
        while i < j:
            if s<target:
                j += 1
                s += j
            elif s > target:
                i += 1
                s -= (i-1)
            else:
                L = []
                for num in range(i,j+1):
                    L.append(num)
                LL.append(L)
                j += 1
                s += j
        return LL
```
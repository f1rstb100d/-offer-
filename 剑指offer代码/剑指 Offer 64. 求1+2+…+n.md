剑指 Offer 64. 求1+2+…+n


求 1+2+...+n ，要求不能使用乘除法、for、while、if、else、switch、case等关键字及条件判断语句（A?B:C）。

示例 1：
```
输入: n = 3
输出: 6
```
示例 2：
```
输入: n = 9
输出: 45
```

[题目链接](https://leetcode-cn.com/problems/qiu-12n-lcof/)

```
利用递归+Python的and短路性质
如果x and y and z，当x，y，z都满足的情况下，python返回最后一个，即z
如果x and y and z，中间有None或0，返回第一个None或0的。比如3 and 0 and '', 返回0
```

```python
class Solution:
    def sumNums(self, n: int) -> int:
        def get_sum(n):
            # 当n大于0的时候，返回n + get_sum
            # 当n等于0的时候，返回0
            return n and n + get_sum(n - 1)
        return get_sum(n)
```
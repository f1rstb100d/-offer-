剑指 Offer 41. 数据流中的中位数


如何得到一个数据流中的中位数？如果从数据流中读出奇数个数值，那么中位数就是所有数值排序之后位于中间的数值。如果从数据流中读出偶数个数值，那么中位数就是所有数值排序之后中间两个数的平均值。

例如，

[2,3,4] 的中位数是 3

[2,3] 的中位数是 (2 + 3) / 2 = 2.5

设计一个支持以下两种操作的数据结构：

void addNum(int num) - 从数据流中添加一个整数到数据结构中。
double findMedian() - 返回目前所有元素的中位数。
示例 1：
```
输入：
["MedianFinder","addNum","addNum","findMedian","addNum","findMedian"]
[[],[1],[2],[],[3],[]]
输出：[null,null,null,1.50000,null,2.00000]
```
示例 2：
```
输入：
["MedianFinder","addNum","findMedian","addNum","findMedian"]
[[],[2],[],[3],[]]
输出：[null,null,2.00000,null,2.50000]
```

[题目链接](https://leetcode-cn.com/problems/shu-ju-liu-zhong-de-zhong-wei-shu-lcof/)

```
1. 逐个往list里添加数据
2. list排序，根据奇数个还是偶数个决定输出中间一位还是两位的平均值
```

```python
class MedianFinder:

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.L = []


    def addNum(self, num: int) -> None:
        self.L.append(num)


    def findMedian(self) -> float:
        self.L.sort()
        if(len(self.L)%2 == 0):
            return (self.L[len(self.L)//2]+self.L[(len(self.L)//2)-1])/2
        else:
            return self.L[(len(self.L)-1)//2]



# Your MedianFinder object will be instantiated and called as such:
# obj = MedianFinder()
# obj.addNum(num)
# param_2 = obj.findMedian()
```
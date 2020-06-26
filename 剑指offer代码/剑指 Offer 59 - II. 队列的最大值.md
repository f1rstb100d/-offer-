剑指 Offer 59 - II. 队列的最大值


请定义一个队列并实现函数 max_value 得到队列里的最大值，要求函数max_value、push_back 和 pop_front 的均摊时间复杂度都是O(1)。

若队列为空，pop_front 和 max_value 需要返回 -1

示例 1：
```
输入: 
["MaxQueue","push_back","push_back","max_value","pop_front","max_value"]
[[],[1],[2],[],[],[]]
输出: [null,null,null,2,1,2]
```
示例 2：
```
输入: 
["MaxQueue","pop_front","max_value"]
[[],[],[]]
输出: [null,-1,-1]
```

[题目链接](https://leetcode-cn.com/problems/dui-lie-de-zui-da-zhi-lcof/)

```
创建一个list作为先进先出队列
直接调用max函数返回list的最大值
入队列就在最后面append
出队列就返回list第一个的值，并修改list
```

```python
class MaxQueue:

    def __init__(self):
        self.L = []


    def max_value(self) -> int:
        if not self.L:
            return -1
        return max(self.L)


    def push_back(self, value: int) -> None:
        self.L.append(value)


    def pop_front(self) -> int:
        if not self.L:
            return -1
        t = self.L[0]
        self.L = self.L[1:]
        return t



# Your MaxQueue object will be instantiated and called as such:
# obj = MaxQueue()
# param_1 = obj.max_value()
# obj.push_back(value)
# param_3 = obj.pop_front()
```
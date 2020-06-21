剑指 Offer 30. 包含min函数的栈


定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。

示例:
```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.min();   --> 返回 -3.
minStack.pop();
minStack.top();      --> 返回 0.
minStack.min();   --> 返回 -2.
```

[题目链接](https://leetcode-cn.com/problems/bao-han-minhan-shu-de-zhan-lcof/)

```
1. 创建一个list作为栈 先入后出
2. push压栈就向list后面添加
3. top就返回list最后一个元素
4. 最小值就调用python的库min(list)返回列表的最小值
```

```python
class MinStack:

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.L = []

    def push(self, x: int) -> None:
        self.L.append(x)

    def pop(self) -> None:
        self.L = self.L[:-1]

    def top(self) -> int:
        return self.L[-1]

    def min(self) -> int:
        return min(self.L)


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(x)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.min()
```
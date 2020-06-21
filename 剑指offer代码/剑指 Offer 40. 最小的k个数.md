剑指 Offer 40. 最小的k个数


输入整数数组 arr ，找出其中最小的 k 个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4。

示例 1：
```
输入：arr = [3,2,1], k = 2
输出：[1,2] 或者 [2,1]
```
示例 2：
```
输入：arr = [0,1,2,1], k = 1
输出：[0]
```

[题目链接](https://leetcode-cn.com/problems/zui-xiao-de-kge-shu-lcof/)

```
先把list从小到大排序，将最小的数添加到结果中，然后从原数组中删除掉所有出现的这个数，继而继续添加最小的数
补：list删除元素
del a[0]  #指定删除第0位的元素
t = a.pop(0) #删除第0位元素,并将删除元素返回值赋值
a.remove('b') #删除指定元素，移除列表中某个值的第一个匹配项
```

```python
class Solution:
    def getLeastNumbers(self, arr: List[int], k: int) -> List[int]:
        arr.sort()
        L = []
        for _ in range(k):
            L.append(arr[0])
            arr.remove(arr[0])
        return L
```
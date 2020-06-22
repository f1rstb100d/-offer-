剑指 Offer 50. 第一个只出现一次的字符


在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。

示例:
```
s = "abaccdeff"
返回 "b"

s = "" 
返回 " "
```

[题目链接](https://leetcode-cn.com/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)

```
1. 新建个字典，第一次遍历字符串，把各个字母出现的次数加入字典
2. 再重新遍历字符串，遇到第一个出现次数为1的字符，输出
3. 否则最后输出个空格
```

```python
class Solution:
    def firstUniqChar(self, s: str) -> str:
        dic = {}
        for i in s:
            if(i not in dic):
                dic[i] = 1
            else:
                dic[i] += 1
        
        for i in s:
            if(dic[i] == 1):
                return i
        
        return " "
```
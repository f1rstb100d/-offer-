剑指 Offer 29. 顺时针打印矩阵


输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。

示例 1：
```
输入：matrix = [[1,2,3],[4,5,6],[7,8,9]]
输出：[1,2,3,6,9,8,7,4,5]
```
示例 2：
```
输入：matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
输出：[1,2,3,4,8,12,11,10,9,5,6,7]
```

[题目链接](https://leetcode-cn.com/problems/shun-shi-zhen-da-yin-ju-zhen-lcof/)

```
1. 按右下左上的顺序遍历二维数组，direction用来控制下一次搜索的方向，flag用于在四个方向循环一边之后重新把方向设置为右
2. 每经过一个点，把数组值改为/，当所有值都是/时输出最后的list
```

```python
class Solution:
    def move(self,i,j):
        if(j+1<self.j_max and self.m[i][j+1]!='/' and self.direction == 'right'):
            return (i,j+1,False)
        else:
            self.direction = 'down'
        if(i+1<self.i_max and self.m[i+1][j]!='/' and self.direction == 'down'):
            return (i+1,j,False)
        else:
            self.direction = 'left'
        if(j-1>=0 and self.m[i][j-1]!='/' and self.direction == 'left'):
            return (i,j-1,False)
        else:
            self.direction = 'up'
        if(i-1>=0 and self.m[i-1][j]!='/' and self.direction == 'up'):
            return (i-1,j,False)
        else:
            self.direction = 'right'
            return (i,j,True)
    
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        L = []
        if not matrix: #针对[]或[[]]
            return L
        self.i_max = len(matrix)
        self.j_max = len(matrix[0])
        self.m = matrix
        self.direction = 'right'
        i = 0
        j = 0
        num = self.i_max * self.j_max
        t = 0
        L.append(self.m[i][j])
        self.m[i][j] = '/'
        t += 1
        if(t == num): # 针对[[1]]
            return L
        while True:
            (i,j,flag) = self.move(i,j)
            if(flag == True):
                (i,j,flag) = self.move(i,j)
            L.append(self.m[i][j])
            self.m[i][j] = '/'
            t += 1
            if(t == num):
                break
                
        return L
```
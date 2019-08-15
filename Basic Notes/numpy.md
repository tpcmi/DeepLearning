# NumPy
>以下内容均来自[这里](https://www.numpy.org.cn/),稍作学习整理
## 基础篇
### 理解NumPy
NumPy是一个功能强大的Python库，主要用于对多维数组执行计算。
```
>>>import numpy as np 
>>>my_array = np.array([1, 2, 3, 4, 5]) 
>>>print my_array
```
- _**.shape**_ ：查询数组的形状
- 可以索引
- _**np.zeros**_ ：输出所有的元素都为0的数组
- _**np.ones**_
- 提取一行或者一列:
```
>>>b=np.array([[4,5],[6,1]])
[[4 5]
 [6 1]]
>>>b[:,1]
[5 1]
>>>b[1,:]
[6 1]
```





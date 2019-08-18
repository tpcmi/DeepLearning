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

- 可对数组进行加减乘除，是对应位置上的数据进行运算，若要执行矩阵乘法，点积：
```
>>>a = np.array([[1.0, 2.0], [3.0, 4.0]]) 
>>>b = np.array([[5.0, 6.0], [7.0, 8.0]])
>>>c=a.dot(b)
[[19. 22.]
 [43. 50.]]
```

  

### Numpy 简单入门教程

numpy允许在Python中进行向量和矩阵计算

```
a = np.array([[11, 12, 13, 14, 15],
              [16, 17, 18, 19, 20],
              [21, 22, 23, 24, 25],
              [26, 27, 28 ,29, 30],
              [31, 32, 33, 34, 35]])
```

进行**切片**的操作：

```
>>>print(a[0, 1:4]) 
[12 13 14]
>>>print(a[1:4, 0]) 
[16 21 26]
>>>print(a[::2,::2]) 
[[11 13 15]
 [21 23 25]
 [31 33 35]]
>>>print(a[:, 1]) 
[12 17 22 27 32]
```

![1565972018470](C:\Users\Codemao\AppData\Roaming\Typora\typora-user-images\1565972018470.png)

- 特殊运算符：
```
>>>a=np.arange(10)	#[0,1,2,3,4,5,6,7,8,9]
>>>print(a.sum())	#45
>>>print(a.max())	#9
>>>print(a.min())	#0
>>>pring(a.cumsum())	#[0,1,3,6,10,15,21,28,36,45]

  
```

- **where**函数：根据条件返回数组中的值

```
>>>a = np.arange(0, 100, 10)
>>>b = np.where(a < 50) 
>>>c = np.where(a >= 50)[0]
>>>print(b) # (array([0, 1, 2, 3, 4]),)
>>>print(c) # [5 6 7 8 9]  
```
### Numpy教程

#### 数组索引

```
>>>import numpy as np
>>>a = np.array([[1,2,3,4], [5,6,7,8], [9,10,11,12]])
>>>b = a[:2, 1:3]
#[[2 3]
# [6 7]]
---------------------------------------------------------
# A slice of an array is a view into the same data, so #modifying it will modify the original array.
>>>print(a[0, 1])   # Prints "2"
>>>b[0, 0] = 77     # b[0, 0] is the same piece of data as 
>>>print(a[0, 1])   # Prints "77"
---------------------------------------------------------
>>>a = np.array([[1,2], [3, 4], [5, 6]])
>>>print(a[[0, 1, 2], [0, 1, 0]])  # Prints "[1 4 5]"
---------------------------------------------------------
```

#### 广播（Broadcasting）

> 允许numpy在执行算术运算时使用不同形状的数组,使代码更加简洁，效率更高

假设向矩阵每一行都加上一个向量

```python
>>>import numpy as np

>>>x = np.array([[1,2,3], [4,5,6], [7,8,9], [10, 11, 12]])
>>>v = np.array([1, 0, 1])
>>>y = np.empty_like(x)   

>>>for i in range(4):
    y[i, :] = x[i, :] + v

# Now y is the following
# [[ 2  2  4]
#  [ 5  5  7]
#  [ 8  8 10]
#  [11 11 13]]
print(y)
```

当矩阵x非常大时，在Python中计算显式循环可能会很慢，这里可以将每一行加上的v向量扩展成一个相同size的矩阵：

```
>>>vv = np.tile(v, (4, 1))   
>>>print(vv)                 # Prints "[[1 0 1]
                          #          [1 0 1]
                          #          [1 0 1]
                          #          [1 0 1]]"
>>>y = x + vv  # Add x and vv elementwise
>>>print(y)  # Prints "[[ 2  2  4
          #          [ 5  5  7]
          #          [ 8  8 10]
          #          [11 11 13]]"
```

### 创建Numpy数组的不同方式

- 使用numpy内部功能函数

- 从Python列表转换

```
>>>list = [4,5,6]
>>>array = np.array(list)
```

- 使用特殊库函数

  - 创建一个填充0到1之间随机值的数组，使用random函数

    ```python
    >>>np.random.random((2,2))
    #array([[0.1632794 , 0.34567049],
    #      [0.03463241, 0.70687903]])
    ```

    

### Numpy中的矩阵和向量

#### 用numpy求解方程组：_**Ax=b**_
$$
A= \left[ \begin{matrix} 2&1&-2 \\ 3&0&1 \\ 1&1&-1 \end{matrix}\right]
$$



$$
b=\left[\begin{matrix}-3\\5\\-2\end{matrix}\right]
$$


```python
A = np.array([[2,1,-2],[3,0,1],[1,1,-1]])
b = np.transpose(np.array([[-3,5,-2]]))
```

求解：

```python
x = np.linalg.solve(A,b)
#[[-1.]
# [-1.]
# [2.]]
```







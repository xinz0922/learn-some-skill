# python三大库

## numpy（numeric Python）——Python的科学计算库

如果没有numpy库可以用pip进行安装

`pip install numpy`

### numpy的一些属性

|属性|功能|
|:-:|:-:|
|numpy.array|创建矩阵|
|shape|以元组数据展示矩阵的维度及各维度的元素个数|
|ndim|矩阵的维度|
|size|矩阵的元素总数|
|dtype|矩阵的元素格式|

### 创建矩阵

|属性|功能|
|:-:|:-:|
|np.zeros|创建元素全部为0的矩阵，参数可设置行、列的数目|
|np.ones|创建元素全部为0的矩阵，参数可设置行、列的数目|
|np.empty|生成无线接近0但非0的数，可以除以该数，得到的商是个非常非常大的数|
|np.arange|设置参数使得生成一维矩阵，和range函数一样的用法|
|.reshape|将元素分为几行几列的|
|np.non|设置空值|


**注:arange和reshape可以连用**

`a = numpy.arange(10).reshape(2,5)` #得到2行5列的元素为0-9的矩阵

### numpy的运算

举例说明
```
$ import numpy as np

$ arr1 = np.array([[1,2,3],[4,5,6]])

$ arr2 = np.array([[1,1,2],[2,2,3]])
```
- 相加：`$ arr1 + arr2`
- 相减：`$ arr1 - arr2`
- 相乘：`$ arr1 * arr2`
- 相除：`$ arr1 / arr2  # 这样是商只取整数部分，如果想得到浮点数类型的商，需要设置矩阵的类型，只设置一个都可以，例如arr2 = np.array([[1,1,2],[2,2,3]]，dtype = float)`
- 设置矩阵类型：`a= np.array([1,2,3],dtype=np.int32);a= np.array([1,2,3],dtype=float)`  # int32类型前必须要加np.,float前不用加np.
- 取整：`$ arr1 // arr2  #取整和int类型的数字相除的结果一样`
- 取余：`$ arr1 % arr2`
- 幂运算：`$ arr1 ** arr2`
- **矩阵乘法**：
   ```$ a = np.arange(10).reshape(2,5)
   $ a 
   array([[0, 1, 2, 3, 4],
       [5, 6, 7, 8, 9]])
   $ b = numpy.arange(15).reshape(5,3)
   $ b
   array([[ 0,  1,  2],
       [ 3,  4,  5],
       [ 6,  7,  8],
       [ 9, 10, 11],
       [12, 13, 14]])
   * $ **np.dot(a,b)**
   array([[ 90, 100, 110],
       [240, 275, 310]])
   * $ a.dot(b)   # 两种用法意义相同
   ```
- 转置矩阵
```np.transpose(arr1) == arr1.T  #  两者用法相同
> $ arr1
> array([[0, 1, 2, 3, 4],
       [5, 6, 7, 8, 9]])
> $ arr1.T
> array([[0, 5],
       [1, 6],
       [2, 7],
       [3, 8],
       [4, 9]])
       
```
### 随机数生成及矩阵的运算
- 生成随机数矩阵
```> import numpy as np
a = np.zeros((3,2))  # 生成3行2列的二维矩阵，元素全部为1
a = np.ones((2，3))  # 生成2行3列的二维矩阵，元素全部为0
a = np.random.random((2,3))   # 生成2行3列随机数矩阵，主需要一个参数，因此需要加括号
b = np.random.normal(size=(3,2)) # 生成3行2列符合正态分布的随机数矩阵
c = np.random.randint(0,10,size=(3,2)) # 生成3行2列大小在0-10之间的整数随机数矩阵，参数中至少要给出下线数字
```
- 矩阵计算
`np.sum(a)` # 计算矩阵a的所有元素的总和

`np.min(a)` # 输出矩阵a的所有元素中最小的值

`np.max(a)` # 输出矩阵a的所有元素中最大的值

`np.sum(a,axis=0)`   # 对列求和，返回列数个元素成为一个一维矩阵

`np.sum(a,axis=1)`   # 对行求和，返回行数个元素成为一个一维矩阵

`np.argmin(a)` # 返回a矩阵中最小的元素的索引（注意索引是从0开始计算的）

`np.argmax(a)` # 返回a矩阵中最大的元素的索引

`np.mean(a)`   # 返回a矩阵所有元素的均值

`np.median(a)`   # 返回a矩阵所有元素的中位数，如果元素为偶数个，则返回中间两个数的均值

`np.sqrt(a)`   # 返回a矩阵所有元素的开方值

`np.sort(a)`   # 对矩阵a的每一行进行排序

`np.clip(a,2,7)`  # 矩阵a中的元素，小于2的会都变成2，大于7的会都大于7


### numpy的索引
矩阵的索引是从0开始，例如矩阵a
```
array([[ 2,  3,  4,  5],
       [ 6,  7,  8,  9],
       [10, 11, 12, 13]])
```

> a[0]  # 取的是整个第一行
> a[0][0]  # 取得的是2
> a[2][3]   # 值为13

- 可以用for循环遍历矩阵
```
>>> for i in b:      # 按行取
>>>     print i
...
[2 3 4 5]
[6 7 8 9]
[10 11 12 13]
```
```
>>> for i in b.T:    # 按列取，需要将矩阵转置
>>>     print i
...
[ 2  6 10]
[ 3  7 11]
[ 4  8 12]
[ 5  9 13]
```
```
>>> for i in b.flat:    # 遍历矩阵的每个元素，按行取每个元素
>>>     print i
...
2
3
4
5
6
7
8
9
10
11
12
13
```


### 矩阵的合并

**必须同一维度的矩阵才能合并**

- 竖直合并   #矩阵直接垂直堆叠成为新的矩阵
```
>>> a
array([[ 5,  2,  6],
       [17, 13, 10]])
>>> b
array([[13, 14, 14],
       [12, 11, 11]])
>>> c
array([[82, 80, 62],
       [91, 68, 60]])
>>> np.vstack((a,b,c))
array([[ 5,  2,  6],
       [17, 13, 10],
       [13, 14, 14],
       [12, 11, 11],
       [82, 80, 62],
       [91, 68, 60]])
```
- 水平合并   #参与合并的每个矩阵的同一行连接成一行，原始矩阵是几行合并完成的新矩阵还是几行
```
>>> np.hstack((a,b,c))
array([[ 5,  2,  6, 13, 14, 14, 82, 80, 62],
       [17, 13, 10, 12, 11, 11, 91, 68, 60]])
```

- concatenate  #可以指定参数，合并某一维度，合并即为

举例说明
```
>>> a = np.random.randint(10,50,size=(2,3,4))
>>> a
array([[[32, 36, 46, 36],
        [12, 13, 24, 34],
        [46, 17, 17, 31]],

       [[27, 28, 30, 41],
        [23, 35, 26, 30],
        [25, 35, 41, 24]]])
        
>>> b = np.random.randint(0,20,size=(2,3,4))
>>> b
array([[[ 8, 15, 11, 17],
        [12,  2, 13, 15],
        [15, 18,  0,  9]],

       [[10,  2, 14,  6],
        [ 7, 18,  5, 10],
        [16, 18, 14, 17]]])        

>>> np.concatenate((a,b),axis=0)
array([[[32, 36, 46, 36],
        [12, 13, 24, 34],
        [46, 17, 17, 31]],

       [[27, 28, 30, 41],
        [23, 35, 26, 30],
        [25, 35, 41, 24]],

       [[ 8, 15, 11, 17],
        [12,  2, 13, 15],
        [15, 18,  0,  9]],

       [[10,  2, 14,  6],
        [ 7, 18,  5, 10],
        [16, 18, 14, 17]]])
        
>>> np.concatenate((a,b),axis=1)
array([[[32, 36, 46, 36],
        [12, 13, 24, 34],
        [46, 17, 17, 31],
        [ 8, 15, 11, 17],
        [12,  2, 13, 15],
        [15, 18,  0,  9]],

       [[27, 28, 30, 41],
        [23, 35, 26, 30],
        [25, 35, 41, 24],
        [10,  2, 14,  6],
        [ 7, 18,  5, 10],
        [16, 18, 14, 17]]])     
```
**矩阵形状**
```
>>> a.shape
(2, 3, 4)
>>> b.shape
(2, 3, 4)
>>> c= np.concatenate((a,b),axis=0)
>>> c.shape
(4, 3, 4)
>>> c= np.concatenate((a,b),axis=1)
>>> c.shape
(2, 6, 4)
>>> c= np.concatenate((a,b),axis=2)
>>> c.shape
(2, 3, 8)
```
- 转置
   1. 矩阵.T == np.transpose(矩阵)
   2. atleast_2d  #2d是指维度为2,2也可以换成其他更大的数字X，即为将矩阵转换为X维度矩阵
```
>>> a = np.array([1,2,3])
c = np.atleast_2d(a)
>>> c
array([[1, 2, 3]])
```

### 矩阵的分割

- np.split(被分割矩阵，分割后的矩阵数目，axis=数字)  # 等分分割，分割后的矩阵形状相同
- np.array_split(被分割矩阵，分割后的矩阵数目，axis=数字)  # 可以进行不等分分割,例如将4列分为3份，则第一份是2，后两份都是1；5列分为3份，则第1、2份是2，最后一份是1；

```
>>> a
array([[84,  4, 22, 79],
       [30, 23,  3, 61],
       [ 5, 77,  0, 40]])
       
>>> b,c,d =np.split(a,3,axis=0)
>>> b
array([[84,  4, 22, 79]])
>>> c
array([[30, 23,  3, 61]])
>>> d
array([[ 5, 77,  0, 40]])       
```
```
>>> x = np.random.randint(0,100,size=(3,5))
>>> x
array([[66,  4, 64, 48,  8],
       [39, 28, 51, 40, 94],
       [38, 58, 51, 85, 96]])
>>> b,c,d = np.array_split(x,3,axis=1)
>>>
>>> b
array([[66,  4],
       [39, 28],
       [38, 58]])
>>>
>>> c
array([[64, 48],
       [51, 40],
       [51, 85]])
>>>
>>> d
array([[ 8],
       [94],
       [96]])
```

### numpy的浅拷贝和深拷贝

- 浅拷贝 # 两个指针指向同一块存储，改一个另外一个会跟着改
```
>>> a = np.array([1,2,3])
>>> b=a
>>> b
array([1, 2, 3])
>>> b[0]=10
>>> b
array([10,  2,  3])
>>> a
array([10,  2,  3])

>>> c = a[::]
>>> c
array([10,  2,  3])
>>> c[0] = 50
>>> c
array([50,  2,  3])
>>> a
array([50,  2,  3])
```

- 深拷贝 # 两个不同的存储，是两个独立的数据，改一个的时候，另一个不会跟着改
```
>>> d = np.copy(a
>>> d
array([50,  2,  3])
>>> d[0]=100
>>> d
array([100,   2,   3])
>>> a
array([50,  2,  3])
```



## pandas

pandas可以说是numpy的扩展，numpy处理的数据一般是矩阵（列表），pandas处理的数据一般是字典

### 函数(pandas.函数名())
```
import pandas as pd
import numpy as np
```

|函数名|语法|功能|
|:-:|:-:|:-:|
|Series|pd.Series(list,index=)|设置n行1列的一维矩阵内容 ，可以指定列表的index，如果不指定则index为0-（n-1）的数字|
|\*date_range|dates = pd.date_range(start='',periods=6,freq='2d')|生成一个间隔为2天的包含6个元素的时间序列|
|\*DataFrame|df = pd.DataFrame(np.random.randint(100,size=(6,4)),index=dates,columns = ['A','B','C','D'])|生成一个6行4列的矩阵，index设置行名，columns设置列名，不设置行列名时，默认从0开始计数|
|index|df.index|查看df数据框的行名|
|columns|df.columns|查看df数据框的列名|
|values|df.values|查看df数据框的值|
|dtype|df.dtype|查看df数据框每一行的内容|
|sort_index|pd.sort_index(axis=0,ascending=False)|axis=0表明按行排序，为1表明按列排序；ascending为false，表明倒序，True为正序|
|sort_values|df.sort_values(by='E',ascending=False)|by表明按照E列排序|
|loc|data.loc[<row selection>, <column selection>]|可以根据data的行列标签对数据进行筛选|
|dropna|pd.dropna(axis=0/1,how='any'/'all')|除去DataFrame中的空值|
|fillna|pd.fillna(value=0)|将df中值为nan的values赋值为0|
|isnull|df.isnull|将df的values根据是否为nan来判断，输出True或者False，为nan的输出True|
|join|join='outer'/join='inner',具体看综合练习9|矩阵合并是否输出不一致的行或者列|
|join_axes|join_axes[df1.index],具体看综合练习9|按照哪一个矩阵的index进行合并，输出的矩阵和该矩阵一样|






### 综合练习（DataFrame：二维标记数据结构）
1. 筛选数据

   1. 创建数据框
```
>>> df1 = pd.DataFrame(np.random.randint(100,size=(6,4)),index = date,columns=['A','B','C','D'])
>>> df1
             A   B   C   D
2013-01-01  37   6  13  32
2013-01-02  47  32  47  79
2013-01-03  99  82  95  99
2013-01-04  40  72  32  84
2013-01-05  51   3  66  40
2013-01-06  93  52  50  49
```

   2. 根据数字索引输出：矩阵名[number:number]，默认按照行取数据，从0开始计数
```
>>> df2
                      x   v   n   m
2019-04-22 00:00:00  15  96   1  26
2019-04-22 02:00:00  97  81  68  36
2019-04-22 04:00:00   9  16  97   0
2019-04-22 06:00:00  41  49  37  13
2019-04-22 08:00:00   0  53  83  64
2019-04-22 10:00:00  55  84  28  83
>>>
>>> df2[0:1]
             x   v  n   m
2019-04-22  15  96  1  26
>>>
>>> df2[0:3]
                      x   v   n   m
2019-04-22 00:00:00  15  96   1  26
2019-04-22 02:00:00  97  81  68  36
2019-04-22 04:00:00   9  16  97   0
```

   3. 按照行列名筛选，单独的可以多行筛选，但是单独的只能输出单列
```
>>> df2['2019-04-22 00:00:00':'2019-04-22 02:00:00']
                      x   v   n   m
2019-04-22 00:00:00  15  96   1  26
2019-04-22 02:00:00  97  81  68  36
>>>
>>> df2['v']
2019-04-22 00:00:00    96
2019-04-22 02:00:00    81
2019-04-22 04:00:00    16
2019-04-22 06:00:00    49
2019-04-22 08:00:00    53
2019-04-22 10:00:00    84
Freq: 2H, Name: v, dtype: int64
>>>
>>> df2['x':'n']
Traceback (most recent call last):
```

   3. 按照标签筛选，loc函数（可以单独筛选行，但是不能只筛选列,列前必须加行的筛选范围，如果行全部输出，则为:,具体公式见上方表格）
```
>>> df2.loc['2019-04-22 00:00:00']
x    15
v    96
n     1
m    26
Name: 2019-04-22 00:00:00, dtype: int64
>>>
>>> df2['2019-04-22 00:00:00':'2019-04-22 02:00:00']
                      x   v   n   m
2019-04-22 00:00:00  15  96   1  26
2019-04-22 02:00:00  97  81  68  36
```

```
>>> df
             A   B   C   D
2019-04-22  78  69   1  98
2019-04-24  32  31  57  78
2019-04-26  65  20  32  84
2019-04-28   4  44  10  58
2019-04-30  97  43  57  91
2019-05-02   8  10  39  44
>>>
>>> df.loc['2019-04-22':'2019-04-24']
             A   B   C   D
2019-04-22  78  69   1  98
2019-04-24  32  31  57  78
>>>
>>> df.loc[:,'A':'B']
             A   B
2019-04-22  78  69
2019-04-24  32  31
2019-04-26  65  20
2019-04-28   4  44
2019-04-30  97  43
2019-05-02   8  10
>>>
>>> df.loc['2019-04-22':'2019-04-26','A':'C']
             A   B   C
2019-04-22  78  69   1
2019-04-24  32  31  57
2019-04-26  65  20  32
```
   4. iloc(按照默认的纯数字index进行筛选)
```
>>> df.iloc[0] # 只给一个数字是先对行筛选，并且结果为Series的列表形式，不是dataframe形式
A    78
B    69
C     1
D    98
Name: 2019-04-22 00:00:00, dtype: int64
>>>
>>> df.iloc[:,0]  # 只选单列
2019-04-22    78
2019-04-24    32
2019-04-26    65
2019-04-28     4
2019-04-30    97
2019-05-02     8
Freq: 2D, Name: A, dtype: int64
>>>
>>> df.iloc[0:3,0:4] 对dataframe进行切片
             A   B   C   D
2019-04-22  78  69   1  98
2019-04-24  32  31  57  78
2019-04-26  65  20  32  84

>>> df.iloc[[0,2],0:4]  逐个不连续的筛选
             A   B   C   D
2019-04-22  78  69   1  98
2019-04-26  65  20  32  84
>>>
>>> df.iloc[[0,2],[1,3]]
             B   D
2019-04-22  69  98
2019-04-26  20  84
```

   5. 结合数字和标签筛选，ix
```
>>> df.ix[0:1,'A':'C']
             A   B  C
2019-04-22  78  69  1
```

   6. 判断筛选
```
>>> df.A>50 # 对单列进行筛选
2019-04-22     True
2019-04-24    False
2019-04-26     True
2019-04-28    False
2019-04-30     True
2019-05-02    False
Freq: 2D, Name: A, dtype: bool

>>> df[df.A>50]   对A列进行判断筛选，并且输出符合的整行
             A   B   C   D
2019-04-22  78  69   1  98
2019-04-26  65  20  32  84
2019-04-30  97  43  57  91

>>> df.ix[0]>50   # 对单行进行判断筛选
A     True
B     True
C    False
D     True
Name: 2019-04-22 00:00:00, dtype: bool
```

   7. 设置数值
```
>>>df = pd.DataFrame(np.random.randint(100,size=(6,4)),index=pd.date_range(start='20190422',periods=6,freq='3d'),columns=['A','B','C','D'])
>>> df
             A   B   C   D
2019-04-22  52  87  39  38
2019-04-24  32  19  41  32
2019-04-26  21  90  64  14
2019-04-28  21   1  89  61
2019-04-30  48  87  43  98
2019-05-02  77  93  55  41

>>> df.iloc[0,0]
52
>>> df.iloc[0,0] = 100  # iloc-用数值index进行value的修改
>>>
>>> df
              A   B   C   D
2019-04-22  100  87  39  38
2019-04-24   32  19  41  32
2019-04-26   21  90  64  14
2019-04-28   21   1  89  61
2019-04-30   48  87  43  98
2019-05-02   77  93  55  41

>>> df.loc['2019-04-22','A']  # loc-用行列名进行value的修改
100
>>>
>>> df.loc['2019-04-22','A'] = 200
>>> df
              A   B   C   D
2019-04-22  200  87  39  38
2019-04-24   32  19  41  32
2019-04-26   21  90  64  14
2019-04-28   21   1  89  61
2019-04-30   48  87  43  98
2019-05-02   77  93  55  41

>>> df.ix[0,'A']
200
>>> df.ix[0,'A'] = 300  # ix-混合使用index（数字和标签）进行value的修改
>>> df
              A   B   C   D
2019-04-22  300  87  39  38
2019-04-24   32  19  41  32
2019-04-26   21  90  64  14
2019-04-28   21   1  89  61
2019-04-30   48  87  43  98
2019-05-02   77  93  55  41
>>>
>>> df[df.A>100]  # 将A列中values >100的整行输出
              A   B   C   D
2019-04-22  300  87  39  38
>>> df[df.A>100] = 300  # 将A列中values >100的那一行的每个value都重新赋值为300
>>> df
              A    B    C    D
2019-04-22  300  300  300  300
2019-04-24   32   19   41   32
2019-04-26   21   90   64   14
2019-04-28   21    1   89   61
2019-04-30   48   87   43   98
2019-05-02   77   93   55   41
>>>
>>> df.B[df.B>90] = 90  # 将B列中values >90的那一行的B列的值重新赋值为90
>>> df
              A   B    C    D
2019-04-22  300  90  300  300
2019-04-24   32  19   41   32
2019-04-26   21  90   64   14
2019-04-28   21   1   89   61
2019-04-30   48  87   43   98
2019-05-02   77  90   55   41
>>>
>>> df
              A   B    C    D
2019-04-22  300  90  300  300
2019-04-24   32  19   41   32
2019-04-26   21  90   64   14
2019-04-28   21   1   89   61
2019-04-30   48  87   43   98
2019-05-02   77  90   55   41
>>> df.C[df.A>100] = 50    # 将A列中的values大于100的那一行的C列的值重新赋值为50
>>> df
              A   B   C    D
2019-04-22  300  90  50  300
2019-04-24   32  19  41   32
2019-04-26   21  90  64   14
2019-04-28   21   1  89   61
2019-04-30   48  87  43   98
2019-05-02   77  90  55   41

>>>
>>> df['F'] = np.arange(6)    # 加一列F列，并赋值
>>> df
              A   B   C    D  F
2019-04-22  300  90  50  300  0
2019-04-24   32  19  41   32  1
2019-04-26   21  90  64   14  2
2019-04-28   21   1  89   61  3
2019-04-30   48  87  43   98  4
2019-05-02   77  90  55   41  5
```
   
   8. 处理丢失数据
```
>>> df.iloc[1,2] = np.nan     # 利用numpy的nan函数重新赋值df的values，得到空值
>>> df
              A     B     C      D    F
2019-04-22  300   NaN  50.0  300.0  0.0
2019-04-24   32  19.0   NaN   32.0  1.0
2019-04-26   21  90.0  64.0    NaN  2.0
2019-04-28   21   1.0  89.0   61.0  NaN
2019-04-30   48  87.0  43.0   98.0  4.0
2019-05-02   77  90.0  55.0   41.0  5.0
>>>
>>> df
                A     B     C      D    F
2019-04-22  300.0   NaN  50.0  300.0  0.0
2019-04-24    NaN   NaN   NaN    NaN  NaN
2019-04-26   21.0  90.0  64.0    NaN  2.0
2019-04-28   21.0   1.0  89.0   61.0  NaN
2019-04-30   48.0  87.0  43.0   98.0  4.0
2019-05-02   77.0  90.0  55.0   41.0  5.0
>>>
# axis设置是对行进行处理，how={'any','all'},how为any表示这一行中只要有一个nan就去除整行，how为all表示整行为nan时取出这一行
>>> df.dropna(axis=0,how='all')     
                A     B     C      D    F
2019-04-22  300.0   NaN  50.0  300.0  0.0
2019-04-26   21.0  90.0  64.0    NaN  2.0
2019-04-28   21.0   1.0  89.0   61.0  NaN
2019-04-30   48.0  87.0  43.0   98.0  4.0
2019-05-02   77.0  90.0  55.0   41.0  5.0
>>>
>>> df1
             A   B   C     D
2019-04-22  67   3  89  93.0
2019-04-25  52  15  95  86.0
2019-04-28   7  35   5   NaN
2019-05-01  58  66  38   2.0
2019-05-04  50  56  90  37.0
2019-05-07  56  89  44  24.0
>>>
>>> df1.dropna(axis=0,how='any')
             A   B   C     D
2019-04-22  67   3  89  93.0
2019-04-25  52  15  95  86.0
2019-05-01  58  66  38   2.0
2019-05-04  50  56  90  37.0
2019-05-07  56  89  44  24.0
>>>
>>> df1.dropna(axis=1,how='any')
             A   B   C
2019-04-22  67   3  89
2019-04-25  52  15  95
2019-04-28   7  35   5
2019-05-01  58  66  38
2019-05-04  50  56  90
2019-05-07  56  89  44
>>>
>>> df1
             A   B   C     D
2019-04-22  67   3  89  93.0
2019-04-25  52  15  95  86.0
2019-04-28   7  35   5   NaN
2019-05-01  58  66  38   2.0
2019-05-04  50  56  90  37.0
2019-05-07  56  89  44  24.0
>>> df1.fillna(value=0)    # 把nan的值重新赋值为0
             A   B   C     D
2019-04-22  67   3  89  93.0
2019-04-25  52  15  95  86.0
2019-04-28   7  35   5   0.0
2019-05-01  58  66  38   2.0
2019-05-04  50  56  90  37.0
2019-05-07  56  89  44  24.0

>>> df
             A   B     C   D
2019-04-22  82  71  70.0  78
2019-04-25  73  92   NaN   0
2019-04-28   5  99  84.0  16
2019-05-01  62   9  77.0   6
2019-05-04  14  89  48.0  44
2019-05-07   4  29  76.0  56
>>> df.isnull()      # 判断df的哪个value是空值
                A      B      C      D
2019-04-22  False  False  False  False
2019-04-25  False  False   True  False
2019-04-28  False  False  False  False
2019-05-01  False  False  False  False
2019-05-04  False  False  False  False
2019-05-07  False  False  False  False
>>>
>>> np.any(df.isnull() == True)  # 判断df中是否有为nan的值，如果有返回True，如果没有返回False
True
>>>

```

   9. 矩阵的合并
```
>>> df1 = pd.DataFrame(np.zeros((3,4)),columns=['a','b','c','d'])    # np.zeros((3,4))，生成3行4列values全部为0的二维矩阵
>>> df1
     a    b    c    d
0  0.0  0.0  0.0  0.0
1  0.0  0.0  0.0  0.0
2  0.0  0.0  0.0  0.0
>>> df2 = pd.DataFrame(np.ones((3,4)),columns=['a','b','c','d'])     # np.ones((3,4))，生成3行4列values全部为1的二维矩阵
>>> df2
     a    b    c    d
0  1.0  1.0  1.0  1.0
1  1.0  1.0  1.0  1.0
2  1.0  1.0  1.0  1.0
>>> df3 = pd.DataFrame(np.ones((3,4))*2,columns=['a','b','c','d'])      # np.ones((3,4))*2，生成3行4列values全部为2的二维矩阵
>>> df3
     a    b    c    d
0  2.0  2.0  2.0  2.0
1  2.0  2.0  2.0  2.0
2  2.0  2.0  2.0  2.0
>>> res = pd.concat([df1,df2,df3],axis=0)    # axie=0,表明j将行顺次合并在一起，输入的第一个参数是列表类型，列表内容需要合并的矩阵名
>>> res
     a    b    c    d
0  0.0  0.0  0.0  0.0
1  0.0  0.0  0.0  0.0
2  0.0  0.0  0.0  0.0
0  1.0  1.0  1.0  1.0
1  1.0  1.0  1.0  1.0
2  1.0  1.0  1.0  1.0
0  2.0  2.0  2.0  2.0
1  2.0  2.0  2.0  2.0
2  2.0  2.0  2.0  2.0
>>>
>>> res = pd.concat([df1,df2,df3],axis=0,ignore_index=True)    # ignore_index=True表明忽略原本的index，重新建立index
>>> res
     a    b    c    d
0  0.0  0.0  0.0  0.0
1  0.0  0.0  0.0  0.0
2  0.0  0.0  0.0  0.0
3  1.0  1.0  1.0  1.0
4  1.0  1.0  1.0  1.0
5  1.0  1.0  1.0  1.0
6  2.0  2.0  2.0  2.0
7  2.0  2.0  2.0  2.0
8  2.0  2.0  2.0  2.0

# 合并行列名不完全一致的矩阵
>>> df1 = pd.DataFrame(np.zeros((3,4)),columns=['a','b','c','d'],index=[0,1,2])
>>> df1
     a    b    c    d
0  0.0  0.0  0.0  0.0
1  0.0  0.0  0.0  0.0
2  0.0  0.0  0.0  0.0
>>> df2 = pd.DataFrame(np.ones((3,4)),columns=['a','c','d','e'],index=[2,3,4])
>>> df2
     a    c    d    e
2  1.0  1.0  1.0  1.0
3  1.0  1.0  1.0  1.0
4  1.0  1.0  1.0  1.0
>>> pd.concat([df1,df2],axis=1)     # 最终列数增加
     a    b    c    d    a    c    d    e
0  0.0  0.0  0.0  0.0  NaN  NaN  NaN  NaN
1  0.0  0.0  0.0  0.0  NaN  NaN  NaN  NaN
2  0.0  0.0  0.0  0.0  1.0  1.0  1.0  1.0
3  NaN  NaN  NaN  NaN  1.0  1.0  1.0  1.0
4  NaN  NaN  NaN  NaN  1.0  1.0  1.0  1.0
>>> pd.concat([df1,df2],axis=0)     # 行堆叠在一起，最终的行数增加
     a    b    c    d    e
0  0.0  0.0  0.0  0.0  NaN
1  0.0  0.0  0.0  0.0  NaN
2  0.0  0.0  0.0  0.0  NaN
2  1.0  NaN  1.0  1.0  1.0
3  1.0  NaN  1.0  1.0  1.0
4  1.0  NaN  1.0  1.0  1.0
>>> pd.concat([df1,df2],axis=0,join='outer')    # join的默认为'outer'，相同列合并，没有的values用nan填充
     a    b    c    d    e
0  0.0  0.0  0.0  0.0  NaN
1  0.0  0.0  0.0  0.0  NaN
2  0.0  0.0  0.0  0.0  NaN
2  1.0  NaN  1.0  1.0  1.0
3  1.0  NaN  1.0  1.0  1.0
4  1.0  NaN  1.0  1.0  1.0
>>> pd.concat([df1,df2],axis=0,join='inner')    # 当join为'inner'时，只合并出列（或者行）相同的
     a    c    d
0  0.0  0.0  0.0
1  0.0  0.0  0.0
2  0.0  0.0  0.0
2  1.0  1.0  1.0
3  1.0  1.0  1.0
4  1.0  1.0  1.0
>>> pd.concat([df1,df2],axis=0,join='outer',ignore_index=True)    # 忽略原始的index，重新建立index，防止index的重复
     a    b    c    d    e
0  0.0  0.0  0.0  0.0  NaN
1  0.0  0.0  0.0  0.0  NaN
2  0.0  0.0  0.0  0.0  NaN
3  1.0  NaN  1.0  1.0  1.0
4  1.0  NaN  1.0  1.0  1.0
5  1.0  NaN  1.0  1.0  1.0
>>> pd.concat([df1,df2],axis=1,join_axes=[df1.index])    # 按照df1的index进行合并，最后输出的矩阵index和df1的相同
     a    b    c    d    a    c    d    e
0  0.0  0.0  0.0  0.0  NaN  NaN  NaN  NaN
1  0.0  0.0  0.0  0.0  NaN  NaN  NaN  NaN
2  0.0  0.0  0.0  0.0  1.0  1.0  1.0  1.0

>>> df1
     a    b    c    d
0  0.0  0.0  0.0  0.0
1  0.0  0.0  0.0  0.0
2  0.0  0.0  0.0  0.0
>>> s1 = pd.Series([1,2,3,4],index=['a','b','c','d'])
>>> s1
a    1
b    2
c    3
d    4
dtype: int64
>>> df1.append(s1,ignore_index=True)      # 必须加ignore_index这个参数，不然会报错，因为s1没有列名，转换后就没有行名了
     a    b    c    d
0  0.0  0.0  0.0  0.0
1  0.0  0.0  0.0  0.0
2  0.0  0.0  0.0  0.0
3  1.0  2.0  3.0  4.0
```

   10. 矩阵的merge
```
>>> left = pd.DataFrame({'key':['K0','K1','K2','K3'],'A':['A0','A1','A2','A3'],'B':['B0','B1','B2','B3']})
>>> left
    A   B key
0  A0  B0  K0
1  A1  B1  K1
2  A2  B2  K2
3  A3  B3  K3
>>> right = pd.DataFrame({'key':['K0','K1','K2','K3'],'C':['C0','C1','C2','C3'],'D':['D0','D1','D2','D3']})
>>> right
    C   D key
0  C0  D0  K0
1  C1  D1  K1
2  C2  D2  K2
3  C3  D3  K3
>>> pd.merge(left,right,on='key')     # on表示对哪一列进行合并
    A   B key   C   D
0  A0  B0  K0  C0  D0
1  A1  B1  K1  C1  D1
2  A2  B2  K2  C2  D2
3  A3  B3  K3  C3  D3

>>> t1
    A   B key1 key2
0  A0  B0   K0   K0
1  A1  B1   K1   K1
2  A2  B2   K1   K0
3  A3  B3   K2   K1
>>> t2
    C   D key1 key2
0  C0  D0   K0   K0
1  C1  D1   K1   K0
2  C2  D2   K1   K0
3  C3  D3   K2   K0
>>> pd.merge(t1,t2,on=['key1','key2'])
    A   B key1 key2   C   D
0  A0  B0   K0   K0  C0  D0
1  A2  B2   K1   K0  C1  D1
2  A2  B2   K1   K0  C2  D2

# how可以有四种参数['inner','outer','left','right'],其中inner为默认参数，表示只输出有相同值的那些行，outer指输出所有的行，right（left）指基于右边（左边）的矩阵的key进行填充
>>> pd.merge(t1,t2,on=['key1','key2'],how='outer')    
     A    B key1 key2    C    D
0   A0   B0   K0   K0   C0   D0
1   A1   B1   K1   K1  NaN  NaN
2   A2   B2   K1   K0   C1   D1
3   A2   B2   K1   K0   C2   D2
4   A3   B3   K2   K1  NaN  NaN
5  NaN  NaN   K2   K0   C3   D3

>>> df1 =pd.DataFrame({'col1':[0,1],'col_left':['a','b']})
>>> df2 = pd.DataFrame({'col1':[1,2,2],'col_right':[2,2,2]})
>>> df1
   col1 col_left
0     0        a
1     1        b
>>> df2
   col1  col_right
0     1          2
1     2          2
2     2          2
>>> pd.merge(df1,df2,on='col1',how='outer',indicator = True)      # indicator默认为False，为True时表示显示出矩阵每一行merge的情况
   col1 col_left  col_right      _merge
0     0        a        NaN   left_only
1     1        b        2.0        both
2     2      NaN        2.0  right_only
3     2      NaN        2.0  right_only
>>> pd.merge(df1,df2,on='col1',how='outer',indicator = 'indicators')    # indicator的那一列改名字
   col1 col_left  col_right  indicators
0     0        a        NaN   left_only
1     1        b        2.0        both
2     2      NaN        2.0  right_only
3     2      NaN        2.0  right_only


>>> boys = pd.DataFrame({'k':['K0','K1','K2'],'age':[3,4,5]})
>>> girls = pd.DataFrame({'k':['K4','K1','K7'],'age':[10,20,15]})
>>> girls
   age   k
0   10  K4
1   20  K1
2   15  K7
>>> boys
   age   k
0    3  K0
1    4  K1
2    5  K2
>>> pd.merge(boys,girls,on='k',suffixes=['_boy','_girl'],how='outer',indicator=True)      # suffixes为后缀名，改columns一样的列名
   age_boy   k  age_girl      _merge
0      3.0  K0       NaN   left_only
1      4.0  K1      20.0        both
2      5.0  K2       NaN   left_only
3      NaN  K4      10.0  right_only
4      NaN  K7      15.0  right_only

```

## 开启新课程

1. 创建文件

   ```
   $ import pandas as pd
   $ import numpy as np
   $ df =pd.DataFrame()
   $ df.to_excel("/p200/husn_group/zhengxin/practice.xslx")    # 在这一步会生成文件到该路径下，但不知道为什么我没做成功
   $ df = pd.DataFrame({'ID':[1,2,3],'name':['Tim','Victor','Nick']})
   $ df
   In [26]: df
   Out[26]:
      ID    name
   0   1     Tim
   1   2  Victor
   2   3    Nick
   
   $ df.set_index('ID')    # 建立索引，也可以说是行名
   Out[28]:
         name
   ID
   1      Tim
   2   Victor
   3     Nick
   
   
   
   
   
   
   
   
   
   






**附录**

1. date_range

设置包含一系列时间数据的列表，有多个参数
   
   * pandas.date_range(start=None, end=None, periods=None, freq='D', tz=None, normalize=False, name=None, closed=None, **kwargs)
   * periods：固定时期，取值为整数或None
   * freq：日期偏移量，取值为string或DateOffset，默认为'D',也可以为s（秒），h（小时）
   * normalize：若参数为True表示将start、end参数值正则化到午夜时间戳
   * name：生成时间索引对象的名称，取值为string或None
2. DataFrame

生成一个矩阵，使用很灵活

`df2 = pd.DataFrame({'A':1.,'B':pd.Timestamp('20190422'),'C':pd.Series(1,index=list(range(4))),'D':np.array([3]*4),'E':pd.Categorical(['test','train','test','train']),'F':'foo'})`

* 上述代码用来生成一个4行6列的矩阵，

# 参考

[B站课程——AI_MOOC](https://www.bilibili.com/video/av38355831/?p=6)

[博客——pandas中时间序列——date_range函数](https://blog.csdn.net/kancy110/article/details/77131539)

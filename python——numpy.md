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

|zeros|创建元素全部为0的矩阵，参数可设置行、列的数目|
|:-:|:-:|
|ones|创建元素全部为0的矩阵，参数可设置行、列的数目|
|empty|生成无线接近0但非0的数，可以除以该数，得到的商是个非常非常大的数|
|arange|设置参数使得生成一维矩阵，和range函数一样的用法|
|reshape|将元素分为几行几列的|

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
- 取整：`$ arr1 // arr2  #取整和int类型的数字相除的结果一样`
- 取余：`$ arr1 % arr2`
- 幂运算：arr1 ** arr2

















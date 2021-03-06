# 目录
[前期铺垫](#前期铺垫)
   1. [python出现](#python出现)
   2. [编程语法分为编译型语言和解释型语言](#编程语法分为编译型语言和解释型语言)
   3. [Python设计目标](#Python设计目标)
   4. [Python特点](#Python特点)
   5. [编写Python程序](#编写Python程序)
   6. [python2 vs python3](#python2vspython3)
   7. [ipython——交互式解释器](#ipython——交互式解释器)
   8. [集成开发环境](#集成开发环境)
[程序开始编写了](#程序开始编写了)

# 前期铺垫df

1. python出现
   * Gudio van Rossum1989年为了打发无聊的圣诞，编写了Python解释器，它是用C语言实现的，并能够调用C语言的库文件。
   * 1991年公布了Python解释器的源代码，做到完全开源，以便任何人都可以为它做贡献。

2. 编程语法分为编译型语言和解释型语言：
   * 编译型语言使用步骤为先在开发环境下编写程序代码，写完后全部交给编译器编译成计算机能识别的包含0、1代码的最终可执行文件，
   如果在windows操作系统下双击可执行文件交由CPU执行该程序，特点是运行速度快，直接执行。
   * 解释型语言使用步骤为编写源代码，逐行提交到解释器，解释完由操作系统提交给CPU进行执行，特点是逐行翻译执行，运行时间较长
   * 计算机不能理解除了计算机以外的其他语言，因此Python这类编程语言想要被计算机执行，需要一个翻译官，Python的翻译官就是不同操作系统下的解释器
3. Python设计目标

   * 一门简单直观的语言并与主要竞争者一样强大
   * 开源，以便任何人都可以为它做贡献　　　
   * 代码像纯英语那样容易理解
   * 适用于短期开发的日常任务
4. Python特点
   * 完全面向对象，在Python中一切皆对象，例如函数、模块、数字、字符串都是对象
      * 解决问题首先需要考虑让谁去解决，这里的谁就是对象
      * 解决复杂的问题可以找多个人，也就是设计多个对象，大家各司其职，合理解决问题，提高效率
   * 强大的标准库，里面有很多对象，可以帮我们完成我们想做的事
   * 大量的第三方模块，指非官方开发提供的，但是功能和标准库差不多的应用包
   * Python的每一行执行一个任务，不建议多条语句写一行，因为会报错
   * 缩进严格，即格式严格，不要有多余空格，因为Python的设计哲学是优雅、简单、明确，优雅就是指所有人完成同一个工作用的代码可以是完全一样的，大家的代码都是整整齐齐，不会因为缩进的不严格导致看起来代码不优雅
5. 编写Python程序
   * 解释器：Python2.X Python3.X
   * 交互式：ipython
   * 集成开发环境:pycharm   可以图形界面可视化
6. python2vspython3
   * Python2.X不支持中文，Python3.X支持中文，可以调用解释器python3 script.py  ，用python3解释script.py的程序
   * Python3.X和Python2.X差异不大，主要在于底层设计的优化
   * 在Python3.0推出之后，又推出了2.6及2.7的兼容版本，这两个兼容版本可以完全涵盖python2.X，同时又部分兼容3.0，所以当有些第三方库不支持python3.0时，仍然推荐使用3.0开发，但是可以在python2.7（Python的最后一款2.X）来解释
7. ipython——交互式解释器
   * 支持自动补全
   * 支持自动缩进
   * 支持shell命令
   * 有很多函数和包
8. 集成开发环境
   * （integrated development environment，IDE），推荐PyCharm，好用
   
# 程序开始编写了
1. 注释
   * 单行注释
   
   由'#'开头，后接一个空格（保证格式整齐），然后可以写注释内容（中英文都可以）
   
   如果代码很短，注释也很短，两者可以放到一行，但是需要将注释放在代码后至少空2个空格后接# ，再写注释
   
   Python解释器看到"#"后会认为后面内容为说明性的语言，直接跳过而不执行
   `# 这是注释`
   - 多行注释
   
2. 程序运行最重要的三大硬件 
   1. CPU：超大规模的集成开发电路、中央处理器，用来干活的，处理\计算数据   
   2. 内存
      - 临时存储数据，断点时数据会消失
      - 读取速度快
      - 空间小
      
   3. 硬盘
      - 永久存储数据，断电时数据会消失
      - 读取速度慢
      - 空间大  
   4. 程序的运行
   1. 代码编写完成后是存储在硬盘上的，需要执行的时候会先复制到内存里，然后由CPU执行。像Python这种解释型语言，在执行的时候，会先将Python解释器加载到内存上，解释器提供翻译代码的规则，指导CPU翻译成自身能够识别的机器语言（0/1语言），再进行执行工作，活全都是CPU干的。
   2. 程序运行时是加载到内存中的，内存给程序划分了程序自己独享的空间，一些数据可以存储在这个空间里，这个空间也叫做变量，是用来存储数据的
   
3. 变量
- 数字型
   1. 整型
   2. 浮点型
   3. 复数型
   4. 布尔值（0为false，非0为true）

- 非数字型
   1. 字符串
   2. 列表
   3. 字典
   4. 元组
   
- 类型变量计算
   1. 数字型：
   - bool值作为数字计算，当bool值存储的是false时作为0参与计算，存储的是true时作为1计算
   2. 非数字型和数字型之间只可以进行\*运算
   
   
4. 格式化
- 格式化字符串指在需要输出的字符串在变量的位置用%s（%d、%f）等格式化符号先占上位置，然后才能被用来格式化
- "格式化字符串" % (变量1，变量2，变量3)
   1. %06d     \# 6表示6位整数，0表示不到6位的用0补齐 
   
   ```
   In [2]: print("我的学号是%06d" % student)
   我的学号是000001
   ```
   2. %.2f     \# 2表示小数点后保留两位
  
   ```
   In [22]: student= 0.08
   In [23]: print("我的学号是%.2f" % student)
   我的学号是0.08
   ```
   - 如果换成%.1f的话，会四舍五入
   
   ```
   In [27]: student= 0.05
   In [28]: print("我的学号是%.2f" % student)
   我的学号是0.05
   In [29]: print("我的学号是%.1f" % student)
   我的学号是0.1
   ```
   3. %% 表示输出% 
   
   ```
   In [32]: print("我的学号是%.1f%%" % (student*100))
   我的学号是5.0%
   ```
 
 
5. 标识符：变量或者函数的名字
- 可以由字母、数字、下划线组成
- 数字不能作为开头
- 不能和关键字重名

6. 关键字：Python内部已经是用的标识符，具有特殊的含义和功能

```
In [35]: import keyword    # 倒入keyword模块
In [36]: print(keyword.kwlist)      # 查看关键字有哪些
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

7. 逻辑运算
- 逻辑运算符可以把多个条件按照逻辑进行连接，编程更复杂的条件
- and or not——————并且 或者 非
   - and：两个条件都成立才成立
   - or：两个条件有一个成立即为成立
   - not：取反
   
8. 循环语句——while
- 格式：
   ```
   初始条件
   while 判断及循环
   改变条件判断的值
   ```
- 死循环：由于程序猿没有改变条件判断的值，导致while判断的条件始终满足，循环无终止执行
- 关键字：
   - break：不执行循环体后续代码，跳出整个循环体，直接到达下一步程序
   - continue：不执行循环体后续代码，直接跳回到while条件判断，因此**在continue前一定要做和在下一步程序中一样要做的条件判断值的更改**
   
``` 
      i = 0
      s = 0
      while i < 101:
         if i %2 == 0:
            s += i
         else:
            i += 1      # continue之前必须要做的，否则会陷入死循环
            continue
         i += 1
      print(s,i)
```

9. print 函数
- 默认输出时在末尾自动增加换行，可以通过加一个语句：end=""使得输出后不会自动换行，例如：print("输出内容"，end="")
   - 将end = "--"，表示将原本的换行符替换成"--",符合也可以换成别的，例如下图
   - ![](http://prl9niawf.bkt.clouddn.com/FsllJZU5u9KYQplfZdkFy0pb60vg)
   - ![](http://prl9niawf.bkt.clouddn.com/FrsExy8Bu7Uw127eiqkd3iGoumQe)


   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   





# 参考
[B站课程](https://www.bilibili.com/video/av14184325?p=2)
[heqiuyong博客](http://www.cnblogs.com/heqiuyong/p/8469357.html)

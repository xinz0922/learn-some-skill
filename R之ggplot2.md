# R画图——ggplot2
---
## 基础知识
---
* ggplot是图层式绘图工具，图层之间的叠加是靠“+”号实现的
* 有明确的起始和终止，起始是ggplot()
* 绘图元素包括两个层次，第一层次是整张图——plot，第二层次是轴——axis，legend——图例，facet——面。其中facet又分为外部script（包括background和text）和内部panel部分（包括background、border、网格线grid，粗的网格线是grid.major，细的网格线是grid.minor）
* ggplot的函数
   * 计算：fortity_，mean_等
   * 初始化，展示绘图：ggplot、plot、print等
   * 真正绘图:stat_，geom_，annotate
   * 微调图型:aes,aes参数控制了对哪些变量进行图形映射，以及映射方式，图形属性，横纵坐标，点的大小、颜色，填充色等
   * **ggplot的公式：
   ggplot(data = , aes(x = , y = ，z = )) +geom_XXX(...) + ... + stat_XXX(...) + ... +annotate(...) + ... + labs(...) +scale_XXX(...) + coord_XXX(...) + guides(...) + theme(...) +facet_XXX(...)
   1. geom :表示几何对象，它是ggplot中重要的图层控制对象，因为它负责图形渲染的类型。
   2. stat :统计变换 比如求均值，求方差等，当我们需要展示出某个变量的某种统计特征的时候，需要用到统计变换
   3. annotate：添加注释 
   4. labs : labs(x = "这是 X 轴", y = "这是 Y 轴", title = "这是标题") ## 修改文字
   5. coord_：调整坐标，控制了图形的坐标轴并影响所有图形元素. 调整坐标 coord_flip()来翻转坐标轴。使用xlim()和ylim()来设置连续型坐标轴的最小值和最大值 coord_cartesian(xlim=c(0,100),ylim=c(0,100))
   6. theme：调整不与数据有关的图的元素的函数。theme函数采用了四个简单地函数来调整所有的主题特征：element_text调整字体，element_line调整主题内的所有线，element_rect调整所有的块，element_blank清空。theme(panel.grid =element_blank()) ## 删去网格线
   7. facet :控制分组绘图的方法和排列形式
   
## 画图
   一个图形对象就是一个包含数据，映射，图层，标度，坐标和分面的列表，外加组件options
   
   ggplot(数据, 映射) geom_xxx(映射, 数据) stat_xxx(映射, 数据)

   通过“+”实现不同图层的相应累加，且越往后的图层表现在上方
   * 点（point, text）：往往只有x、y指定位置，有shape但没有fill
   * 线(line,vline,abline,hline,stat_function等)：一般是基于函数来处理位置
   * 射(segment)：特征是指定位置有xend和yend，表示射线方向
   * 面(tile, rect)：这类一般有xmax,xmin,ymax,ymin指定位置
   * 棒(boxplot,bin,bar,histogram)：往往是二维或一维变量，具有width属性
   * 带(ribbon,smooth):透明是特征是透明的fill

|函数|功能|
|:-:|:-:|
|数据（data）|将要展示的数据|
|映射（mapping）|数据中的变量到图形成分的映射|
|几何对象（geom）|用来展示数据的几何对象，如geom_point,geom_bar,geom_abline|
|图形属性（aes）|图形属性决定了图形的外观，如字体大小、标签位置及刻度线|
|标度（scale）|决定了变量如何被映射到图形属性上|
|坐标（coordinate）|数据如何被映射到图中。如coord_polar:极坐标|
|统计变换（stat）|对数据进行汇总，如箱线图stat_boxplot、线图stat_abline、直方图stat_bin|
|分面（facet）|用来描述数据如何被拆分为子集，以及对不同子集是如何绘制的|
|位置调整（position）|对图形位置做精细控制|



   
   
   
   
   
   
   
   
   
   
   
   
   
   
   ## 引用
   [来源于博客https://www.cnblogs.com/nxld/p/6059603.html](https://www.cnblogs.com/nxld/p/6059603.html)

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
   
   ~~* **ggplot的公式：~~
   
   ggplot(data = , aes(x = , y = ，z = )) +geom_XXX(...) + ... + stat_XXX(...) + ... +annotate(...) + ... + labs(...) +scale_XXX(...) + coord_XXX(...) + guides(...) + theme(...) +facet_XXX(...)
   1. geom :表示几何对象，它是ggplot中重要的图层控制对象，因为它负责图形渲染的类型。
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   ## 引用
   [来源于博客https://www.cnblogs.com/nxld/p/6059603.html](https://www.cnblogs.com/nxld/p/6059603.html)

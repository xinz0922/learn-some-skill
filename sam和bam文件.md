# sam和bam文件格式

SAM(Sequence Alignment/Map)格式是一种通用的比对格式，用来存储reads到参考序列的比对信息。

SAM是一种序列比对格式标准，由sanger制定，是以TAB为分割符的文本格式。主要应用于测序序列mapping到基因组上的结果表示，当然也可以表示任意的多重比对结果。

SAM分为两部分，注释信息（header section）和比对结果部分（alignment section）。

## head——头部分

>@HD，说明符合标准的版本、对比序列的排列顺序；
>@SQ，参考序列说明；

>@RG，比对上的序列（read）说明；

>@PG，使用的程序说明；

>@CO，任意的说明信息。

- 参考

[简书来源:https://www.jianshu.com/p/9c99e09630da](https://www.jianshu.com/p/9c99e09630da)

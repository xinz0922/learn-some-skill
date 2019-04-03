# sam和bam文件格式

SAM(Sequence Alignment/Map)格式是一种通用的比对格式，用来存储reads到参考序列的比对信息。

SAM是一种序列比对格式标准，由sanger制定，是以TAB为分割符的文本格式。主要应用于测序序列mapping到基因组上的结果表示，当然也可以表示任意的多重比对结果。

SAM分为两部分，注释信息（header section）和比对结果部分（alignment section）。

**注意**
头部分可有可无；

在比对部分，每一行是一条fragement的比对结果；

template指参考序列和比对上的序列共同组成的序列

## head section——头部分

>* @HD，说明符合标准的版本、对比序列的排列顺序；
>* @SQ，参考序列说明;
>* @RG，比对上的序列（read）说明；
>* @PG，使用的程序说明；
>* @CO，任意的说明信息。

## alignment section——比对部分

>1. QNAME    比对片段的（template）的编号；read name，read的名字通常包括测序平台等信息
\# eg.ILLUMINA-379DBF:1:1:3445:946#0/1    
>2. FLAG    位标识，template mapping情况的数字表示，每一个数字代表一种比对情况，这里的值是符合情况的数字相加总和
\# flag取值见下方备注表格
>3. RNAME   参考序列的编号，如果注释中对SQ-SN进行了定义，这里必须和其保持一致，另外对于没有mapping上的序列，这里是'\*';
>4. 
# eg.chr1

每一行是一个read的比对结果信息，包括11个必须字段和1个可选字段

- 参考

[主要来源为简书:https://www.jianshu.com/p/9c99e09630da](https://www.jianshu.com/p/9c99e09630da)

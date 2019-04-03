# sam和bam文件格式

SAM(Sequence Alignment/Map)格式是一种通用的比对格式，用来存储reads到参考序列的比对信息。

SAM是一种序列比对格式标准，由sanger制定，是以TAB为分割符的文本格式。主要应用于测序序列mapping到基因组上的结果表示，当然也可以表示任意的多重比对结果。

SAM分为两部分，注释信息（header section）和比对结果部分（alignment section）。

**注意**

头部分可有可无；

在比对部分，每一行是一条fragement的比对结果,包括11个必须字段和1个可选字段

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
|flag value|Description|
:-:|:-:
|0x1|template has multiple segments|
>4. POS   比对上的位置，注意是从1开始计数，没有比对上，此处为0;
>5. 5. MAPQ     mapping的质量,，比对的质量分数，越高说明该read比对到参考基因组上的位置越唯一;
\# eg.42
>6. CIGAR   简要比对信息表达式（Compact Idiosyncratic Gapped Alignment Report），其以参考序列为基础，使用数字加字母表示比对结果，match/mismatch、insertion、deletion 对应字母 M、I、D。比如3S6M1P1I4M，前三个碱基被剪切去除了，然后6个比对上了，然后打开了一个缺口，有一个碱基插入，最后是4个比对上了，是按照顺序的；
\# eg.36M   表示36个碱基在比对时完全匹配

\# **注：第七列到第九列是mate(备注1)的信息，若是单末端测序这几列均无意义**

>7. RNEXT    配对片段（即mate）比对上的参考序列的编号，没有另外的片段，这里是'*'，同一个片段，用'='；
\# eg.*
>8. PNEXT    配对片段（即mate）比对到参考序列上的第一个碱基位置，若无mate,则为0；
\# eg.0
>9. TLEN    Template（文库插入序列）的长度，最左边得为正，最右边的为负，中间的不用定义正负，不分区段（single-segment)的比对上，或者不可用时，此处为0(ISIZE，Inferred fragment size.详见Illumina中paired end sequencing 和 mate pair sequencing，是负数，推测应该是两条read之间的间隔(待查证)，若无mate则为0);
\# eg.0
>10. SEQ    序列片段的序列信息，如果不存储此类信息，此处为'\*'，注意CIGAR中M/I/S/=/X对应数字的和要等于序列长度；
\# eg.CGTTTCTGTGGGTGATGGGCCTGAGGGGCGTTCTCN
>11. QUAL    序列的质量信息,read质量的ASCII编码,格式同FASTQ一样。
\# eg.PY\[\[YY\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_QQQQbILKIGEFGKB
>12. 第十二列之后：Optional fields，以tab建分割。
\# eg.AS:i:-1 XN:i:0 XM:i:1 XO:i:0 XG:i:0 NM:i:1 MD:Z:35T0 YT:Z:UU




- 参考

[主要来源为简书:https://www.jianshu.com/p/9c99e09630da](https://www.jianshu.com/p/9c99e09630da)

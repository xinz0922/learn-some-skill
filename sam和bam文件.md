# sam和bam文件格式

SAM(Sequence Alignment/Map)格式是一种通用的比对格式，用来存储reads到参考序列的比对信息。

SAM是一种序列比对格式标准，由sanger制定，是以TAB为分割符的文本格式。主要应用于测序序列mapping到基因组上的结果表示，当然也可以表示任意的多重比对结果。

SAM分为两部分，注释信息（header section）和比对结果部分（alignment section）。

**注意**

头部分可有可无；

在比对部分，每一行是一条fragement的比对结果,包括11个必须字段和1个可选字段

**名词解释**

- template：DNA/RNA序列的一部分，用它进行测序或者由原始数据拼接得到它，作为研究的模版；
- read：测序仪下机得到的原始数据，这些数据依照测序时间的先后被打上不同标签；双端测序存在read1，read2
- segment：比对到read的时候的一段连续序列或者被分开几条子序列。一条read可以包含多条segment；
- linear alignment:一条read比对到参考序列上，可以存在插入(insert)、缺失(delete)、跳跃(skip)、剪切(clip)，但是方向不变（不能是一部分和正链匹配，另一部分又和负链匹配），sam文件中只占用一行记录；
- chimeric alignment:“嵌合比对” 的形成是由于一条测序read比对到基因组上时分别比对到两个不同的区域，而这两个区域基本没有overlap。因此它在sam文件中需要占用多行记录显示。只有第一个记录被称作"representative",其他的都是"supplementary"


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

### flag description

\#    **下表flag数值用16进制表示，所以在识别flag前先简单回顾进制**

几进制就是逢几进一

- 2进制，用两个阿拉伯数字：0、1；
- 8进制，用八个阿拉伯数字：0、1、2、3、4、5、6、7；
- 10进制，用十个阿拉伯数字：0到9；
- **16进制，用十个阿拉伯数字和6个英文字母：**
   - 16进制就是逢16进1，但是数字只有0-9这十个，所以用A，B，C，D，E，F这六个字母来分别表示10，11，12，13，14，15，字母不区分大小写。
   - 十六进制数为0x开头，0是数字0，不是字母o，以下为16进制转换十进制的举例说明：
      - 0x1 = 1（10)   \# 1 * 16^（1-0） = 1
      - 0x12 = 18(10)   \# 1 * 16^(2-1) + 2*16^(1-0) = 18
      - 0x12A = 12(10)  \# 1 * 16^(3-1) + 2*16^(2-1) + 10*16^(1-1) = 298
      - 从以上例子中可以看出，除去0x剩下的部分为16进制数值，个位数字*16的0次方，十位数值*16的一次方，百位数值*16的二次方，以此类推。从右向左数，16进制数值的第n位数值乘以16的(n-1)次方，分别算出每一位的10进制数值，然后全部相加最终得到转化后的十进制数值。

|flag value|Description|
|:-:|:-:|
|0x1|该read是成对的paired reads中的一个|
|0x2|paired reads中每个都正确比对到参考序列上|
|0x4|该read没比对到参考序列上|
|0x8|与该read成对的matepair read没有比对到参考序列上|
|0x10|该read其反向互补序列能够比对到参考序列|
|0x20|与该read成对的matepair read其反向互补序列能够比对到参考序列|
|0x40|0x与该read成对的matepair read其反向互补序列能够比对到参考序列|
|0x80|在paired reads中，该read是与参考序列比对的第二条|
|0x100|该read是次优的比对结果|
|0x200|该read没有通过质量控制|
|0x400|由于PCR或测序错误产生的重复reads|
|0x800|补充匹配的read|

## BAM文件

bam文件是sam文件的二进制格式文件，两者格式相同，bam比sam文件占空间更小，因此运算更快。但是有的软件只能用bam或者sam文件作为输入文件，因此可以用samtools软件实现两者的转化。

查看bam文件：`samtools view *.bam | less -S`

文件转换：
-sam转bam `samtools view -bS sample1.sam > sample1.bam` 
-bam转sam `samtools view -h sample1.bam > sample1.sam`

-参考

[主要来源为简书:https://www.jianshu.com/p/9c99e09630da](https://www.jianshu.com/p/9c99e09630da)
[来源于简书：链接：https://www.jianshu.com/p/53167d7b811e](https://www.jianshu.com/p/53167d7b811e)
[来源于简书：https://www.jianshu.com/p/240bffd7cf00](https://www.jianshu.com/p/240bffd7cf00)

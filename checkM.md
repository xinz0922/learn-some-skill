# checkM软件

官网：https://ecogenomics.github.io/CheckM/

## checkM原理

* 推测参考基因组树
   
   通过将细菌和古细菌基因之间的交集确定为> 90％的基因组中的单拷贝，建立了初始的66个通用标记基因。并且从该初始基因组中，移除了在参考基因组的> 1％中具有不同系统发育历史的18个多拷贝基因。后面又移除了和IMG不一致的5个gene
     
   进行分类学一致性的测试。 最终的43个系统发育信息标记基因（补充表S6）主要由核糖体蛋白和RNA聚合酶结构域组成，并且类似于PhyloSift使用的通用标记组（Supplemental Table S7; Darling等，2014）。 参考基因组树是在WAG + GAMMA模型下从6988列与FastTree v2.1.3的级联比对推断的，并且在细菌和古细菌之间生根。 使用tax2tree为内部节点分配了分类标签（McDonald等人，2012）。
   
* 在推定的基因组中鉴定标记基因

   使用Prodigal v2.60（Hyatt等人2012）和Pfam（Finn等人2014）预测基因，并使用HMMER v3.1b1（http：// hmmer。）鉴定TIGRFAMs（Haft等人2003）蛋白质家族。 janelia.org）具有Pfam（-cut_gc）和TIGRFAM（-cut_nc）HMM的模型特定截止值。 Pfam注释使用与Sanger Institute和IMG相同的方法进行分配，该方法考虑了Pfam氏族之间的同源关系（参见Sanger Institute FTP站点上的pfam_scan.pl，https：//www.sanger.ac.uk/）。 由于重叠群中的模糊碱基偶尔会发生基因调用错误，这可能导致相邻的错误基因被分配到相同的标记基因。 通过检查相邻标记基因是否与标记基因HMM的相邻非重叠部分具有最佳匹配来解决这些错误。
   











# 引用
[checkM官网](https://ecogenomics.github.io/CheckM/)

[checkM article](https://genome.cshlp.org/content/25/7/1043.full#F3)

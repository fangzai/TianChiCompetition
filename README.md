# TianChiCompete
Our responding code and resources for TianChi competition



#Update 2015/04/10
 - 基本框架的构建：<br/> 
    **特征工程部分**<br/> 
     Generate_raw_train.py (从原始数据中按照分割点，得到分割点前的数据)<br />
     Generate_feature_All.py (从raw_train数据中提取特征，并构建基于特征向量的训练集合)<br />
    **算法框架部分**<br/>
     Algorithm_LRTest.py (利用LR回归，进行分类预测)<br />
     Function_CalF1.py (F1函数的计算)<br />
 - 负样本影响问题<br/> 
    测试产生 '候选集'的过程中，发现虽然只用子集，但是一早上起来，数据量还是把硬盘给爆了，经测试，代码应该没有产生大问题。估计是负样本太多，过多的想预测没有发生过预测行为的（U,I）对。尝试取消这部分内容

#Update 2015/04/09
  - 提取整个特征模块的代码架构，想相似代码融合到一个有效函数内，用Generate_feature_All.py 来生成ref/test/vectorResult。同时预先生成中间特征csv文件，方便后期自动化流程的顺利开展

#Update 2015/04/08
 - 添加特征<br/> 
     商品：<br />
	 销量（前3/7/15天） √ <br />
	 分类中商品排名     - <br />
     用户：<br/> 
	 购买总量           √ <br />
	 活跃天数           √ <br />
	 相关转化率         - <br />
     geohash：<br />
	 了解前缀匹配方式  √  <br />
 - 代码自动化程度<br/> 
     通过实际动手，发现现在的两部分代码自动化拟合程度还不是很高。当前是为了方便，没有追加写特征的csv文件<br />
     后期跟进数据需要，可能需要先写出中间的特征文件，然后对于每天新增数据再进行追加写。<br />
 
#Update 2015/04/06
1. 基本框架的构建<br/> 
    特征工程部分<br/> 
        Generate_raw_train.py (从原始数据中按照分割点，得到分割点前的数据)<br />
        Generate_feature_All.py (从raw_train数据中提取特征，并构建基于特征向量的训练集合)<br />
    算法框架部分<br/> 
        LRTest.py (利用LR回归，进行分类预测)<br />
        CalF1.py (F1函数的计算)<br />
    调用模块的文件<br/> 
        根据网上的建议，当前主要选用pandas & statemodel，暂不清楚是否方便修改相关算法的API。先试着跑通流程pandas/statmodels 为相关库(依赖库较多，暂未上传) docs-py2.7(python官方文档pdf)
2. 所需要处理的工作
 - 特征提取上<br/> 
   商品相关特征： 销量（前3/7/15天）<br />
   分类中商品的排名（可能需要折合成数值型）<br />
   用户相关特征： 购买总量/总的购买天数<br />
   用户-分类特征：用户对该分类进行访问/购买/加购物车的次数<br />
 - 数据分布的问题<br/> 
   当然，在进一步利用单模型对特征进行多重训练之前，先要解决好数据的一些问题，保证不会使"知识"在测试集上无法有效应用<br />

#Update 2015/04/05
初步准备利用LR,把 *特征工程的构建* 和 *算法模型的选取* 分开来，也方便将整体流程顺一下。
然后有机会在进一步深入学习和探究

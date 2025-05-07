# 个人github项目

##备注：
好的书籍三个特点，和书法审美很像：结构、笔法、章法
●结构：目录具有结构性，逻辑关系
●排他：每个目录内容和其他有互斥关系，不能重复
●聚焦：正个结构聚焦在一个方向上

两个项目
BPM Defined ERP设计指南1.0版本
AI Defined ERP 设计指南1.0版本

各大交易所对上市公司ERP采购、销售、应收、应付单有啥明确且具体的要求？

内容规范
每个主数据对象和业务单据对象都给一个最小可行性（看齐SaaS）和pro版本（看齐sap）示例


BD_ERP
https://docs.qq.com/sheet/DRWt0Z0FnSXN4WXJ6?no_promotion=1&tab=BB08J2

目录结构
一、纵向：
主数据：整个行业解决方案，面向政府、学校、企业机构
流程
规则
报表
表单
对象


二、横向：
销售，CRM
库存，WMS
生产，PP
质量
项目
MES
采购，SRM
财务，FICO
EHR


一、开源背景
解决两类需求
●自研ERP，取代SAP/Oracle融合云
●自研ERP

两种方案
●基于BPM驱动设计
●基于AI驱动设计

二、设计规范


## 一、基本知识

1. 本书中所有的向量都是列向量的形式：
    
    ![一、基本知识 - 图1](https://static.sitestack.cn/projects/huaxiaozhuan-ai/239aaefa581740e66c088fe9d407fff4.svg)
    
    本书中所有的矩阵 ![一、基本知识 - 图2](https://static.sitestack.cn/projects/huaxiaozhuan-ai/85d0de7405b0093400a5046e64579b3a.svg) 都表示为：
    
    ![一、基本知识 - 图3](https://static.sitestack.cn/projects/huaxiaozhuan-ai/3656d7851918e6722c30500769f9fb14.svg)
    
    简写为：![一、基本知识 - 图4](https://static.sitestack.cn/projects/huaxiaozhuan-ai/70ffbcb4455d9cb8dbb0903ed9f4d232.svg) 或者 ![一、基本知识 - 图5](https://static.sitestack.cn/projects/huaxiaozhuan-ai/bbc4222e3182e63bec325f108a5e08b7.svg) 。
    
2. 矩阵的`F`范数：设矩阵 ![一、基本知识 - 图6](https://static.sitestack.cn/projects/huaxiaozhuan-ai/4c819e57bcb79bd9872d4c58aee2fa06.svg)，则其`F` 范数为：![一、基本知识 - 图7](https://static.sitestack.cn/projects/huaxiaozhuan-ai/26504d626733de561f7f7b5669665b59.svg) 。
    
    它是向量的 ![一、基本知识 - 图8](https://static.sitestack.cn/projects/huaxiaozhuan-ai/63304f0ad202562f9162391f8d2092a9.svg) 范数的推广。
    
3. 矩阵的迹：设矩阵 ![一、基本知识 - 图9](https://static.sitestack.cn/projects/huaxiaozhuan-ai/4c819e57bcb79bd9872d4c58aee2fa06.svg)，则![一、基本知识 - 图10](https://static.sitestack.cn/projects/huaxiaozhuan-ai/7c8823b6d64cb217d9d2bef587a76262.svg)的迹为： ![一、基本知识 - 图11](https://static.sitestack.cn/projects/huaxiaozhuan-ai/311b7d05485736e43897812eddf3c7f5.svg)。
    
    迹的性质有：
    
    - ![一、基本知识 - 图12](https://static.sitestack.cn/projects/huaxiaozhuan-ai/1b1039ab2b6412f97f6771f5f4efef88.svg) 的`F` 范数等于![一、基本知识 - 图13](https://static.sitestack.cn/projects/huaxiaozhuan-ai/70a0fe40f6aa3cab4fa8a56b8b03346a.svg) 的迹的平方根：![一、基本知识 - 图14](https://static.sitestack.cn/projects/huaxiaozhuan-ai/4130deebdbc7238f90f6923552befa63.svg) 。
    - ![一、基本知识 - 图15](https://static.sitestack.cn/projects/huaxiaozhuan-ai/1b1039ab2b6412f97f6771f5f4efef88.svg) 的迹等于![一、基本知识 - 图16](https://static.sitestack.cn/projects/huaxiaozhuan-ai/c20e3a1b073be9b5ed4c530f2be5ad15.svg) 的迹：![一、基本知识 - 图17](https://static.sitestack.cn/projects/huaxiaozhuan-ai/dd6e85f139a5037241ae5a5fe7b6660c.svg) 。
    - 交换律：假设 ![一、基本知识 - 图18](https://static.sitestack.cn/projects/huaxiaozhuan-ai/1a363a8db5137e67c6a1a2cb00bab2ac.svg)，则有：![一、基本知识 - 图19](https://static.sitestack.cn/projects/huaxiaozhuan-ai/097bcb56b62f97a0b7f9c652654d3ce4.svg) 。
    - 结合律：![一、基本知识 - 图20](https://static.sitestack.cn/projects/huaxiaozhuan-ai/af2f15c390ed59f8e9c72c5a22b08f39.svg) 。

## 二、向量操作

1. 一组向量 ![二、向量操作 - 图1](https://static.sitestack.cn/projects/huaxiaozhuan-ai/38cedf88a8ce1550c321c940754d6eaf.svg) 是线性相关的：指存在一组不全为零的实数 ![二、向量操作 - 图2](https://static.sitestack.cn/projects/huaxiaozhuan-ai/c4e2e6d9fa327d8e0c1231b0f8108d9a.svg)，使得： ![二、向量操作 - 图3](https://static.sitestack.cn/projects/huaxiaozhuan-ai/f93fce5714a7a56048285d0e7f652613.svg) 。
    
    一组向量 ![二、向量操作 - 图4](https://static.sitestack.cn/projects/huaxiaozhuan-ai/38cedf88a8ce1550c321c940754d6eaf.svg) 是线性无关的，当且仅当 ![二、向量操作 - 图5](https://static.sitestack.cn/projects/huaxiaozhuan-ai/969eca3559080831f6ce892ac333854f.svg) 时，才有：![二、向量操作 - 图6](https://static.sitestack.cn/projects/huaxiaozhuan-ai/f93fce5714a7a56048285d0e7f652613.svg) 。
    
2. 一个向量空间所包含的最大线性无关向量的数目，称作该向量空间的维数。
    
3. 三维向量的点积：![二、向量操作 - 图7](https://static.sitestack.cn/projects/huaxiaozhuan-ai/8fda2e098f817ca34604bc7385d185d4.svg) 。




### 三大范式

第一范式：保证列的原子性，保证列不可再分。

第二范式：唯一性 ；一个表只说明一个事物;有主键且非主键依赖主键；（限制多对多的关系，建立一个关联表，通过外键和联合主键来关联两张表）

第三范式：每列都与主键有直接关系，不存在传递依赖;（限制一对多的关系，在从表中建立一个外键，通过外键来引用主表的信息）


### MySQL引擎及区别

![img](https://mmbiz.qpic.cn/mmbiz_png/A66lAAJ1DX3KfyIDll94PMiajRtRD2WpKPTTvySUHAeG9dS4GlWOC3CvTXegKLA85R8sJombbn98mLhHN5UbVibQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### 索引索引为什么要用B+树不用二叉树

MySQL索引是按页存储的，相同数据量二叉树的高度比B+树高，高度越高，磁盘IO次数越多，效率也就越低。所以用B+树是为了减少磁盘IO次数。

### like查询什么情况可以用到索引，什么情况用不到

like ‘aaa%’ 可以用到索引

like '%aaa' 不能用到索引

### MySQL索引优化

最左匹配原则、不在列上做函数运算、不在列上加表达式运算

具体可以看这篇：

https://monkeysayhi.github.io/2018/03/06/%E6%B5%85%E8%B0%88MySQL%E7%9A%84B%E6%A0%91%E7%B4%A2%E5%BC%95%E4%B8%8E%E7%B4%A2%E5%BC%95%E4%BC%98%E5%8C%96/

### MySQL回表

https://www.jianshu.com/p/8991cbca3854

### 索引下推

https://blog.csdn.net/mccand1234/article/details/95799942



### 覆盖索引

https://www.cnblogs.com/happyflyingpig/p/7662881.html
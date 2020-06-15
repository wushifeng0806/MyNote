### Redis是单线程还是多线程

Redis在执行命令的过程中是单线程的

Redis 6.0引进了多线程IO，不过执行命令依旧还是单线程的。

### Redis事务

https://www.cnblogs.com/DeepInThought/p/10720132.html

**Redis事务的概念：**

　	Redis 事务的本质是一组命令的集合。事务支持一次执行多个命令，一个事务中所有命令都会被序列化。在事务执行过程，会按照顺序串行化执行队列中的命令，其他客户端提交的命令请求不会插入到事务执行命令序列中。

　　总结说：redis事务就是一次性、顺序性、排他性的执行一个队列中的一系列命令。　　

**Redis事务没有隔离级别的概念：**

　　批量操作在发送 EXEC 命令前被放入队列缓存，并不会被实际执行，也就不存在事务内的查询要看到事务里的更新，事务外查询不能看到。

**Redis不保证原子性：**

　　Redis中，单条命令是原子性执行的，但事务不保证原子性，且没有回滚。事务中任意命令执行失败，其余的命令仍会被执行。



### Redis高性能原因

可以看这篇：

https://www.cnblogs.com/xlecho/archive/2019/11/10/11832118.html

### 缓存穿透/击穿

https://baijiahao.baidu.com/s?id=1655304940308056733

### 布隆过滤器

https://www.cnblogs.com/heihaozi/p/12174478.html

### Redis分布式锁

https://www.cnblogs.com/wukongbubai/p/12393370.html



### Redis协议是文本还是二进制？

文本协议

### Redis持久化

RDB、AOF

https://baijiahao.baidu.com/s?id=1654694618189745916




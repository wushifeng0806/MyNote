### 乐观锁和悲观锁

- b			悲观锁：悲观锁在操作数据时比较悲观，认为别人会同时修改数据。因此操作数据时直接把数据锁住，直到操作完成后才会释放锁；上锁期间其他人不能修改数据。

### ThreadLocal原理

https://www.jianshu.com/p/98b68c97df9b

### synchronized锁升级

**偏向锁**

在 JDK1.8 中，其实默认是轻量级锁，但如果设定了 -XX:BiasedLockingStartupDelay = 0 ，那在对一个 Object 做 syncronized 的时候，会立即上一把偏向锁。当处于偏向锁状态时， markword 会记录**当前线程 ID** 。

**升级到轻量级锁**

当下一个线程参与到偏向锁竞争时，会先判断 markword 中保存的线程 ID 是否与这个线程 ID 相等，如果不相等，会立即撤销偏向锁，升级为轻量级锁。每个线程在自己的线程栈中生成一个 **LockRecord** ( LR )，然后每个线程通过 CAS (自旋)的操作将锁对象头中的 markwork 设置为指向自己的 LR 的指针，哪个线程设置成功，就意味着获得锁。关于 synchronized 中此时执行的 CAS 操作是通过 native 的调用 HotSpot 中 bytecodeInterpreter.cpp 文件 C++ 代码实现的，有兴趣的可以继续深挖。

**升级到重量级锁**

如果锁竞争加剧(如线程自旋次数或者自旋的线程数超过某阈值， JDK1.6 之后，由 JVM 自己控制该规则)，就会升级为重量级锁。此时就会向操作系统申请资源，线程挂起，进入到操作系统内核态的等待队列中，等待操作系统调度，然后映射回用户态。在重量级锁中，由于需要**做内核态到用户态**的转换，而这个过程中需要消耗较多时间，也就是"重"的原因之一。



### CAS的问题

ABA问题，可以用版本号来避免这个问题。

具体可以看这篇：

https://blog.csdn.net/summerZBH123/article/details/80642467



### LongAdder原理

LongAdder类与AtomicLong类的区别在于高并发时前者将对单一变量的CAS操作分散为对数组cells中多个元素的CAS操作，取值时进行求和；而在并发较低时仅对base变量进行CAS操作，与AtomicLong类原理相同。

具体可以看这篇：

https://www.jianshu.com/p/ec045c38ef0c



### 线程池

创建多少个线程

- CPU 密集型程序	

  一个完整请求，I/O操作可以在很短时间内完成， CPU还有很多运算要处理，也就是说 CPU 计算的比例占很大一部分

  **理论上：`线程数量 = CPU 核数（逻辑）`**

  **实际上 配置：`线程数量CPU 核数（逻辑）+ 1`**

- I/O 密集型程序    

  与 CPU 密集型程序相对，一个完整请求，CPU运算操作完成之后还有很多 I/O 操作要做，也就是说 I/O 操作占比很大部分

  **最佳线程数 =  `(1/CPU利用率)` = `1 + (I/O耗时/CPU耗时)`**

### 原子引用

#### LongAdder

https://mp.weixin.qq.com/s/le-BfM6-mDftU2nGI1DmuA


### 各字段解释

1. id （表的读取顺序）: select查询的序列号，包含一组数字，表示查询中执行select子句或操作表的顺序

三种情况

- id相同，执行顺序由上至下
- id不同，如果是子查询，id的序号会递增，id值越大优先级越高，越先被执行。
- id相同又不同。 id相同，可以认为是一组，从上往下顺序执行；在所有组中，id值越大，优先级越高，越先执行（衍生=DERIVED）

  2.select_type（数据读取操作的操作类型）:  主要用于区别简单查询、联合查询、子查询等的复杂查询。

1. SIMPLE:简单的select查询，查询中不包含子查询或者UNION

2. PRIMARY：查询中若包含任何负责的子部分，最外层查询则被标记为

3. SUBQUERY：在select或者where列表中的子查询

4. DERIVED：在from列表中包含的子查询被标记为derived（衍生）,MYSQL会递归执行这些子查询，把结果放在临时表里。

5. UNION：若第二个select出现在UNION之后，则被标记为UNION；

   ​				若UNION包含在from子句的子查询中，外层SELECT将被标记为DERIVED

6. UNION RESULT:从UNION表中获取结果的select




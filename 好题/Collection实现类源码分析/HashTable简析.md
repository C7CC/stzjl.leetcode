## HashTable简析

1，HashHable中的**key，value均不能为null**

2，方法实现了synchronized实现了线程同步

3，存放时直接使用hashCode值（不重新计算）

4，继承自Dictionary
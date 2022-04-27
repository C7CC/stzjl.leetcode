## HashMap

1，HashMap底层维护了数组 + 链表 + 红黑树 （JDK8及以后）

2，（key - value）为一个HashMap$Node结点 多个HashMap$Node结点构成Map$Entry单向链表，HashMap中table数组也存储数据（不用维护双向链表来保持顺序）

<img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20220419082033669.png" alt="image-20220419082033669" style="zoom: 67%;" />

3，红黑树，树化条件

一，某个链表长度>=8

二，table数组长度>=64

这二者同时成立时该链表会进行树化，其它未达成条件链表不会树化

细节：

一，若链表长度达到了8而table长度未达到64此时再向该链表添加元素就会扩容每次扩容2倍，

每次扩容后不会立即检查是否要树化，下次添加时才会进行检查（若达到树化条件则不会再进行扩容）

二，一般时扩容根据加载因子0.75，即数组长度*加载因子时进行扩容（到达时即扩容），扩容考虑为总元素数而不是仅在table数组上的元素数

三，HashMap在存放时重新计算了hash值

```Java
static final int hash(Object key) {
    int h;
    return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);//此处将hash值重新计算不是直接用HashCode()方法所得的值来存放
}
```




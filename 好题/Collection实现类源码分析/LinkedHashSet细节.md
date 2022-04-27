## LinkedHashSet

1，LinkedHashSet是HashSet的子类

2，LinkedHashSet底层是数组+双向链表

LinkedHashSet不在数组中存数据（仅用数组在元素hash后确定存放位置，不同于HashMap）而将数组存放到双向链表中

3，LinkedHashSet用双向链表来维持元素顺序看似以顺序插入保存（实际保存地址是根据hash值也就是无序的）

<img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20220419072911490.png" alt="image-20220419072911490" style="zoom: 50%;" />
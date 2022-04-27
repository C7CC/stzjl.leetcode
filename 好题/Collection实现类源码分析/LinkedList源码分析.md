## LinkedList源码分析

### 1,无参构造器创建链表

```java
public LinkedList() {
}//无语句
```

### first = null , last = null

### 2，进行添加操作

```java
public boolean add(E e) {
    linkLast(e);
    return true;
}
```



```java
void linkLast(E e) {
    final Node<E> l = last;//l为最后面的结点
    final Node<E> newNode = new Node<>(l, e, null);//创建新的结点并且此结点放在最后
    last = newNode;//将last(类似于指针)指向最后的结点
    if (l == null)//没有结点既初次添加
        first = newNode;
    else
        l.next = newNode;
    size++;
    modCount++;
}
```

### 

### 总结

1，LinkedList底层维护了一个双向链表

2，链表基本原理

first指向最前的，last指向最后通过链表来完成而不是数组

![image-20220413122420263](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20220413122420263.png)

3，LinkedList相较于ArrayList

增删的速度更快查改的速度较慢

4，LinkedList是线程不安全的


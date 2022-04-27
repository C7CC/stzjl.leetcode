## TreeSet,TreeMap源码分析

1，二者在无参构造器时均为无序

2，传入一个Comparator类的匿名内部类实现了compare方法后才可根据compare中自己规定的方法进行排序

3，均为按照key来进行排序，与其value无关

```Java
TreeSet/TreeMap<Object> objects = new TreeSet/TreeMap<>(
new Comparator<Object>() {//匿名内部类
    @Override
    public int compare(Object o1, Object o2) {//重写compare方法实现自己的排序逻辑
        return 0;
    }
}
);
```

一，传入

```Java
public boolean add(E e) {
    return m.put(e, PRESENT)==null;//此为TreeSet来演示所以value为默认的null
}
```

二，将key-value封装为结点

```Java
public V put(K key, V value) {
    Entry<K,V> t = root;
    if (t == null) {
        compare(key, key); // type (and possibly null) check

        root = new Entry<>(key, value, null);
        size = 1;
        modCount++;
        return null;
    }
```

三，进行比较

```Java
Comparator<? super K> cpr = comparator;
if (cpr != null) {
    do {
        parent = t;
        cmp = cpr.compare(key, t.key);//调用自己的传入的比较方法
        if (cmp < 0)
            t = t.left;
        else if (cmp > 0)
            t = t.right;
        else
            return t.setValue(value);
    } while (t != null);
}
```
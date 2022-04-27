## ArrayList源码分析

```java
public ArrayList() {
    this.elementData = DEFAULTCAPACITY_EMPTY_ELEMENTDATA;
}
```

### 先将ArrayList默认为{}既为null（调用无参构造时，有参构造器会开空间）

```java
public boolean add(E e) {
    ensureCapacityInternal(size + 1);  // Increments modCount!!
    elementData[size++] = e;
    return true;
}
```

### 开始进行验证是否有空间

```java
private void ensureCapacityInternal(int minCapacity) {
    ensureExplicitCapacity(calculateCapacity(elementData, minCapacity));
}
```

### 1，先确认是否初始化

```java
private static int calculateCapacity(Object[] elementData, int minCapacity) {
    if (elementData == DEFAULTCAPACITY_EMPTY_ELEMENTDATA) {//判断是否用构造器规定空间
       return Math.max(DEFAULT_CAPACITY, minCapacity);//没有则默认为10(仅第一次可能会进入)
    }
    return minCapacity;
    }
```

### 2，判断空间是否足够

```java
private void ensureExplicitCapacity(int minCapacity) {
    modCount++;

    // overflow-conscious code
    if (minCapacity - elementData.length > 0)//进行判断
        grow(minCapacity);
}
```

### 3，空间不足则会开空间

```java
private void grow(int minCapacity) {
    // overflow-conscious code
    int oldCapacity = elementData.length;
    int newCapacity = oldCapacity + (oldCapacity >> 1);//新空间为原来空间的1.5倍
    if (newCapacity - minCapacity < 0)//默认开空间且第一次开，newCapacity为0结果为-1
        newCapacity = minCapacity;//空间开为10
    if (newCapacity - MAX_ARRAY_SIZE > 0)//是否达到能开空间的上限
        newCapacity = hugeCapacity(minCapacity);
    // minCapacity is usually close to size, so this is a win:
    elementData = Arrays.copyOf(elementData, newCapacity);//数组拷贝返回数组
}
```

### 总结

1，ArrayList无参构造器默认空间为null所以需要单独判断其是否有空间(与Vector默认有空间不同)

2，空间满后均以1.5倍扩容

3，底层维护了transient Object [] elementDate数组其中transient表示不可序列化/串行化应为ArrayList是线程不安全的但是效率较高

4，每次扩容后地址都会改变Arrays.copyOf

5，jdk1.2时出现

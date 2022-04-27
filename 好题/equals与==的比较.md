## equals与==的比较

1，equals只能用来对引用数据类型进行比较，默认为比较地址，一般会被类重写变为就比较值

2，==引用类型和基本数据类型都可以比较  引用类型为比较地址，基本数据类型为值的比较

注意

==的比较是根据其真实地址而不是hashCode（可以认为hashCode只是对象地址的一个表现形式hashCode变化不一定真实地址变化hashCode可被重写，有些程序是按hashCode有些不是）

## 基础数据类型与其包装类比较细节

### ==

1，两个Integer进行比较时若在-128~127返回true（此范围内会直接从数组中存取，即缓冲区）超出此范围返回flase

Integer较特殊

```java
Integer a = 100;
Integer b = 100;
Integer c = 200;
Integer d = 200;
System.out.println(a == b);//true
System.out.println(c == d);//false
```

2，基本数据类型和包装类比较时会变为值比较

```java
Double a = 100.0;
int b = 100;
System.out.println(a == b);//true -- > 值比较
```

### equals（只有引用数据类型有，基本数据类型没有方法）

1，先比较类型是否相同，类型相同再比较值都相同则返回true

2，若equals比较的为基本数据类型则先将其变为对应的包装类再进行比较

```Java
Long a = 100l;
int b = 100;
long c = 100l;
System.out.println(a.equals(b));//false// a -> Long  , b -> Integer
System.out.println(a.equals(c));//true// a -> Long  , c -> Long
```


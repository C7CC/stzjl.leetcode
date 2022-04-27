# String

Sting是一个final类其中有保存字符串的属性public final char value[]

所以字符串确定后地址不能改变(因为final)

<img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20220411181648759.png" alt="image-20220411181648759" style="zoom:80%;" />

s为直接创建赋值

s2为调用构造器来赋值

创建对象的String直接返回的是堆中的对象地址，对象中维护了value属性来指向常量池(HaseCode会直接返回常量池中地址但本质不是直接指向常量池中地址，intern()方法会直接返回String对象在常量池中的属性地址)

![image-20220411190941054](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20220411190941054.png)

## hashCode

String将hashCode方法进行了重写

```Java
public int hashCode() {
    int h = hash;
    if (h == 0 && value.length > 0) {
        char val[] = value;

        for (int i = 0; i < value.length; i++) {
            h = 31 * h + val[i];//按内容进行赋予hashCode
        }
        hash = h;
    }
    return h;
}
```

Stringhash的hashCode是根据内容来的而不是其地址（改变hashCode不会改变其真实地址hashCode仅为地址的一种表示方式）

## String存放的底层优化

1，两字符串直接相加若常量池中已有相同的字符串则直接返回常量池中的地址

2，若为两个变量相加则会StringBuffer sb = new StringBuffer(); 再调用 sb.append()方法来添加最后返回是一个对象所以在堆区而不是常量池

```Java
String a = "123456";
String b = "123";
String c = "456";
System.out.println(a == "123" + "456");//true 均为常量池
System.out.println((b + c) == a);//false 前堆中对象，后常量池
```




## final

### 1，final是声明常量(不变的量，定值不能改变)的所以final修饰的属性会存放到常量池



<img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20220412071736302.png" alt="image-20220412071736302" style="zoom: 80%;" />

![image-20220412071857513](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20220412071857513.png)

体现了对于引用数据类型final是保证其地址不会改变而不是其中的值不能改变

### 2，String中保存字符串属性为 private final char value[] 因为有private只能通过其给的方法来修改不能从外部手动修改

```JAVA
//证明了final对于引用类型为确保地址不被改变
final int a[] = {1, 2, 3, 4};
System.out.println(a.hashCode());
a[0] = 6;
System.out.println(a.hashCode());
//二者hashCode相同(既地址未改变)
```

### 

### 3，final的作用

1，修饰类时代表该类不能被继承

2，修饰方法时该方法不能被重写（注意是重写而不是重载）

3，修饰属性时该属性放入常量池（方法区中）引用类型为地址，基本类型为值

4，final修饰的属性一定要初始化，即使在成员位置也不会默认初始化因为其无法改变

作用范围总结（比一般修饰符要广）

类，属性，方法，局部变量
# IO流

## 一，节点流

### 1，IO流分为字节流（二进制文件），字符流（字符，文本文件）

![image-20220416142959736](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20220416142959736.png)

### 2，两种输入方法对比

```Java
//1.一个一个读
FileInputStream fileInputStream = new FileInputStream("e:\\666.jpg");
int read = 0;
if ((read = fileInputStream.read()) != -1) {//此处read()返回的是读到的信息
System.out.println(new String(read));
}

//创建缓冲数组一次读入多个
FileInputStream fileInputStream = new FileInputStream("e:\\666.jpg");
byte a[] = new byte[1024];//a[]即为缓冲数组
int lenth = 0;
if ((lenth = fileInputStream.read(a)) != -1) {//此方法返回的的是读取到的字节数(返回-1表示读取完)
//一次读入读到的字节数，最大为a[]的规定
System.out.println(new String(a, 0, lenth));//此处a为读取到的字节内容
}
```

###### String的API使用

new String (byte [])	将字节数组转为String

new String (byte[], off, length)	将字节数组的指定范围转为String

### 3，两种输出方法比较

###### 一，输出方法的特殊之处

1，OutputStream.write (filefullpath, true/false)此处true代表追加内容，false代表覆盖原来内容

2，一定要flush/close才能够写入，不然不会写入

###### 二，输出方式

```Java
//1，直接输出
FileOutputStream fileOutputStream = new FileOutputStream("e:\\666.jpg");
fileOutputStream.write("are you ok ?".getBytes());
fileOutputStream.close();

//2，规定输出数
FileOutputStream fileOutputStream = new FileOutputStream("e:\\666.jpg");
byte b[] = new byte[1024];
int length = 0;
fileOutputStream.write(b, 0, length);
fileOutputStream.close();
```

###### String的API使用

Sting.getBytes()可将String转为字节数组

### 4，读取和输入的联合使用（文件的复制）

```Java
FileInputStream fI = null;
FileOutputStream fO = null;
try {
    fI = new FileInputStream("E:\\666.jpg");
    fO = new FileOutputStream("E:\\888.jpg",true);//追加方式写入
    byte b[] = new byte[1024];
    int readline = 0;
    while ((readline = fI.read(b)) != - 1) {
        fO.write(b, 0, readline);
    }
} catch (FileNotFoundException e) {//catch异常而不用抛出可以在快速找到错误所在
    throw new RuntimeException(e);
} catch (IOException e) {
    e.printStackTrace();
} finally {//最后不论是否成功都要关闭，节约资源
    try {
        fI.close();
        fO.close();//关了才能写入
    } catch (IOException e) {
        e.printStackTrace();
    }
}
```

### 其余与之类似不再举例

## 二，包装流/处理流

1，包装流不直接处理数据源，包装流控制节点流来间接操作数据源

2，包装流用法基本和节点流相同，不同为多了一些方法便于操作，关闭包装流节点流也会被关闭

## 三，对象流

1，对象流也是包装流的一种

#### 序列化，反序列化

1，存储的不仅是数据的值而且还有数据的类型

2，ObjectInputStream，ObjectOutputStream

3，序列化顺序和反序列化顺序要一致

###### 注意

1，子类对象序列化时父类不用序列化也不会报错，若父类没有序列化则反序列化时会默认调用父类的无参构造器，若没有无参构造器则报错（序列化的是对象不是类）

###### 反序列化时子类对象不会调用构造器故若父类实现了Serializable则不用其构造器，若父类没有实现Serializable则父类及其上的超类都会调用构造器进行初始化（不论超类是否实现了Serializable）

> 父类实现Serializable则会被序列化但若没有则反序列化时需调用父类的无参构造器，因为加载子类对象时会先初始化父类对象，此对象不会在堆上而是将属性保存在子类的对象堆空间中（此为非静态属性，静态属性在类加载时就初始化了，保存在方法区中故不在子类对象中，与子类对象没有关系）

2，父类对象序列化则其子类也会默认序列化

3，类中所以属性都会被序列化，除了static，transient修饰的不会被序列化（static属于类而不是对象，transient修饰的表示不会被序列化）




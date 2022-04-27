## 静态方法（static）的调用

###### 静态成员是属于类的与对象无关，类加载实在编译时进行所以静态成员是编译类型的静态成员而不是运行类型的。

```Java
class Test {
    public static void hello() {
        System.out.println("hello");
    }
}

class MyApplication {
    public static void main(String[] args) {
        Test test = null;
        test.hello();//即使没有运行类型也可以调用静态成员因为其是编译类型的静态成员
    }
}
```
## interface接口

1，用interface替换class，interface默认有abstract

2，jdk7.0时接口不能有具体的方法体，jdk8.0及以后接口中用static，default修饰的方法可以有具体的方法体

3，抽象类实现接口不用实现方法，接口与接口间为继承关系

4，接口中的方法默认有public abstract修饰

5，接口中的属性为public final static 修饰调用时可以不用类加载（底层优化）

6，接口修饰符只能为public/默认，和类一样

7，接口多态性其实就时重写了其方法

###### 注意

接口可以作为编译类型来接受其实现子类的对象

```Java
public class test {
    public static void main(String[] args) throws IOException {
        a b = new b();//相当于父类编译类型指向子类运行类型
    }
}

interface a {}
class b implements a { }
```
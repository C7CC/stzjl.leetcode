## 枚举(enum)

1，本质就是定义对象如 public final static XXX xxx = new XXX();使用enum枚举后可简化为XXX();

2，所以可以调用方法(因为是对象)

3，枚举类的本质还是类

4，enum默认继承了Enum

## 枚举细节说明

###### enum在后台运行时的变化

```Java
private AccountType(){ System.out.println(“It is a account type”); }//此为无参构造器有参同理
//1,运行时会在构造器再加入两个类型
private AccountType(String s, int a){
    super (s, a);
    System.out.println(“It is a account type”); 
}
/*=================================================*/
//2,枚举类型会被修饰
public static final SERSON SPRING ();
public static final SERSON SUMMER ();
//3,还会加入一段静态代码块
static {//对其枚举对象进行初始化
    SPRING = new SERSON ("SPRING", 0);
    SUMMER = new SERSON ("SUMMER", 0);
    $VALUES = new SERSON {//放入$VALUES数组便于进行查找
        SPRING,SUMMER;
    }
}
```

###### 引例

```Java
enum AccountType
{
    SAVING, FIXED, CURRENT;
    private AccountType()
    {
        System.out.println("It is a account type");//该语句最终会输出三次
        //因为枚举有三个实例对象所以在静态代码块中进行了三次对象初始化调用了三次构造器所以会输出三次
    }
}
class EnumOne
{
    public static void main(String[]args)
    {
        System.out.println(AccountType.FIXED);
    }
}
```

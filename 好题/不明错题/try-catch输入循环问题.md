```java
while (true) {
    String number = "";
    int num = 0;
    try {
        num = scanner.nextInt();
        System.out.println("输入成功");
    } catch (Exception e) {
        System.out.println("请重新输入");
    }
}
```

尚不清楚的错误原因(导致无限循环)

```Java
while (true) {
    String number = "";
    number = scanner.next();
    int num = 0;
    try {
        num = Integer.parseInt(number);
        System.out.println("输入成功");
    } catch (Exception e) {
        System.out.println("请重新输入");
    }
}
```

正确的示范
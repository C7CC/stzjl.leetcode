## 异常捕获中return

```Java
private static int test() {
    int temp = 1;
    try {
      System.out.println(temp);
      return ++temp;
    } catch (Exception e) {
      return ++temp;//会返回2而不是3
    } finally {
      ++temp;
    }
  }
```

### return处会先进行++temp，renturn会保存此时的temp值所以即使finally里有++temp返回的temp值也不再变化

### 总结

### return会保存值所以值不会改变
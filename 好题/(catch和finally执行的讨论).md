catch和finally执行的讨论

<img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20220411091128580.png" alt="image-20220411091128580" style="zoom:67%;" />

finally必须执行(不论是否发生异常)

catch中有return会进行结束所以finally会覆盖catch强制执行finally中语句

但catch中return前的语句仍可以执行

<img src="C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20220411092313281.png" alt="image-20220411092313281" style="zoom:80%;" />

此处体现了前++/--会先于语句进行

![image-20220411111314028](C:\Users\DELL\AppData\Roaming\Typora\typora-user-images\image-20220411111314028.png)

finally一定会执行，所以快结束时会先执行finally中语句
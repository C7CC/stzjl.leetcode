## Switch

1，Switch中传入和判断的值只能为（byte，short，int，char，enum，String）

2，case中只能为常量表达式而不能为变量（变量均不行）

3，若没有break则进入该语句后会跳过下面语句的判断直接执行下面的语句除非下面语句有break否则会一直执行到最后的语句

4，default语句是在没有匹配到时才执行不是一定要执行。
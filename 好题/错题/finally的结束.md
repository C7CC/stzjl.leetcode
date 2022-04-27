## finally的结束

### 如果在finally之前有System.exit(0)；这样的语句会终止JVM虚拟机，这时有finally也不会执行（相当于强行结束程序）

### return会保存当前的值所以即使暂时不执行return且值发生变化return的值也不会变化（多见于try-catch-finally中）
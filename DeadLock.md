# DeadLock死锁


------

[TOC]

## 实验过程


进入文件 Deadlock.java，对 count 进行减法操作，当 count的值为0，执行线程a。同时， 线程t对线程b 进行run的调度。


```java
  class Deadlock implements Runnable{
	  A a = new A();
	  B b = new B();
	  
	  //构造函数
	  Deadlock(){
		  Thread t = new Thread(this);
		  int count = 20000;
		  
		  t.start();
		  while(count-- >0);
		  a.methodA(b); 		  
	  }

	@Override
	public void run() {
		// TODO Auto-generated method stub
		b.methodB(a);
	}
	public static void main(String args[]){
		new Deadlock();
	}
}
```

执行以下语句：
`javac Deadlock.java`
然后在 Windows 对 Deadlock.bat 进行编译





## 实验结果

![deadlock](http://ww1.sinaimg.cn/large/e3bf9b05gw1f9n0hmtclmj20bf0bejt2.jpg)




##产生死锁的4个必要条件
 

* 互斥条件：  一个资源每次只能被一个进程使用。
* 请求与保持条件：  一个进程因请求资源而阻塞时，对已获得的资源保持不放。
* 不剥夺条件:  进程已获得的资源，在末使用完之前，不能强行剥夺。
* 循环等待条件:  若干进程之间形成一种头尾相接的循环等待资源关系。



## 实验心得

通过本次实验，我复习了上学期学习的有关死锁的内容，同时也了解了java 中synchronized关键字的相关知识。
本次实验没有遇到太多问题，按照ta给的ppt做即可完成。




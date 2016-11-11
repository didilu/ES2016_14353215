#Deadlock
***
##产生死锁的截图
![](http://a3.qpic.cn/psb?/V11g2aQW16thea/nbZcF5DQct1wSiDqYE.VbDk.zWmTQ5ZumOunlEGrFtM!/b/dNoAAAAAAAAA&bo=zQLMAQAAAAADByA!&rf=viewer_4)<br>

![](http://a3.qpic.cn/psb?/V11g2aQW16thea/Rauf*Bai63WP*FrGj7qmSHYeFad19JEeAgA1UMbGHyk!/b/dAoBAAAAAAAA&bo=0QLOAQAAAAADADk!&rf=viewer_4)<br>
##产生死锁的4个必要条件
1. 资源互斥：一个资源每次只能被一个进程使用。
2. 占有且等待：一个进程因请求资源而阻塞时，对已获得的资源保持不放。
3. 非抢占：进程已获得的资源，在末使用完之前，不能强行剥夺。
4. 循环等待：若干进程之间形成一种头尾相接的循环等待资源关系。
##这个程序产生死锁的原因
    
    class A{
    	synchronized void methodA(B b){
		b.last();
	}
	synchronized void last(){
		System.out.println("Inside A.last()");
	}
   	}
   
    	class B{
		synchronized void methodB(A a){
			a.last();
		}
		synchronized void last(){
			System.out.println("Inside B.last()");
		}
    	}

		class Deadlock implements Runnable{
		A a=new A();
		B b=new B();

		Deadlock(){
			Thread t = new Thread(this);
			int count = 20000;
		
			t.start();
			while(count-->0);
			a.methodA(b);
		}
		public void run(){
			b.methodB(a);
		}
	
		public static void main(String args[]){
			new Deadlock();
		}
		}

1.当调用java Deadlock的时候，因为Runnable一运行就会调用run()函数，所以会调用b.method(A)，此时线程1访问的是 B的一个synchronized同步代码块，会得到B的对象锁;

2.在还没有来得及执行调用a.last()函数时，这时候刚好count到20000，所以执行a.method(B)，此时线程2访问的是A的一个synchronized同步代码块，获得A的对象锁;

3.而如果要执行a.last()的话必须得等线程1先释放A的对象锁，要执行b.last()的话必须得等线程2先释放B的对象锁,所以这里会产生死锁。

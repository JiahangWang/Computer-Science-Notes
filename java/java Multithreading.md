# <center>java 多线程</center>

## <font class="text-color-13" color="#ffeb3b">概述</font>
* 进程是一个应用程序。（1个进程是一个软件）
* 线程是一个进程中的执行场景 / 执行单元，一个进程可以启动多个线程。
* 运行java程序会先启动JVM，而JVM就是一个进程，JVM再启动一个主线程调用main方法，同时启动一个GC线程负责看护，回收垃圾。所有java程序至少有两个线程并发。（GC线程和main方法的主线程）
* 进程和线程区别：
进程A和进程B的内存独立不共享。
java中，线程A和线程B堆内存和方法区内存共享，栈内存独立，一个线程一个栈。每个栈和栈之间互不干扰，各自执行，称为多线程并发，提高程序处理效率。

### <font class="text-color-15" color="#ff9800">java 并发编程</font>
* Java的高并发主要是通过以下几种方式实现的：

	1. 多线程并发编程：Java内置支持多线程并发编程，可以方便地创建、启动和管理多个线程，以实现并发执行任务的效果。

	2. 线程池技术：Java提供了Executor框架和线程池技术，可以通过预先创建一定数量的线程池来重复使用线程，避免线程的频繁创建和销毁。

	3. 锁技术：Java提供了synchronized关键字和Lock接口等锁技术，可以实现对共享资源的互斥访问，避免并发问题的出现。

	4. 并发容器：Java提供了一系列的并发容器，如ConcurrentHashMap、ConcurrentLinkedQueue等，可以在多线程环境下实现对集合元素的安全访问和操作。

	5. 原子类和CAS：Java提供了一些原子类，如AtomicInteger、AtomicLong、AtomicBoolean等，以及CAS（Compare and Swap）技术，可以实现对共享变量的安全原子操作。

	6. 并发框架：Java提供了并发框架，如Fork/Join框架和CompletableFuture框架等，可以方便地实现并行计算和异步编程。
  

* 通过以上这些技术的组合使用，Java能够支持高并发的应用场景，提高程序的执行效率和吞吐量，提高系统的可用性和可靠性。

## <font class="text-color-13" color="#ffeb3b">实现线程的方式</font>
### <font class="text-color-15" color="#ff9800">第一种：继承 Thread 类</font>
* 编写一个类，直接继承 java.lang.Thread，重写 run 方法。
* void <font class="text-color-11" color="#8bc34a">run</font>() ：该方法在执行时由线程运行。
* void <font class="text-color-11" color="#8bc34a">start</font>() 安排此线程开始执行。
```java
    public static void main(String[] args) {
        // 这里是 main 方法，这里的代码属于主线程，在主栈中压栈
        // 新建一个分支线程对象
        MyThread myThread = new MyThread();

        // 启动线程
        myThread.start();
        // 这里的代码还是运行在主线程中
        for (int i = 0; i < 1000; i++) {
            System.out.println("主线程 ---> " + i);
        }

    }

class MyThread extends Thread {
    @Override
    public void run() {
        // 编写程序，这段程序运行在分支线程中（分支栈）。
        for (int i = 0; i < 1000; i++) {
            System.out.println("分支线程 ---> " + i);
        }
    }
}
```
* start() 方法的作用是：启动一个分支线程，在JVM中开辟一个新的栈空间。只要新的栈空间开辟出来，start() 方法就结束了，线程启动成功。
* 启动成功的线程会自动调用 run() 方法，并且run()方法在分支栈的底部（压栈）。main() 方法在主栈底部，run和main是平级的。(只调用 run() 方法不会开辟新的栈空间，还是在主栈中执行)
* run() 当中异常不能 throws，只能 try catch，因为 run() 方法在父类中没有抛出任何异常，子类不能比父类抛出更多异常。
---

### <font class="text-color-15" color="#ff9800">第二种：实现 Runnable 接口</font>

* 定义一个可运行的类，实现 java.lang.Runnable 接口，实现 run() 方法。
* <font class="text-color-11" color="#8bc34a">Thread</font>(Runnable task) ：Thread构造器，初始化一个新Thread。
```java
    public static void main(String[] args) {
        // 这里是 main 方法，这里的代码属于主线程，在主栈中压栈

        // 创建一个可运行的对象，将可运行的对象封装成一个线程对象
        Thread myThread = new Thread(new MyRunnable());

        // 启动线程
        myThread.start();
        // 这里的代码还是运行在主线程中
        for (int i = 0; i < 100; i++) {
            System.out.println("主线程 ---> " + i);
        }

    }

class MyRunnable implements Runnable{

    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println("分支线程 ---> " + i);
        }
    }
}
```
* 第二种方式实现接口比较常用，因为一个类实现了接口，它还可以继承其它的类，更灵活。
* <font class="text-color-15" color="#ff9800">匿名内部类</font>实现 Runnable 接口
```java
    public static void main(String[] args) {
        // 这里是 main 方法，这里的代码属于主线程，在主栈中压栈

        // 匿名内部类实现 Runnable 接口，封装成线程对象
        Thread myThread = new Thread(new Runnable() {
            @Override
            public void run() {
                for (int i = 0; i < 100; i++) {
                    System.out.println("分支线程 ---> " + i);
                }
            }
        });

        // 启动线程
        myThread.start();
        // 这里的代码还是运行在主线程中
        for (int i = 0; i < 100; i++) {
            System.out.println("主线程 ---> " + i);
        }

    }
}
```
* <font class="text-color-15" color="#ff9800">Lamda表达式</font>实现 Runnable 接口
```java
    public static void main(String[] args) {
        // 这里是 main 方法，这里的代码属于主线程，在主栈中压栈
        
        // Lamda表达式实现 Runnable 接口，封装成线程对象
        Thread myThread = new Thread(() -> {
            for (int i = 0; i < 100; i++) {
                System.out.println("分支线程 ---> " + i);
            }
        });

        // 启动线程
        myThread.start();
        // 这里的代码还是运行在主线程中
        for (int i = 0; i < 100; i++) {
            System.out.println("主线程 ---> " + i);
        }

    }
}
```
### <font class="text-color-141" color="#ff9800">第三种：实现 Callable 接口</font>
* 创建 FutureTask 对象。
* <a href="https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/util/concurrent/FutureTask.html">FutureTask文档</a>

* 这种方式实现的线程可以获取线程的返回值
* V <font class="text-color-11" color="#8bc34a">get</font>() ：如有必要，等待计算完成，然后检索其结果。
* 效率较低，在获取执行结果时，当前线程受阻塞。
```java
    public static void main(String[] args) throws ExecutionException, InterruptedException {

        // 创建 FutureTask 对象，传入对 Callable 接口的实现
        FutureTask<Integer> task = new FutureTask(new MyCall());

        // 创建线程对象，传入 FutureTask 对象
        Thread myThread = new Thread(task);
        myThread.start();

        // 可能导致当前线程阻塞
        int result = task.get();
        
    }
```
```java
class MyCall implements Callable<Integer>{

    @Override
    public Integer call() throws Exception {
        int res = 100;
        return 100;
    }
}
```


## <font class="text-color-13" color="#ffeb3b">线程的生命周期</font>
![](https://huatu.98youxi.com/markdown/work/uploads/upload_a4cf4b14a80c48c121e6081f9aa181f4.jpg)


## <font class="text-color-121" color="#ffeb3b">Thread 常用方法</font>
* final void <font class="text-color-11" color="#8bc34a">setName</font>(String name) ：将此线程的名称更改为等于 argument name。
* final String <font class="text-color-11" color="#8bc34a">getName</font>() ：返回此线程的名称，默认名字：Thread-0，Thread-1 ...
* static Thread <font class="text-color-11" color="#8bc34a">currentThread</font>() ：静态方法，返回当前线程的 Thread 对象。
```java
    public static void main(String[] args) {
        // 这里是 main 方法，这里的代码属于主线程，在主栈中压栈

        // Lamda表达式实现 Runnable 接口，封装成线程对象
        Thread myThread = new Thread(() -> {
            for (int i = 0; i < 50; i++) {
                System.out.println("分支线程 ---> " + i);
            }
            System.out.println(Thread.currentThread().getName()); // Thread-0
        });

        // 启动线程
        myThread.start();
        // 这里的代码还是运行在主线程中
        for (int i = 0; i < 50; i++) {
            System.out.println("主线程 ---> " + i);
        }
        System.out.println(Thread.currentThread().getName());  // main

    }
```
* static void <font class="text-color-11" color="#8bc34a">sleep</font>(long millis) ：使当前正在执行的线程休眠（进入阻塞状态）指定的毫秒数，放弃占有CPU时间片，让给其他线程使用。
```java
        // 每隔一秒执行一次循环中的代码
        for (int i = 0; i < 50; i++) {
            System.out.println(Thread.currentThread().getName() + " --> " + i);
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
```
* void <font class="text-color-11" color="#8bc34a">interrupt</font>() 中断此线程，可以利用 catch 语句块终止睡眠。
* final void <font class="text-color-11" color="#8bc34a">stop</font>() ：已弃用，这种方法本质上是不安全的，直接杀死线程，可能导致数据丢失。

## <font class="text-color-121" color="#ffeb3b">终止线程</font>
* 使用布尔标记位
```java
    public static void main(String[] args) {
        MyRunnable myRunnable = new MyRunnable();
        Thread myThread = new Thread(myRunnable);
        
        // 启动 myThread 线程
        myThread.start();

        // 主线程睡 3s
        for (int i = 0; i < 3; i++) {
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }

        // 终止线程时，把标记为改为 false
        myRunnable.run = false;

    }


class MyRunnable implements Runnable {

    // 布尔标记
    boolean run = true;

    @Override
    public void run() {
        for (int i = 0; i < 10; i++) {
            if(run){
                System.out.println(Thread.currentThread().getName() + " --> " + i);
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
            else{
                // 结束之前保存数据
                return; // 终止当前线程
            }
        }
    }
}
```
* 使用 catch 语句块终止线程
```java
public static void main(String[] args){

        Thread myThread = new MyThread();

        // 启动 myThread 线程
        myThread.start();

        // 主线程睡 3s
        try {
            Thread.sleep(3000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        // 终止分支线程
        myThread.interrupt();

    }
}

class MyThread extends Thread {

    @Override
    public void run() {
        for (int i = 0; i < 10; i++) {
            try{
                if(!isInterrupted()){
                    System.out.println(Thread.currentThread().getName() + " --> " + i);
                    Thread.sleep(1000);
                }
                else throw new InterruptedException();
            }catch (InterruptedException e){
                System.out.println("保存数据,退出");// 结束之前保存数据
                return; // 终止当前线程
            }
        }
    }
```

## <font class="text-color-121" color="#ffeb3b">线程调度</font>
* 常见的线程调度模型：
    1. 抢占式调度模型：线程的优先级高，抢到的CPU时间片概率高一些/多一些，java采用的就是抢占式调度模型。
    2. 平均式调度模型：平均分配CPU时间片。每个线程占有的CPU时间片长度一样。
### <font class="text-color-15" color="#ff9800">线程调度相关方法</font>
* final void <font class="text-color-11" color="#8bc34a">setPriority</font>(int newPriority) 更改此线程的优先级。
* final int <font class="text-color-11" color="#8bc34a">getPriority</font>() 返回此线程的优先级。
* 最低优先级：1 
* 默认优先级：5
* 最高优先级：10
```java
    public static void main(String[] args) {

        Thread currentThread = Thread.currentThread();

        Thread myThread = new Thread(() -> {
            System.out.println(Thread.currentThread().getName() + "线程的默认优先级：" + Thread.currentThread().getPriority());
            Thread.currentThread().setPriority(1);
            // 分支线程循环
            for (int i = 0; i < 100; i++) {
                System.out.println(Thread.currentThread().getName());
            }
        });

        myThread.start(); // 启动分支线程

        System.out.println(currentThread.getName() + "线程的默认优先级：" + currentThread.getPriority());
        currentThread.setPriority(10);
        // 主线程循环
        for (int i = 0; i < 100; i++) {
            System.out.println(Thread.currentThread().getName());
        }

    }
```
* static void <font class="text-color-11" color="#8bc34a">yield</font>() 向调度程序提示当前线程愿意放弃其当前对处理器的使用。会让当前线程从“运行状态”回到“就绪状态”。（回到就绪后有可能还会再次抢到）
```java
    public static void main(String[] args) {

        Thread currentThread = Thread.currentThread();

        Thread myThread = new Thread(() -> {
            // 分支线程循环
            for (int i = 0; i < 100; i++) {
                if(i % 5 == 0){
                    Thread.yield();
                }
                System.out.println(Thread.currentThread().getName() + "--->" + i);
            }
        });

        myThread.start(); // 启动分支线程

        // 主线程循环
        for (int i = 0; i < 100; i++) {
            System.out.println(Thread.currentThread().getName() + "--->" + i);
        }

    }
```

* final void <font class="text-color-11" color="#8bc34a">join</font>() 等待此线程终止。
```java
   public static void main(String[] args) {

        Thread currentThread = Thread.currentThread();

        Thread myThread = new Thread(() -> {
            // 分支线程循环
            for (int i = 0; i < 100; i++) {
                System.out.println(Thread.currentThread().getName() + "--->" + i);
            }
        });

        myThread.start(); // 启动分支线程

        // 主线程循环
        for (int i = 0; i < 100; i++) {
            if(i == 50){
                try {
                    myThread.join(); // myThread线程合并到当前线程中，myThread执行直到结束
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
            System.out.println(Thread.currentThread().getName() + "--->" + i);
        }

    }
```

## <font class="text-color-13" color="#ffeb3b">线程安全</font>
* 什么时候数据在多线程并发的环境下会存在安全问题？（三个条件）
    1. 多线程并发
    2. 有共享数据
    3. 共享数据有修改行为
* 局部变量在栈中，不存在线程安全问题。
* <font class="text-color-11" color="#8bc34a">线程同步机制</font>：线程不能并发，需排队执行。会牺牲一部分效率。
* <font class="text-color-7" color="#03a9f4">异步编程模型</font>：线程t1和t2各自执行，互相不管，谁也不需要等谁，多线程并发，效率较高。
* <font class="text-color-7" color="#03a9f4">同步编程模型</font>：线程t1和t2，其中一个线程执行的时候必须等待另一个线程执行结束，两个线程之间有等待关系，效率较低。

### <font class="text-color-15" color="#ff9800">synchronized()</font>

* 线程同步的语法机制：<font class="text-color-15" color="#ff9800">synchronized()</font> ，后面小括号中传的这个数据必须是多线程共享的数据，才能达到多线程排队。
```java
        synchronized (排队线程的共享的对象){ 
            // 线程同步代码块
        }
```
* () 中写什么？具体看想要让哪些线程同步：
    假设 t1, t2, t3, t4, t5 有5个线程，只希望 t1, t2, t3 排队， t4, t5不需要排队。则在 () 中写一个 t1, t2, t3 共享的对象。而这个对象对于 t4, t5 来说不是共享的。
* <font class="text-color-15" color="#ff9800">对象锁</font>：java中，任何对象都有“一把锁”（标记）。
    1. 假设 t1 先执行了，遇到了synchronized ()，这个时候 t1 自动找 () 中的对象的对象锁，找到之后 t1 会占有这把锁，然后执行同步代码块中的程序，直到同步代码块结束，这把锁才会被 t1 释放。
    2. 假设 t1 已经占有这把锁，此时 t2 也遇到synchronized ()，也会去找 () 中的对象的对象锁，结果这把锁被 t1 占有， t2 只能在同步代码块外等待  t1 结束执行完同步代码块后释放这把锁，然后 t2 占有这把锁，进入同步代码块执行程序。
    3. 注：这里的共享对象一定是你需要排队执行的这些线程所共享的。

	4. <a href="https://blog.csdn.net/guoguo527/article/details/118004077?app_version=5.14.0&csdn_share_tail=%7B%22type%22%3A%22blog%22%2C%22rType%22%3A%22article%22%2C%22rId%22%3A%22118004077%22%2C%22source%22%3A%22unlogin%22%7D&utm_source=app">java 的18把锁</a>

* <font class="text-color-15" color="#ff9800">锁池</font>
![](https://huatu.98youxi.com/markdown/work/uploads/upload_159189774d566edd3caeacb1d93524ff.jpg)
---
### <font class="text-color-141" color="#ff9800">账户类例子</font>
```java
    public static void main(String[] args) {
        // 创建账户对象
        Account act = new Account("act01",10000);
        // 创建两个线程
        Thread t1 = new AccountThread(act);
        Thread t2 = new AccountThread(act);

        t1.setName("t1");
        t2.setName("t2");
        // 启动取款线程
        t1.start();
        t2.start();

    }
```
```java
public class Account {
    // 账号
    private String actno;
    // 余额
    private double balance;

    public Account() {}

    public Account(String actno, int balance) {
        this.actno = actno;
        this.balance = balance;
    }

    public String getActno() {
        return actno;
    }

    public void setActno(String actno) {
        this.actno = actno;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }

    // 取款方法
    public void withdraw(double money) {
        // 以下的代码必须是线程排队的，不能并发。一个线程把这里的代码全部执行结束之后，另一个线程才能进来
        synchronized (this){ // 线程同步代码块
            // 取款之前余额
            double before = this.getBalance();
            // 取款之后余额
            double after = before - money;
            // 模拟网络延迟1秒
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            // 更新余额
            this.setBalance(after);
        }
    }
}
```
```java
public class AccountThread extends Thread {
    // 线程共享同一个账户对象
    private Account act;

    // 通过构造方法传入账户对象
    public AccountThread(Account act) {
        this.act = act;
    }

    @Override
    public void run() {
        // 取款
        act.withdraw(5000);
        System.out.println(Thread.currentThread().getName() + "对账户" + act.getActno() + "取款成功，余额：" + act.getBalance());
    }
}
```
* synchronized 也可以出现在实例方法上，一定锁的是 this ，不能是其他对象，所以不灵活。
* 另一个缺点：synchronized 出现在实例方法上，表示整个方法体都需要同步，可能会无故扩大同步范围，导致程序执行效率降低，所以这种方式不常用。
* 优点：代码更少，更简洁。如果共享的对象就是 this ，并且同步的代码块就是整个方法体，建议使用这种方式。
```java
    public synchronized void withdraw(double money) {
            // 取款之前余额
            double before = this.getBalance();
            // 取款之后余额
            double after = before - money;
            // 模拟网络延迟
            try {
                Thread.sleep(500);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            // 更新余额
            this.setBalance(after);
    }
```
* synchronized 还可以使用在静态方法上，表示找类锁，类锁永远只有一把。即使创建100个对象，类锁也只有一把。
* synchronized 会让程序的执行效率降低，用户体验不好，系统的用户吞吐量降低。解决办法：
    1. 尽量使用局部变量代替实例变量和静态变量。
    2. 如果必须是实例变量，可以考虑创建多个对象，这样实例变量的内存就不共享了。（每个线程对应一个对象，没有数据安全问题）
---
### <font class="text-color-15" color="#ff9800">死锁</font>
* 死锁是指两个或多个线程在互相持有对方需要的锁并且在等待对方释放锁，导致程序无法继续执行下去的情况。

* 这种情况下，所有线程都处于等待状态，无法继续执行下去，形成了一个死循环。如果没有被及时解决，死锁会一直存在，直到程序被强制终止。

* 举个例子，假设线程A持有锁1，等待锁2；线程B持有锁2，等待锁1，那么线程A无法继续执行直到线程B释放锁2，而线程B也无法继续执行直到线程A释放锁1，从而形成死锁。在这种情况下，除非手动中断程序，否则程序将永远无法继续执行下去。

* synchronized 的嵌套使用，可能会导致死锁发生。
```java
        Object o1 = new Object();
        Object o2 = new Object();

        MyThread1 myThread1 = new MyThread1(o1,o2);
        MyThread2 myThread2 = new MyThread2(o1,o2);

        myThread1.start();
        myThread2.start();
```
```java
class MyThread1 extends Thread{
    Object o1;
    Object o2;

    public MyThread1(Object o1, Object o2) {
        this.o1 = o1;
        this.o2 = o2;
    }

    @Override
    public void run() {
        synchronized (o1){
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            synchronized (o2){
            }
        }
    }
}
```
```java
class MyThread2 extends Thread{
    Object o1;
    Object o2;

    public MyThread2(Object o1, Object o2) {
        this.o1 = o1;
        this.o2 = o2;
    }

    @Override
    public void run() {
        synchronized (o2){
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            synchronized (o1){
            }
        }
    }
}
```

### <font class="text-color-15" color="#ff9800">活锁</font>
* 活锁是指当线程间频繁地重试某个操作，但每次尝试都失败时，线程不会被阻塞，而是继续重试，导致CPU时间浪费，但程序无法继续执行的情况。在活锁中，线程并没有被阻塞，它们仍然在运行，但它们一直在重试某个操作而无法继续往下执行。活锁通常是由于线程之间的相互作用导致的，每个线程都试图避免发生死锁，但它们的操作却总是在阻碍对方，导致无法进展。

* 例子
```java
public class BankAccount {
    private int balance;
    private final int overdraftLimit = 500;

    public BankAccount(int balance) {
        this.balance = balance;
    }

    public synchronized void withdraw(int amount) {
        while (balance < amount) {
            try {
                wait();
            } catch (InterruptedException e) {
                // do nothing
            }
        }
        balance -= amount;
    }

    public synchronized void deposit(int amount) {
        balance += amount;
        notifyAll();
    }

    public synchronized void transfer(BankAccount to, int amount) {
        while (balance < amount) {
            try {
                wait();
            } catch (InterruptedException e) {
                // do nothing
            }
        }
        balance -= amount;
        to.balance += amount;
        notifyAll();
    }
}
```
* 这里定义了一个银行账号类，其中`withdraw`方法表示从账户中取款，`deposit`方法表示向账户中存款，`transfer`方法表示将金额转移至另一个账户。在这些方法中，我们都使用`synchronized`关键字保证了线程安全。如果一个线程调用`withdraw`方法时发现余额不足，则会进入等待状态，直到有其他线程调用`deposit`方法存入足够的金额，并通过`notifyAll`方法唤醒所有等待中的线程。在`transfer`方法中也是类似的，如果当前账户余额不足，则等待直到有足够的金额。这里的问题在于，如果同时有两个线程分别尝试从账户A和账户B转移金额，但是由于等待对方释放锁，两个线程都无法进行转移，这就是一个典型的活锁问题。为了解决这个问题，我们需要引入一些额外的机制，例如引入随机等待时间或者优先级调整，以打破死锁状态。

#### <font class="text-color-7" color="#03a9f4">活锁和死锁区别</font>
* 死锁和活锁都是多线程程序中可能出现的问题，二者的区别在于：

	1. 死锁指的是两个或多个线程互相持有对方需要的资源而无法继续执行的情况。每个线程都在等待对方释放资源，导致所有线程都被阻塞，程序无法继续执行。
  
	2. 活锁指的是两个或多个线程在互相响应对方的动作而无法继续执行的情况。例如，两个人在走路时互相让路，结果都一直让对方，导致无法通过。在活锁中，线程不会被阻塞，它们一直在运行，但程序无法继续执行。
  

* 因此，死锁和活锁都是多线程程序中的问题，但是它们的原因和表现形式是不同的。

## <font class="text-color-13" color="#ffeb3b">守护线程</font>
* java 中线程分为用户线程和守护线程。一般守护线程（后台线程）是一个死循环，所有的用户线程只要结束，守护线程自动结束。其中具有代表性的是垃圾回收线程。
```java
    public static void main(String[] args) {
        MyDaemon myDaemon = new MyDaemon();
        // 将线程设置为守护线程
        myDaemon.setDaemon(true);
        myDaemon.start();

        for (int i = 0; i < 5; i++) {
            System.out.println(Thread.currentThread().getName() + "--->" + i );
            try {
                Thread.sleep(500);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }

}
```
```java
class MyDaemon extends Thread{
    @Override
    public void run() {
        int i = 0;
        while (true) {  // 死循环，用户线程结束，守护线程自动终止
            System.out.println(Thread.currentThread().getName() + "--->" + (++i));
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```
---
### <font class="text-color-15" color="#ff9800">定时器</font>
* java.util.Timer 类
* [](https://)https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/util/Timer.html
* <font class="text-color-11" color="#8bc34a">Timer</font>(String name, boolean isDaemon) ：创建一个新的计时器，其关联的线程具有指定的名称，并且可以指定为 作为守护进程运行。
* void <font class="text-color-11" color="#8bc34a">schedule</font>(TimerTask task, Date time) ：安排指定的任务在指定的时间执行。
* void <font class="text-color-11" color="#8bc34a">schedule</font>(TimerTask task, long delay, long period) 安排指定任务重复固定延迟执行，在指定延迟后开始。
* void <font class="text-color-11" color="#8bc34a">schedule</font>(TimerTask task, long delay) 安排指定的任务在指定的延迟后执行。
* 需要实现 TimerTask 类。
```java
        // 创建定时器对象
        Timer timer = new Timer();
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH-mm");
        Date firstTime = sdf.parse("2023-2-2 03-59");
        // 指定定时任务（任务，第一次执行时间，间隔）
        timer.schedule(new LoggerTimeTask(),firstTime,1000 * 10);
```
```java
class LoggerTimeTask extends TimerTask{

    @Override
    public void run() {
        System.out.println("正在执行");
    }
}
```

## <font class="text-color-13" color="#ffeb3b">Wait 和 Notify</font>
* Object 类中的方法
* final void <font class="text-color-11" color="#8bc34a">wait</font>() ：让正在此对象的监视器上的线程进入等待状态，并且释放占有的该对象的锁。
* final void <font class="text-color-11" color="#8bc34a">notify</font>() ：唤醒在此对象的监视器上等待的单个线程。
* final void <font class="text-color-11" color="#8bc34a">notifyAll</font>() ：唤醒在此对象的监视器上等待的所有线程。

### <font class="text-color-15" color="#ff9800">wait() 等待队列</font>
* 等待队列中的线程是按照调用 `wait()` 方法的顺序进入的，先调用 `wait()` 方法的线程先进入等待队列，后调用的线程后进入等待队列。在调用 `notify()` 或 `notifyAll()` 方法时，等待队列中的线程按照这个顺序被唤醒，即先进入等待队列的线程先被唤醒。但是，Java 并不保证每次唤醒的顺序都是相同的，因此不能依赖于这个顺序来编写代码。

### <font class="text-color-141" color="#ff9800">生产者和消费者模式</font>
* 生产线程负责生产，消费线程负责消费，要达到均衡。
* Wait 和 Notify 方法建立在线程同步的基础之上。因为多线程需要同时操作一个仓库。有线程安全问题。
```java
    public static void main(String[] args) {

        // 创建一个共享仓库对象
        List list = new ArrayList();
        // 创建生产和消费线程
        Thread t1 = new Thread(new Producer(list));
        Thread t2 = new Thread(new Consumer(list));

        t1.setName("生产者线程");
        t2.setName("消费者线程");

        t1.start();
        t2.start();

    }
```
```java
// 生产线程
class Producer implements Runnable{
    private List list;

    public Producer(List list) {
        this.list = list;
    }

    @Override
    public void run() {
        while(true){
            synchronized (list){ // 给 list 加锁
                if(list.size() > 0){ // 大于0,说明仓库中已经有一个元素了。
                    // 当前线程进入等待状态，并且释放 list 的锁。
                    try {
                        list.wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
                // 程序能执行到这里，说明仓库是空的，可以生产
                Object obj = new Object();
                list.add(obj);
                System.out.println(Thread.currentThread().getName() + " ---> " + obj);
                // 唤醒消费者进行消费
                list.notify();
            }
        }
    }
}
```
```java
// 消费线程
class Consumer implements Runnable{
    private List list;

    public Consumer(List list) {
        this.list = list;
    }

    @Override
    public void run() {
        while (true){
            synchronized (list){  // 给 list 加锁
                if(list.size() == 0){  // 等于0,说明仓库中没有元素了。
                    try {
                        list.wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
                // 程序能执行到这里，说明仓库是空的，可以生产
                Object obj = list.remove(0);
                System.out.println(Thread.currentThread().getName() + " ---> " + obj);
                // 唤醒生产者生产
                list.notify();
            }
        }

    }
}
```
## <font class="text-color-13" color="#ffeb3b">volatile</font>
* 在Java中，`volatile`是一个关键字，用于标记变量，以指示该变量在多线程环境中可能被多个线程同时访问。它具有以下两个主要的特性：

	1. 可见性（Visibility）：一个被volatile修饰的变量的值发生变化后，会立即被其他线程所看到，因为JVM会将该变量的最新值刷新到主内存中，使得其他线程读取的是最新值，而不是本地线程的缓存值。
  
	2. 禁止指令重排序（Ordering）：volatile修饰的变量，其操作不会被JVM进行重排序，也就是说，volatile修饰的操作的执行顺序是固定的，不会被JVM进行优化或重排。
  

* 需要注意的是，volatile仅保证了可见性和指令顺序，但并不能保证原子性，也就是说，它无法保证在并发情况下对于同一个volatile变量的读写操作是互斥的。如果需要保证原子性，需要使用synchronized关键字或者Lock等同步工具。

* 另外，使用volatile会对性能产生一定的影响，因为它会强制将变量从主内存中读取，而不是从线程的本地缓存中读取，这可能会导致额外的开销。因此，在需要保证可见性和指令顺序的情况下才使用volatile，避免过度使用。

```java
public class VolatileExample {
    private static volatile boolean flag = false;

    public static void main(String[] args) throws InterruptedException {
        new Thread(() -> {
            while (!flag) {
                System.out.println("Thread A is running...");
            }
            System.out.println("Thread A is done.");
        }).start();

        Thread.sleep(1000); // wait for 1 second

        flag = true;

        System.out.println("Main thread is done.");
    }
}
```
* 在这个例子中，有两个线程，一个是主线程，另一个是线程A。共享变量`flag`被声明为`volatile`。线程A一直在循环中检查`flag`的值，直到它变为`true`，然后线程A才停止。在主线程中，等待1秒钟后将`flag`的值设置为`true`。这样，当线程A检查`flag`的值时，它能够读取到最新的值，因为`flag`被声明为`volatile`，它的值会立即更新到主内存中，线程A可以读取到主内存中的最新值。

## <font class="text-color-13" color="#ffeb3b">Lock 接口</font>
* <a href="https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/util/concurrent/locks/Lock.html">Lock 接口API文档</a>

* Java Lock 接口是一种比 synchronized 块更高级的线程同步机制，它提供了更多的功能和更灵活的控制方式。Lock 接口提供了两种常用的实现，即 ReentrantLock 和 ReentrantReadWriteLock。与 synchronized 块相比，Lock 接口提供的功能有以下几点：

	1. 可中断性：可以在等待锁的过程中中断该线程的执行。
	2. 公平锁：可以设置公平锁，即等待时间最长的线程最先获取锁。
	3. 非阻塞的获取锁：尝试获取锁时如果锁已经被占用，则不会一直等待锁被释放，而是返回一个失败信息。
	4. 条件锁：可以创建与锁绑定的条件变量，以便线程之间更加精细地协调。

Lock 接口的基本用法如下：
```java
Lock lock = new ReentrantLock(); // 创建一个 Lock 实例
lock.lock(); // 获取锁
try {
    // 执行线程安全的操作
} finally {
    lock.unlock(); // 释放锁
}
```
* 需要注意的是，在使用 Lock 接口时，必须手动释放锁，否则会导致其他线程无法获取该锁。通常使用 try-finally 代码块来确保在任何情况下都能够正确地释放锁。

* Lock接口中常用的方法包括：

| 方法名 | 描述 |
|--------|------|
| void lock() | 获取锁，如果锁已经被占用，则当前线程将被阻塞，直到获得锁为止。|
| void unlock() | 释放锁。|
| boolean tryLock() | 尝试获取锁，如果锁未被占用，则获取锁并返回true，否则返回false。|
| boolean tryLock(long timeout, TimeUnit unit) | 在指定时间内尝试获取锁，如果锁未被占用，则获取锁并返回true，否则等待指定时间，如果在等待时间内未能获得锁，则返回false。|
| Condition newCondition() | 创建一个与该锁相关的条件变量。|

* tryLock() 方法例子
```java
Lock lock = new ReentrantLock();
if (lock.tryLock()) {
    try {
        // 获得了锁
    } finally {
        lock.unlock();
    }
} else {
    // 未获得锁
}
```
* 在这个示例中，首先通过tryLock()方法尝试获取锁。如果获取成功，则执行锁保护的代码段；如果获取失败，则跳过锁保护的代码段。

* 需要注意的是，在使用tryLock()方法时，需要手动释放锁。在上面的示例中，使用了finally语句块来确保锁的释放。

## <font class="text-color-121" color="#ffeb3b">Condition 接口</font>
* <a href="https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/util/concurrent/locks/Condition.html">Condition 接口API文档</a>

* Condition接口是Java中与Lock接口一同提供的一种条件队列机制。它提供了一个等待通知的方法await()，以及一个发出通知的方法signal()，signalAll()。

* Condition接口的作用是对锁进行更精细的控制。在使用synchronized关键字时，我们只能通过wait()和notify()等方法进行线程的等待和唤醒操作。而使用Lock接口和Condition接口，我们可以针对不同的情况，分别创建不同的Condition对象，从而实现更细粒度的线程控制。

* Condition接口中最重要的方法是await()和signal()方法。其中await()方法会释放当前线程占有的锁，并将当前线程挂起，等待被唤醒。而signal()方法则是唤醒一个处于等待状态的线程，使其继续执行。

* 另外，Condition接口还有一个signalAll()方法，该方法可以唤醒所有处于等待状态的线程，使它们都能够继续执行。

* 在使用Condition接口时，需要先通过Lock接口的newCondition()方法来创建一个Condition对象，然后再调用该对象的await()、signal()等方法来实现线程的等待和唤醒操作。

* 需要注意的是，Condition接口与Object类的wait()和notify()方法的功能是类似的，但是Condition接口提供了更多的灵活性和功能。在使用Condition接口时，需要注意一些线程安全问题，比如线程死锁、线程饥饿等问题。

* 常用方法：

| 方法名称 | 功能描述 |
| --- | --- |
| await() | 当前线程进入等待状态，直到其他线程调用 signal() 或 signalAll() 方法唤醒该线程。 |
| awaitUninterruptibly() | 与 await() 方法类似，不同之处在于该方法不会响应中断，即使当前线程被中断，也会一直等待，直到其他线程调用 signal() 或 signalAll() 方法唤醒该线程。 |
| signal() | 唤醒一个正在等待的线程，使其从 await() 方法返回，但不会释放锁。如果有多个线程在等待，那么具体唤醒哪个线程是不确定的，取决于 JVM 实现。 |
| signalAll() | 唤醒所有正在等待的线程，使其从 await() 方法返回，但不会释放锁。所有线程都被唤醒后，JVM 会在某个时刻选择一个线程获取锁并继续执行，其他线程将继续等待。 |
| awaitNanos(long nanosTimeout) | 当前线程进入等待状态，等待一定的时间（以纳秒为单位），或者其他线程调用 signal() 或 signalAll() 方法唤醒该线程。 |
| awaitUntil(Date deadline) | 当前线程进入等待状态，等待指定时间点，或者其他线程调用 signal() 或 signalAll() 方法唤醒该线程。 |


* Condition实现生产者消费者模型的例子
```java
public class ProducerConsumer {

    private static final int CAPACITY = 5;
    private final Queue<Integer> queue = new LinkedList<>();

    private final Random random = new Random();

    private final Lock lock = new ReentrantLock();
    private final Condition notFull = lock.newCondition();
    private final Condition notEmpty = lock.newCondition();

    public static void main(String args[]) {
        ProducerConsumer producerConsumer = new ProducerConsumer();
        Thread producerThread = new Thread(() -> {
            try {
                producerConsumer.produce();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }, "ProducerThread");

        Thread consumerThread = new Thread(() -> {
            try {
                producerConsumer.consume();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }, "ConsumerThread");

        producerThread.start();
        consumerThread.start();
    }

    public void produce() throws InterruptedException {  //生产方法 
 
        while (true) {
            lock.lock();
            try {
                while (queue.size() == CAPACITY) {
                    System.out.println(Thread.currentThread().getName() + " : Queue is full, waiting");
                    notFull.await();
                }
                int number = random.nextInt();
                boolean isAdded = queue.offer(number);
                if (isAdded) {
                    System.out.printf("%s added %d into the queue %n", Thread.currentThread().getName(), number);

                    System.out.println(Thread.currentThread().getName() + " : Signalling that queue is no more empty now");
                    notEmpty.signalAll();
                }
            } finally {
                lock.unlock();
            }
        }
    }

    public void consume() throws InterruptedException {  //消费方法
        while (true) {
            lock.lock();
            try {
                while (queue.isEmpty()) {
                    System.out.println(Thread.currentThread().getName() + " : Queue is empty, waiting");
                    notEmpty.await();
                }
                Integer value = queue.poll();
                if (value != null) {
                    System.out.printf("%s consumed %d from the queue %n", Thread.currentThread().getName(), value);

                    System.out.println(Thread.currentThread().getName() + " : Signalling that queue may is not full now");
                    notFull.signalAll();
                }
            } finally {
                lock.unlock();
            }
        }
    }
}
```
* 这个例子中，使用Condition接口实现了一个简单的生产者消费者模型。Lock接口和Condition接口的组合实现了更细粒度的线程控制。其中，`notFull`和`notEmpty`都是Condition对象，分别用于表示队列不满和队列不空的状态。在生产者线程中，当队列已满时，生产者线程将被挂起，直到队列不满为止。在消费者线程中，当队列为空时，消费者线程将被挂起，直到队列不空为止。这样可以保证生产者和消费者线程的同步。

## <font class="text-color-13" color="#ffeb3b">原子类</font>
* <a href="https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/util/concurrent/atomic/package-summary.html">atomic API文档</a>

* Java提供了多个原子类，这些类都位于`java.util.concurrent.atomic`包中。下面是常用的原子类及其作用：

| 类型                            | 描述                                     |
| ------------------------------- | ---------------------------------------- |
| `AtomicBoolean`                 | 原子更新布尔类型的值。                   |
| `AtomicInteger`                 | 原子更新整型的值。                       |
| `AtomicLong`                    | 原子更新长整型的值。                     |
| `AtomicReference`               | 原子更新引用类型的值。                   |
| `AtomicStampedReference`        | 原子更新带有版本号的引用类型，解决ABA问题。 |
| `AtomicMarkableReference`       | 原子更新带有标记位的引用类型。           |
| `AtomicIntegerFieldUpdater`     | 原子更新整型字段的值。                   |
| `AtomicLongFieldUpdater`        | 原子更新长整型字段的值。                 |
| `AtomicReferenceFieldUpdater`   | 原子更新引用类型字段的值。               |
| `AtomicIntegerArray`            | 用于在多线程环境中原子更新`int`数组中的元素。 |
| `AtomicLongArray`               | 用于在多线程环境中原子更新`long`数组中的元素。 |
| `AtomicReferenceArray`          | 用于在多线程环境中原子更新引用类型数组中的元素。 |


* 这些原子类提供了线程安全的操作，可以避免多个线程同时访问同一个变量导致的数据竞争问题。它们通常比使用`synchronized`关键字进行同步的方式更加高效，因为它们利用了硬件提供的原子操作指令，而`synchronized`则需要进入和退出管程。

### <font class="text-color-15" color="#ff9800">AtomicInteger</font>
* <a href="https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/util/concurrent/atomic/AtomicInteger.html">AtomicInteger 类API文档</a>

* `AtomicInteger` 是 Java 中的原子类之一，用于实现原子性操作的整型变量。

* 相对于传统的 `int` 类型，在多线程环境下，`AtomicInteger` 可以保证自增、自减、累加等操作的原子性，避免了多线程并发操作时出现的数据不一致的问题。

* `AtomicInteger` 提供了如下常用方法：

| 方法                            | 描述                                                                                                           |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `get()`                          | 获取当前值                                                                                                     |
| `getAndIncrement()`              | 先获取当前值，再将值加 1，返回加 1 前的值                                                                    |
| `incrementAndGet()`              | 将值加 1，再获取当前值，返回加 1 后的值                                                                       |
| `getAndDecrement()`              | 先获取当前值，再将值减 1，返回减 1 前的值                                                                    |
| `decrementAndGet()`              | 将值减 1，再获取当前值，返回减 1 后的值                                                                       |
| `getAndSet(int newValue)`        | 将当前值设为新值，并返回旧值                                                                                 |
| `compareAndSet(int expect, int update)` | 若当前值等于期望值，则将当前值设置为新值，返回 true；否则不修改当前值，返回 false。 |

* 需要注意的是，`AtomicInteger` 只能保证单个操作的原子性，不能保证多个操作的原子性，例如以下代码就不能保证原子性：
```java
if (atomicInteger.get() < 10) {
    atomicInteger.incrementAndGet();
}
// 因为在获取当前值和增加操作之间，可能有其他线程对 `atomicInteger` 进行了修改。
```
* 在使用 `AtomicInteger` 时，应该注意使用场景，只有对于单个变量的修改操作才适合使用，对于多个变量的复合操作需要使用锁或者其他并发控制方式来实现。

## <font class="text-color-13" color="#ffeb3b">Collections 接口</font>
* Collections接口提供了以下synchronized包装方法：

| 方法名称                                   | 描述                                       |
| ---------------------------------------- | ---------------------------------------- |
| `synchronizedCollection(Collection<T> c)` | 返回一个同步（线程安全）的 Collection。                           |
| `synchronizedList(List<T> list)`          | 返回一个同步（线程安全）的 List。                           |
| `synchronizedMap(Map<K,V> m)`             | 返回一个同步（线程安全）的 Map。                           |
| `synchronizedSet(Set<T> s)`              | 返回一个同步（线程安全）的 Set。                           |
| `synchronizedSortedMap(SortedMap<K,V> m)` | 返回一个同步（线程安全）的 SortedMap。                         |
| `synchronizedSortedSet(SortedSet<T> s)`  | 返回一个同步（线程安全）的 SortedSet。                         |

* 这些方法返回的集合都是线程安全的，可以在多线程环境下使用。它们是通过在方法内部添加同步块来实现同步的，因此它们的性能可能会受到一定的影响，因此在高并发场景下，建议使用`ConcurrentHashMap`等并发集合类。
---
### <font class="text-color-15" color="#ff9800">synchronizedList()</font>
* `Collections.synchronizedList` 是一个静态方法，用于创建一个线程安全的 List。它接收一个 List 对象作为参数，并返回一个线程安全的 List 对象。

* 使用 `Collections.synchronizedList` 可以将非线程安全的 List 转换为线程安全的 List。该方法使用了装饰者模式，将非线程安全的 List 对象包装成一个线程安全的对象。

* 使用该方法创建的线程安全的 List 在进行读写操作时，会使用 synchronized 关键字进行同步，从而保证线程安全性。

* 示例代码如下：
```java
List<String> list = new ArrayList<>();
List<String> synchronizedList = Collections.synchronizedList(list);
```

* 注：对于已经使用 `Collections.synchronizedList()` 方法创建的同步的List对象，可以使用其提供的同步方法来保证线程安全，但是对于复合操作，需要额外的同步措施。

	- 假设现在有一个使用 `synchronizedList` 封装的集合，我们需要对它进行遍历操作并且在遍历的同时修改集合中的元素。由于遍历和修改是两个操作，如果不进行额外的同步措施，就会产生并发修改异常。

```java
List<String> list = Collections.synchronizedList(new ArrayList<>());
list.add("apple");
list.add("banana");
list.add("orange");

synchronized (list) {
    Iterator<String> iterator = list.iterator();
    while (iterator.hasNext()) {
        String fruit = iterator.next();
        if (fruit.equals("banana")) {
            list.remove(fruit);
        }
    }
}
```
* 在这个例子中，我们尝试在遍历列表时删除一个元素。由于 `synchronizedList` 只对单个方法进行同步，因此我们需要使用 `synchronized` 块来同步整个遍历和修改操作，以避免并发修改异常。

* 但是，使用 `synchronized` 块进行同步会影响并发性能。因此，对于这种需要同时遍历和修改的操作，更好的解决方案是使用并发集合类，如 `ConcurrentHashMap` 或 `CopyOnWriteArrayList`。这些并发集合类使用了更高效的同步机制，可以支持更高的并发性能。

## <font class="text-color-121" color="#ffeb3b">并发集合</font>
* Java 提供了一些并发集合类，主要包括以下几种：

| 名称 | 描述 |
| --- | --- |
| ConcurrentHashMap | 一个线程安全的哈希表，它允许并发地读取和写入键值对，而不需要像 Hashtable 或者 Collections.synchronizedMap() 那样对整个 Map 进行加锁。ConcurrentHashMap 采用了分段锁的机制，不同的线程可以同时访问不同的段，从而提高了并发性能。 |
| ConcurrentLinkedQueue | 一个线程安全的队列，它可以支持并发地读取和写入元素，不需要像同步的队列那样对整个队列进行加锁。ConcurrentLinkedQueue 采用了无锁的算法，因此在高并发场景下性能很高。 |
| CopyOnWriteArrayList | 一个线程安全的列表，它通过在写入操作时复制整个列表来实现线程安全。这样，在写入操作期间，其他线程可以继续读取列表中的元素，而不会被阻塞。因为写操作会导致列表的复制，所以 CopyOnWriteArrayList 的写操作性能比较低，但是读操作性能很高。 |
| ArrayBlockingQueue | 一个基于数组实现的有界阻塞队列，它可以在队列满时阻塞生产者线程，在队列空时阻塞消费者线程，从而实现线程间的数据交换。ArrayBlockingQueue 可以保证在高并发情况下的数据安全，因此它被广泛应用于生产者消费者模型中。 |
| LinkedBlockingQueue | 一个基于链表实现的阻塞队列，它的特点与 ArrayBlockingQueue 类似，不同的是 LinkedBlockingQueue 没有固定的容量限制，因此它可以在需要时动态地增加队列的容量。LinkedBlockingQueue 的阻塞操作采用的是锁机制，因此在高并发情况下，性能不如无锁的队列。 |
| ConcurrentSkipListMap | 一个线程安全的有序映射表，它采用了跳表（SkipList）的数据结构，可以实现并发读写操作，而不需要像 TreeMap 或者 Collections.synchronizedSortedMap() 那样对整个 Map 进行加锁。ConcurrentSkipListMap 的写操作采用了分段锁的机制，因此可以实现高并发的写操作。 |

* 除了以上几种并发集合类，Java 还提供了许多其他的并发集合类，如 ConcurrentLinkedDeque、LinkedTransferQueue、ConcurrentHashMap.KeySetView 等等。这些集合类可以根据具体的业务场景选择使用。

### <font class="text-color-15" color="#ff9800">CopyOnWriteArrayList</font>
* CopyOnWriteArrayList是Java并发包提供的一个线程安全的List集合实现类，它基于“写时复制”的思想来实现高效且线程安全的并发访问，它保证了在迭代集合的过程中，不会抛出ConcurrentModificationException异常。

* CopyOnWriteArrayList在每次添加、修改、删除元素时，都会创建一个新的底层数组，并将原数组的元素复制到新数组中，然后再将新元素加入到新数组中，最后再将原数组指向新数组。这样就能保证在遍历集合时，不会出现修改操作导致的并发问题。

* CopyOnWriteArrayList的特点包括：

	1. 线程安全：在多线程环境下，CopyOnWriteArrayList能够提供一定的线程安全性保障。

	2. 读操作不加锁：读操作可以不加锁，因为CopyOnWriteArrayList在写入操作时，会使用synchronized关键字进行同步，保证只有一个线程进行写入操作。

	3. 写操作高效：由于读操作不加锁，所以不会阻塞读操作，写操作的开销是在写入操作时进行的，因此写操作相对高效。

	4. 迭代器弱一致性：迭代器遍历时，只能保证元素的弱一致性，不能保证在遍历时，其它线程没有修改过集合中的元素。
  
* 需要注意的是，CopyOnWriteArrayList适用于读操作远远多于写操作的场景，如果写操作比较频繁，建议使用其他线程安全的List实现类，例如ConcurrentLinkedDeque等。

* 例子
```java
import java.util.concurrent.CopyOnWriteArrayList;

public class CopyOnWriteArrayListExample {

    public static void main(String[] args) throws InterruptedException {
        // 创建一个CopyOnWriteArrayList
        CopyOnWriteArrayList<String> list = new CopyOnWriteArrayList<>();

        // 添加元素
        list.add("apple");
        list.add("banana");
        list.add("orange");

        // 创建一个线程用于遍历集合
        Thread thread1 = new Thread(() -> {
            for (String item : list) {
                System.out.println(item);
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        });

        // 创建一个线程用于修改集合
        Thread thread2 = new Thread(() -> {
            list.add("grape");
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            list.remove(0);
        });

        // 启动两个线程
        thread1.start();
        thread2.start();

        // 等待两个线程执行完毕
        thread1.join();
        thread2.join();
    }
}
```
* 在上面的例子中，我们创建了一个CopyOnWriteArrayList，并向其中添加了三个元素。然后，我们创建了两个线程。一个线程用于遍历集合，另一个线程用于修改集合。在遍历的同时修改集合，不会抛出ConcurrentModificationException异常。

* 我们使用Thread.sleep()方法来模拟遍历和修改操作的时间，这样我们可以看到遍历线程在等待修改线程完成之前，只会看到原始集合中的元素，而不会看到修改后的元素。当修改线程完成时，遍历线程才会看到修改后的元素。


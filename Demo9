package TreadDemo;

import java.util.concurrent.*;

/**
 * Created with IntelliJ IDEA.
 * Description:
 * User: czt20
 * Date: 2026 -08-31
 * Time: 20:48
 */
public class Demo9 {
    public static void main(String[] args) {
        //线程写法一(匿名内部类):
        Thread t1 = new Thread(){
            @Override
            public void run() {
               System.out.println("111");
            }
        };
        //线程写法一(子类继承):
        Thread t2 = new MyTread();
        //线程写法二Runnable接口(匿名内部类):
        Thread t3 = new Thread(new Runnable() {
            @Override
            public void run() {
              System.out.println("333");
            }
        });
        //线程写法二Runnable接口(子类继承):
        Runnable r1 = new MyRunnable();
        Thread t4 = new Thread(r1);
        //线程写法三Callable:
        Callable<Integer> callable = new Callable() {
            @Override
            public Integer call() throws Exception {
                return 5;
            }
        };
        FutureTask<Integer> task = new FutureTask<>(callable);
        Thread t5 = new Thread(task);
        //线程写法四(Lambda表达式):
        Thread t6 = new Thread(()->{
            System.out.println("666");
        });
        //线程写法五(线程工厂+线程池):
        ThreadFactory factory = new ThreadFactory() {
            private int count = 1;
            @Override
            public Thread newThread(Runnable r) {
                Thread t = new Thread(r,"线程"+count);
                count++;
                return t;
            }
        };
        ThreadPoolExecutor pool = new ThreadPoolExecutor(4,10,10, TimeUnit.SECONDS,new ArrayBlockingQueue<Runnable>(10),factory,
                new ThreadPoolExecutor.AbortPolicy());
        for (int i = 0; i < 10; i++) {
            pool.execute(()->{
                System.out.println(Thread.currentThread().getName()+"正在执行的线程");
            });
        }
        pool.shutdown();
    }
    class MyThread extends Thread{
        @Override
        public void run() {
            System.out.println("222");
        }
    }
    class  MYRunnable implements Runnable{
        @Override
        public void run() {
            System.out.println("444");
        }
    }
}

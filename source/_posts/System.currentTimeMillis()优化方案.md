---
title: System.currentTimeMillis()优化方案
date: 2020-04-26 10:37:08
comments: false
---
## System.currentTimeMillis()优化方案
<!--more-->

> System.currentTimeMillis()在java中是最常用的获取系统时间的方法，它返回的是1970年1月1日0点到现在经过的毫秒数。

针对System.currentTimeMillis()性能不好的原因分析，有一篇很好的文章The slow currentTimeMillis()，它直接从系统级、源码、汇编语言各个层次全方位的分析。

从The slow currentTimeMillis()中我们了解到，执行速度缓慢currentTimeMillis()是由两个因素造成的：
- JVM使用gettimeofday() 而不是clock_gettime()
- gettimeofday() 如果使用HPET时间源，则速度非常慢

```java
import java.util.concurrent.Executors;
import java.util.concurrent.ScheduledExecutorService;
import java.util.concurrent.ThreadFactory;
import java.util.concurrent.TimeUnit;
import java.util.concurrent.atomic.AtomicLong;

/**
 * 替换System.currentTimeMillis
 */
public class SystemTimeMilli {

    private final int period;

    private final AtomicLong now;

    private static class InstanceHolder {
        private static final SystemTimeMilli INSTANCE = new SystemTimeMilli(1);
    }

    private SystemTimeMilli(int period) {
        this.period = period;
        this.now = new AtomicLong(System.currentTimeMillis());
        scheduleClockUpdating();
    }

    private static SystemTimeMilli instance() {
        return InstanceHolder.INSTANCE;
    }

    private void scheduleClockUpdating() {
        ScheduledExecutorService scheduler = Executors.newSingleThreadScheduledExecutor(new ThreadFactory() {
            @Override
            public Thread newThread(Runnable runnable) {
                Thread thread = new Thread(runnable, "System-Time-Milli");
                thread.setDaemon(true);
                return thread;
            }
        });
        scheduler.scheduleAtFixedRate(() -> now.set(System.currentTimeMillis()), period, period, TimeUnit.MILLISECONDS);
    }

    private long currentTimeMillis() {
        return now.get();
    }

   
    public static long now() {
        return instance().currentTimeMillis();
    }
}
```


---
[参考地址](https://www.jianshu.com/p/3fbe607600a5)

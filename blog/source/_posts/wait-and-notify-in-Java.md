title: wait() and notify() in Java
date: 2018-07-03 10:30:00
categories:
- [Java, Concurrency]
tags:
- Java
- Concurrency
---

Remember in article synch/Asynch Callback in Java I wrote, multithreading in Java is important and can improve performance. We can use callbacks to notify some threads finish executing. What if we don’t need to pass arguments, but we still want to implements multithreads falixable? Another simple way to let a thread wait and wake up is to use __Object.wait()__ and __Object.notify()__.

Keep in mind that:

- __Object.wait()__ means suspend a thread.
- __Object.notify()__ means wake a thread up.

<!-- more -->

### Logic

To use __wait()__ and __notify()__, we need to create an object to control execuations. This is similary to a lock. We use the common object to lock execuation steps.

Here is the sample code that keep waiting if the condition is not satisfied:

```java
synchronized (object) {
    while (!condition) {
        object.wait();
    }
    // do something:
    // those things will wait 
    // until other place calls notify
}
```

Use the following code in other places to notify the above wait code:

```java
synchronized (object) {
    object.notify();
}
```

Keep in mind, there are two places need to be paid attention:

1. use __synchronized()__ to keep __wait()__ and __notify()__ under the same thread.
2. use while loop instead of if loop to keep waiting and traking notifying.

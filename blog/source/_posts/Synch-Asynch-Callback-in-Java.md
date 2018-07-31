---
title: Synch/Asynch Callback in Java
date: 2018-07-03 08:53:08
---

###Callback Function

Image a senario, you have several threads executed at the same time, how can you know some threads are already finished? Maybe you want to execuate a thread after another thread, then how can you control the flow? Here, we can use callback functions.

A callback function is a function passed into another function as an argument. The purpose of it is to inform a class Sync/Async if some work in other class is down.

In java, we can implement calbaks by interface. Here is the steps:

1. Define methods in an interface that we want to invoke after callback.
2. Define a class that implements callback methods of the above interface.
3. Define a reference in other classes to register the callback interface.
4. Use the reference to invoke callback method.

###Synch vs. Asynch

Most functions we use is synchronous functions. It means a thread is executed after another thread. Threads are executed in order. It is safe and easy understand, however, it is slow because we don’t need to always wait all threads. Some of them are independent. Therefore, we can use asynchronous functions.

An asynchronous call do not block the program from the code execution. It means we can have several threads working together. Here is an example of asynchrouous method:

```java
new Thread(new Runnable() {
    public void run() {
    // what you want to do in asynch
    }
}).start();
```

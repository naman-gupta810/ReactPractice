# Reactive Programming

Reactive programming is part of reactive systems. Reactive system is responsive system that react 
to changes by being able to scale up and down or recover from failures.

A Reactive system has below traits:
  1. Responsive
  2. Resilient
  3. Scalable
  4. Message driven architecture (Sometimes called as event. But the message has explicit destination,
   while event has listener to react over it)
  
Reactive programming is on the event. We have imperative programming before the reactive. 
Let's understand the difference between imperative programming and reactive programming by example

### Imperative Programming example:<br/>
```java
    int a = 2;
    int b = a*10;
    System.out.println(b);
    a = 3;
    System.out.println(a);
```
In above example with change in value of a, b value not react. It will be 20 and not update when a 
value changes to 3.<br/>
To achieve this reactive affect on value change of a, b value also change, one option is 
Observer pattern.

The problem with observer pattern is that, if producer is producing at high rate that the consumer 
is not able to consume. There is no mechanism to notify producer to emit the event at different rate.

The ability of the consumer to request items at different rate or when it is ready to process 
is called as backpressure.

### Reactive programming

In addition to backpressure the reactive programming  also include below three concept.
1. Non-blocking Programming
2. Asynchronous Programming
3. Functional/Declarative Programming

##### 1. Non-blocking Programming
Blocking is another word for synchronous requests. We use number of block or synchronous calls in 
use like API calls or database calls, where the thread waits for getting data from system or 
database. Till now we have single threaded server in which each thread handle a request.
If there is any blocking operation with request the thread stuck while processing that request
and not able to serve other requests. 

While the reactive servers work in event loop model where small number of threads handling request.
In this model the request handling is divided into the events and handled by these threads which waiting 
time is less. The operation like API call or database call is carried out by some worker threads which generate
new event whenever the operation is completed and these threads can carry out the rest of event handling.

Servlet 3.1 APIs provides the support for non-blocking server.

##### 2. Asynchronous Programming
In async programming we execute task in parallel or background and their result is consumed at later point of
time. This can achieved using callback function or the completable future. But the problem with callbacks is callback
hell where number of operation nested which is not easy to read and maintain. In javascript to provide this two new keyword
comes into picture <b>async</b> and <b>await</b>. When we use they looks like functional but they use the asynchronous 
call. In java we use the Publisher and Subscriber model.

##### 3. Functional/Declarative Programming
In last point we discussed about disadvantage of asyn programming. To address that the reactive libraries provide the
functional programming approach. Which uses the concept of pure functions, lambada expressions and immutability.Which makes code
more maintainable, declarative and testable. Java is not really functional language. But Java uses stream APIs or the reactive
libraries to provide these features.

### Reactive implementation 
There are different implementation we can use for the reactive programming and can use with Spring WebFlux which support are provided.
1. Reactor API
2. RxJava
3. RxJava 2
4. Completable Future
5. Java 9 Flow API

For this we use the Reactor API.

## Reference and FAQ
1. What is difference in Spring MVC and Spring WebFlux?<br/>
They both use almost similar syntax apart from returning type and handling the request processing.

2. What we can achieve by using Spring Webflux instead of Spring MVC?<br/>
We get a much better performance in case of Spring WebFlux(Event base processing) as compare to Spring MVC(1 request/thread model).<br/>
Ref : a. https://dzone.com/articles/raw-performance-numbers-spring-boot-2-webflux-vs-s<br/>
      b. https://medium.com/@the.raj.saxena/springboot-2-performance-servlet-stack-vs-webflux-reactive-stack-528ad5e9dadc









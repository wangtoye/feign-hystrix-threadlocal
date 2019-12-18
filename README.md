## 简介
此jar包的目的是为了解决FeignClient开启Hystrix的线程隔离支持下，主线程的本地线程变量无法在子线程获取问题。

## 使用方式
1.引用jar包依赖  
&lt;dependency&gt;  
    &lt;groupId&gt;com.wangtoye&lt;/groupId&gt;  
    &lt;artifactId&gt;feign-hystrix-threadlocal-spring-boot-starter&lt;/artifactId&gt;  
    &lt;version&gt;0.0.1-SNAPSHOT&lt;/version&gt;  
&lt;/dependency&gt;  
2.实现Callable<T>接口或者继承AbstractCallable<T>类  
作用是实现回调，在子线程中设置需要传入的值。  
3.实现FeignHystrixCallableWrapper类  
作用是实现包装，实例化过程2的实现类，此处可以获取主线程的值，交给过程2的实现类设置值。  
4.使用参考[spring-all/consumer-service](https://github.com/wangtoye/spring-all/tree/master/consumer-service)
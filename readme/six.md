# @author：Karajan


#### 什么是Etag？


当发送一个服务器请求时，浏览器首先会进行缓存过期判断。浏览器根据缓存过期时间判断缓存文件是否过期。<br>

情景一：若没有过期，则不向服务器发送请求，直接使用缓存中的结果，此时我们在浏览器控制台中可以看到  `200 OK`(from cache) ，此时的情况就是完全使用缓存，浏览器和服务器没有任何交互的。


情景二：若已过期，则向服务器发送请求，此时请求中会带上①中设置的文件修改时间，和`Etag`



然后，进行资源更新判断。服务器根据浏览器传过来的文件修改时间，判断自浏览器上一次请求之后，文件是不是没有被修改过；根据`Etag`，判断文件内容自上一次请求之后，有没有发生变化

情形一：若两种判断的结论都是文件没有被修改过，则服务器就不给浏览器发`index.html`的内容了，直接告诉它，文件没有被修改过，你用你那边的缓存吧—— `304 Not Modified`，此时浏览器就会从本地缓存中获取`index.html`的内容。此时的情况叫协议缓存，浏览器和服务器之间有一次请求交互。<br>

情形二：若修改时间和文件内容判断有任意一个没有通过，则服务器会受理此次请求，之后的操作同①

<br>

① 只有get请求会被缓存，post请求不会


#### Expires和Cache-Control



`Expires`要求客户端和服务端的时钟严格同步。`HTTP1.1`引入`Cache-Control`来克服Expires头的限制。如果max-age和Expires同时出现，则max-age有更高的优先级。


```js
    Cache-Control: no-cache, private, max-age=0

    ETag: abcde

    Expires: Thu, 15 Apr 2014 20:00:00 GMT

    Pragma: private

    Last-Modified: $now // RFC1123 format
```


#### ETag应用:


`Etag`由服务器端生成，客户端通过`If-Match`或者说`If-None-Match`这个条件判断请求来验证资源是否修改。常见的是使用`If-None-Match`。请求一个文件的流程可能如下：

====第一次请求===


    1.客户端发起 HTTP GET 请求一个文件；

    2.服务器处理请求，返回文件内容和一堆Header，当然包括Etag(例如"2e681a-6-5d044840")(假设服务器支持Etag生成和已经开启了Etag).状态码200



====第二次请求===



    客户端发起 HTTP GET 请求一个文件，注意这个时候客户端同时发送一个If-None-Match头，这个头的内容就是第一次请求时服务器返回的Etag：2e681a-6-5d0448402.服务器判断发送过来的Etag和计算出来的Etag匹配，因此If-None-Match为False，不返回200，返回304，客户端继续使用本地缓存；流程很简单，问题是，如果服务器又设置了Cache-Control:max-age和Expires呢，怎么办


答案是同时使用，也就是说在完全匹配`If-Modified-Since`和`If-None-Match`即检查完修改时间和`Etag`之后，

服务器才能返回304.(不要陷入到底使用谁的问题怪圈)



为什么使用Etag请求头?

Etag 主要为了解决 `Last-Modified` 无法解决的一些问题。
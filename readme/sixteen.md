# @author：Karajan


#### 谈谈你对重构的理解

网站重构：在不改变外部行为的前提下，简化结构、添加可读性，而在网站前端保持一致的行为。也就是说是在不改变UI的情况下，对网站进行优化，
在扩展的同时保持一致的UI。


    对于传统的网站来说重构通常是：

    表格(table)布局改为DIV+CSS

    使网站前端兼容于现代浏览器(针对于不合规范的CSS、如对IE6有效的)

    对于移动平台的优化

    针对于SEO进行优化

    深层次的网站重构应该考虑的方面


    减少代码间的耦合

    让代码保持弹性

    严格按规范编写代码

    设计可扩展的API

    代替旧有的框架、语言(如VB)

    增强用户体验

    通常来说对于速度的优化也包含在重构中



    压缩JS、CSS、image等前端资源(通常是由服务器来解决)

    程序的性能优化(如数据读写)

    采用CDN来加速资源加载

    对于JS DOM的优化

    HTTP服务器的文件缓存


#### HTTP状态码


```html

    100  Continue  继续，一般在发送post请求时，已发送了http header之后服务端将返回此信息，表示确认，之后发送具体参数信息

    200  OK   正常返回信息

    201  Created  请求成功并且服务器创建了新的资源

    202  Accepted  服务器已接受请求，但尚未处理

    301  Moved Permanently  请求的网页已永久移动到新位置。

    302 Found  临时性重定向。

    303 See Other  临时性重定向，且总是使用 GET 请求新的 URI。

    304  Not Modified  自从上次请求后，请求的网页未修改过。


    400 Bad Request  服务器无法理解请求的格式，客户端不应当尝试再次使用相同的内容发起请求。

    401 Unauthorized  请求未授权。

    403 Forbidden  禁止访问。

    404 Not Found  找不到如何与 URI 相匹配的资源。

    500 Internal Server Error  最常见的服务器端错误。

    503 Service Unavailable 服务器端暂时无法处理请求（可能是过载或维护）。

```


#### 说说你对Promise的理解



依照 `Promise/A+` 的定义，`Promise` 有四种状态：

	pending: 初始状态, 非 fulfilled 或 rejected.

	fulfilled: 成功的操作.

	rejected: 失败的操作.

	settled: Promise已被fulfilled或rejected，且不是pending



另外， `fulfilled` 与 `rejected` 一起合称 `settled`。



`Promise` 对象用来进行延迟(deferred) 和异步(asynchronous ) 计算。



>Promise 的构造函数



构造一个 `Promise`，最基本的用法如下：


```js
	var promise = new Promise(function(resolve, reject) {

	    if (...) {  // succeed

	        resolve(result);

	    } else {   // fails

	        reject(Error(errMessage));

	    }
	});
```


`Promise` 实例拥有 `then` 方法（具有 `then` 方法的对象，通常被称为 `thenable`）。它的使用方法如下：

```js
promise.then(onFulfilled, onRejected)
```

接收两个函数作为参数，一个在 `fulfilled` 的时候被调用，一个在 `rejected` 的时候被调用，接收参数就是 `future，onFulfilled` 对应 `resolve`, `onRejected` 对应 `reject`。

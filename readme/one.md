# @author：Karajan


#### position的值， relative和absolute分别是相对于谁进行定位的？


- `absolute` :生成绝对定位的元素， 相对于最近一级的 定位不是 static 的父元素来进行定位。

- `fixed` （老IE不支持）生成绝对定位的元素，通常相对于浏览器窗口或 frame 进行定位。

- `relative` 生成相对定位的元素，相对于其在普通流中的位置进行定位。

- `static`  默认值。没有定位，元素出现在正常的流中

- `sticky` 生成粘性定位的元素，容器的位置根据正常文档流计算得出

<br>



#### 如何解决跨域问题

>JSONP：

原理是：动态插入`script`标签，通过`script`标签引入一个`js`文件，这个js文件载入成功后会执行我们在url参数中指定的函数，并且会把我们需要的`json`数据作为参数传入。



由于同源策略的限制，`XmlHttpRequest`只允许请求当前源（域名、协议、端口）的资源，为了实现跨域请求，可以通过`script`标签实现跨域请求，然后在服务端输出JSON数据并执行回调函数，从而解决了跨域的数据请求。



优点是兼容性好，简单易用，支持浏览器与服务器双向通信。缺点是只支持GET请求。

`JSONP`：`json+padding`（内填充），顾名思义，就是把JSON填充到一个盒子里

```js
<script>
    function createJs(sUrl){

        var oScript = document.createElement('script');
        oScript.type = 'text/javascript';
        oScript.src = sUrl;
        document.getElementsByTagName('head')[0].appendChild(oScript);
    }

    createJs('jsonp.js');

    box({
       'name': 'test'
    });

    function box(json){
        alert(json.name);
    }
</script>
```


>CORS

服务器端对于`CORS`的支持，主要就是通过设置`Access-Control-Allow-Origin`来进行的。如果浏览器检测到相应的设置，就可以允许`Ajax`进行跨域的访问。



>通过修改document.domain来跨子域

将子域和主域的`document.domain`设为同一个主域.前提条件：这两个域名必须属于同一个基础域名!而且所用的协议，端口都要一致，否则无法利用`document.domain`进行跨域



主域相同的使用`document.domain`

>使用window.name来进行跨域



`window`对象有个`name`属性，该属性有个特征：即在一个窗口(window)的生命周期内,窗口载入的所有的页面都是共享一个`window.name`的，每个页面对`window.name`都有读写的权限，`window.name`是持久存在一个窗口载入过的所有页面中的




>使用HTML5中新引进的`window.postMessage`方法来跨域传送数据



还有flash、在服务器上设置代理页面等跨域方式。个人认为`window.name`的方法既不复杂，也能兼容到几乎所有浏览器，这真是极好的一种跨域方法。





#### `XML`和`JSON`的区别？

```html
(1).数据体积方面。

JSON相对于XML来讲，数据的体积小，传递的速度更快些。

(2).数据交互方面。

JSON与JavaScript的交互更加方便，更容易解析处理，更好的数据交互。

(3).数据描述方面。

JSON对数据的描述性比XML较差。

(4).传输速度方面。

JSON的速度要远远快于XML。
```
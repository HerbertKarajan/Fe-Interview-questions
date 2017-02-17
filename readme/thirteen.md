# @author：Karajan



#### DOM操作——怎样添加、移除、移动、复制、创建和查找节点。


>1）创建新节点

          createDocumentFragment()    //创建一个DOM片段

          createElement()   //创建一个具体的元素

          createTextNode()   //创建一个文本节点


>2）添加、移除、替换、插入

          appendChild()

          removeChild()

          replaceChild()

          insertBefore() //并没有insertAfter()



>3）查找



          getElementsByTagName()    //通过标签名称

          getElementsByName()    //通过元素的Name属性的值(IE容错能力较强，
          会得到一个数组，其中包括id等于name值的)

          getElementById()    //通过元素Id，唯一性



#### html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和 HTML5？



      HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。

      拖拽释放(Drag and drop) API

      语义化更好的内容标签（header,nav,footer,aside,article,section）

      音频、视频API(audio,video)

      画布(Canvas) API

      地理(Geolocation) API

      本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；

      sessionStorage 的数据在浏览器关闭后自动删除


      表单控件，calendar、date、time、email、url、search

      新的技术webworker, websocket, Geolocation




>移除的元素


    纯表现的元素：basefont，big，center，font, s，strike，tt，u；

    对可用性产生负面影响的元素：frame，frameset，noframes；


>支持HTML5新标签：


```

    IE8/IE7/IE6支持通过document.createElement方法产生的标签，

    可以利用这一特性让这些浏览器支持HTML5新标签，

    当然最好的方式是直接使用成熟的框架、使用最多的是html5shim框架

       <!--[if lt IE 9]>

       <script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>

       <![endif]-->

    如何区分： DOCTYPE声明\新增的结构元素\功能元素
```




#### 如何实现浏览器内多个标签页之间的通信?


```js
    调用localstorge、cookies等本地存储方式
```

#### 什么是 FOUC（无样式内容闪烁）？你如何来避免 FOUC？


```html
     FOUC - Flash Of Unstyled Content 文档样式闪烁

     <style type="text/css" media="all">@import "../fouc.css";</style>

    而引用CSS文件的@import就是造成这个问题的罪魁祸首。IE会先加载整个HTML文档的DOM，然后再去导入外部的CSS文件，因此，在页面DOM加载完成到CSS导入完成中间会有一段时间页面上的内容是没有样式的，这段时间的长短跟网速，电脑速度都有关系。

     解决方法简单的出奇，只要在<head>之间加入一个<link>或者<script>元素就可以了。
```


#### null和undefined的区别？


`null`是一个表示"无"的对象，转为数值时为0；`undefined`是一个表示"无"的原始值，转为数值时为`NaN`。


当声明的变量还未被初始化时，变量的默认值为`undefined`。

`null`用来表示尚未存在的对象，常用来表示函数企图返回一个不存在的对象。


`undefined`表示"缺少值"，就是此处应该有一个值，但是还没有定义。典型用法是：



    （1）变量被声明了，但没有赋值时，就等于undefined。


    （2) 调用函数时，应该提供的参数没有提供，该参数等于undefined。


    （3）对象没有赋值的属性，该属性的值为undefined。


    （4）函数没有返回值时，默认返回undefined。



`null`表示"没有对象"，即该处不应该有值。典型用法是：


    （1） 作为函数的参数，表示该函数的参数不是对象。

    （2） 作为对象原型链的终点。



#### new操作符具体干了什么呢?


       1、创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。

       2、属性和方法被加入到 this 引用的对象中。

       3、新创建的对象由 this 所引用，并且最后隐式的返回 this 。



    var obj  = {};

    obj.__proto__ = Base.prototype;

    Base.call(obj);

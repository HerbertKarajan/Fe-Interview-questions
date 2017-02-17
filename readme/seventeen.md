# @author：Karajan


#### 说说你对前端架构师的理解


负责前端团队的管理及与其他团队的协调工作，提升团队成员能力和整体效率；
带领团队完成研发工具及平台前端部分的设计、研发和维护；
带领团队进行前端领域前沿技术研究及新技术调研，保证团队的技术领先
负责前端开发规范制定、功能模块化设计、公共组件搭建等工作，并组织培训。



#### 实现一个函数clone，可以对JavaScript中的5种主要的数据类型（包括Number、String、Object、Array、Boolean）进行值复制


```js
    Object.prototype.clone = function(){

            var o = this.constructor === Array ? [] : {};

            for(var e in this){

                    o[e] = typeof this[e] === "object" ? this[e].clone() : this[e];

            }

            return o;
    }
```

#### 说说严格模式的限制



严格模式主要有以下限制：

    变量必须声明后再使用

    函数的参数不能有同名属性，否则报错

    不能使用with语句

    不能对只读属性赋值，否则报错

    不能使用前缀0表示八进制数，否则报错

    不能删除不可删除的属性，否则报错

    不能删除变量delete prop，会报错，只能删除属性delete global[prop]

    eval不会在它的外层作用域引入变量

    eval和arguments不能被重新赋值

    arguments不会自动反映函数参数的变化

    不能使用arguments.callee

    不能使用arguments.caller

    禁止this指向全局对象

    不能使用fn.caller和fn.arguments获取函数调用的堆栈

    增加了保留字（比如protected、static和interface）



设立"严格模式"的目的，主要有以下几个：


- 消除`Javascript`语法的一些不合理、不严谨之处，减少一些怪异行为;

- 消除代码运行的一些不安全之处，保证代码运行的安全；

- 提高编译器效率，增加运行速度；

- 为未来新版本的`Javascript`做好铺垫。



注：经过测试`IE6,7,8,9`均不支持严格模式。




#### 如何删除一个cookie



>1.将时间设为当前时间往前一点。


```js
var date = new Date();

date.setDate(date.getDate() - 1);//真正的删除
```


`setDate() `方法用于设置一个月的某一天。

>2.expires的设置

```js
    document.cookie = 'user='+ encodeURIComponent('name')  + ';expires = ' + new Date(0)
```


#### `<strong>`，`<em>`和`<b>`，`<i>`标签


```html
<strong> 标签和 <em> 标签一样，用于强调文本，但它强调的程度更强一些。

em 是 斜体强调标签，更强烈强调，表示内容的强调点。相当于html元素中的 <i>...</i>;

< b > < i >是视觉要素，分别表示无意义的加粗，无意义的斜体。

em 和 strong 是表达要素(phrase elements)。
```


#### 说说你对AMD和Commonjs的理解



`CommonJS`是服务器端模块的规范，Node.js采用了这个规范。`CommonJS`规范加载模块是同步的，也就是说，只有加载完成，才能执行后面的操作。AMD规范则是非同步加载模块，允许指定回调函数。

`AMD`推荐的风格通过返回一个对象做为模块对象，`CommonJS`的风格通过对`module.exports`或`exports`的属性赋值来达到暴露模块对象的目的。

>详情：[也谈webpack及其开发模式]()

#### document.write()的用法



` document.write()`方法可以用在两个方面：页面载入过程中用实时脚本创建页面内容，以及用延时脚本创建本窗口或新窗口的内容。

`document.write`只能重绘整个页面。`innerHTML`可以重绘页面的一部分


#### 编写一个方法 求一个字符串的字节长度

假设：一个英文字符占用一个字节，一个中文字符占用两个字节

```js
 function GetBytes(str){

        var len = str.length;

        var bytes = len;

        for(var i=0; i<len; i++){

            if (str.charCodeAt(i) > 255) bytes++;

        }

        return bytes;

    }

alert(GetBytes("你好,as"));
```


### git fetch和git pull的区别


```js
git pull：相当于是从远程获取最新版本并merge到本地

git fetch：相当于是从远程获取最新版本到本地，不会自动merge
```


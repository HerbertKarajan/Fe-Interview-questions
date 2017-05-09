# @author：Karajan



#### 如何评价AngularJS和BackboneJS

`backbone`具有依赖性，依赖`underscore.js`。`Backbone + Underscore + jQuery(or Zepto)` 就比一个`AngularJS` 多出了2 次HTTP请求.

<br>

`Backbone`的`Model`没有与UI视图数据绑定，而是需要在View中自行操作DOM来更新或读取UI数据。`AngularJS`与此相反，Model直接与UI视图绑定，`Model`与UI视图的关系，通过`directive`封装，`AngularJS`内置的通用`directive`，就能实现大部分操作了，也就是说，基本不必关心`Model`与UI视图的关系，直接操作Model就行了，UI视图自动更新。

<br>

`AngularJS`的`directive`，你输入特定数据，他就能输出相应UI视图。是一个比较完善的前端MVW框架，包含模板，数据双向绑定，路由，模块化，服务，依赖注入等所有功能，模板功能强大丰富，并且是声明式的，自带了丰富的 Angular 指令。



#### 用过哪些设计模式？



>工厂模式：

    主要好处就是可以消除对象间的耦合，通过使用工程方法而不是new关键字。将所有实例化的代码集中在一个位置防止代码重复。

        工厂模式解决了重复实例化的问题 ，但还有一个问题,那就是识别问题，因为根本无法 搞清楚他们到底是哪个对象的实例。


    function createObject(name,age,profession){//集中实例化的函数var obj = new Object();
        obj.name = name;
        obj.age = age;
        obj.profession = profession;
        obj.move = function () {
            return this.name + ' at ' + this.age + ' engaged in ' + this.profession;
        };
        return obj;
    }
    var test1 = createObject('trigkit4',22,'programmer');//第一个实例var test2 = createObject('mike',25,'engineer');//第二个实例


<br>



>构造函数模式


使用构造函数的方法 ，即解决了重复实例化的问题 ，又解决了对象识别的问题，该模式与工厂模式的不同之处在于：



    1.构造函数方法没有显示的创建对象 (new Object());

    2.直接将属性和方法赋值给 this 对象;

    3.没有 renturn 语句。
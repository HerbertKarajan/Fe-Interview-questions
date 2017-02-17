# @author：Karajan



#### 栈和队列的区别?



    栈的插入和删除操作都是在一端进行的，而队列的操作却是在两端进行的。

    队列先进先出，栈先进后出。

    栈只允许在表尾一端进行插入和删除，而队列只允许在表尾一端进行插入，在表头一端进行删除



#### 栈和堆的区别？

    栈区（stack）—   由编译器自动分配释放   ，存放函数的参数值，局部变量的值等。

    堆区（heap）   —   一般由程序员分配释放，   若程序员不释放，程序结束时可能由OS回收。

    堆（数据结构）：堆可以被看成是一棵树，如：堆排序；

    栈（数据结构）：一种先进后出的数据结构。


#### 快速 排序的思想并实现一个快排？



"快速排序"的思想很简单，整个排序过程只需要三步：

　　（1）在数据集之中，找一个基准点

　　（2）建立两个数组，分别存储左边和右边的数组

　　（3）利用递归进行下次比较


```js
    <script type="text/javascript">

        function quickSort(arr){
            if(arr.length<=1){
                return arr;//如果数组只有一个数，就直接返回；
            }

            var num = Math.floor(arr.length/2);//找到中间数的索引值，如果是浮点数，则向下取整

            var numValue = arr.splice(num,1);//找到中间数的值
            var left = [];
            var right = [];

            for(var i=0;i<arr.length;i++){
                if(arr[i]<numValue){
                    left.push(arr[i]);//基准点的左边的数传到左边数组
                }
                else{
                   right.push(arr[i]);//基准点的右边的数传到右边数组
                }
            }

            return quickSort(left).concat([numValue],quickSort(right));//递归不断重复比较
        }

        alert(quickSort([32,45,37,16,2,87]));//弹出“2,16,32,37,45,87”

    </script>
```


#### 你觉得jQuery或zepto源码有哪些写的好的地方

(答案仅供参考)

`jquery`源码封装在一个匿名函数的自执行环境中，有助于防止变量的全局污染，然后通过传入window对象参数，可以使window对象作为局部变量使用，好处是当`jquery`中访问window对象的时候，就不用将作用域链退回到顶层作用域了，从而可以更快的访问`window`对象。同样，传入`undefined`参数，可以缩短查找undefined时的作用域链。




```js
    (function( window, undefined ) {

         //用一个函数域包起来，就是所谓的沙箱

         //在这里边var定义的变量，属于这个函数域内的局部变量，避免污染全局

         //把当前沙箱需要的外部变量通过函数参数引入进来

         //只要保证参数对内提供的接口的一致性，你还可以随意替换传进来的这个参数

        window.jQuery = window.$ = jQuery;

    })( window );
```


jquery将一些原型属性和方法封装在了`jquery.prototype`中，为了缩短名称，又赋值给了`jquery.fn`，这是很形象的写法。



有一些数组或对象的方法经常能使用到，jQuery将其保存为局部变量以提高访问速度。




`jquery`实现的链式调用可以节约代码，所返回的都是同一个对象，可以提高代码效率。
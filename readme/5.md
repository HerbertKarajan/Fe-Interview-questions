# @author：Karajan


#### 你觉得前端工程的价值体现在哪



    为简化用户使用提供技术支持（交互部分）

    为多个浏览器兼容性提供支持

    为提高用户浏览速度（浏览器性能）提供支持

    为跨平台或者其他基于webkit或其他渲染引擎的应用提供支持

    为展示数据提供支持（数据接口）



#### 谈谈性能优化问题



代码层面：避免使用css表达式，避免使用高级选择器，通配选择器。

缓存利用：缓存Ajax，使用CDN，使用外部js和css文件以便缓存，添加Expires头，服务端配置Etag，减少DNS查找等

请求数量：合并样式和脚本，使用css图片精灵，初始首屏之外的图片资源按需加载，静态资源延迟加载。

请求带宽：压缩文件，开启GZIP，



>代码层面的优化



- 用`hash-table`来优化查找

- 少用全局变量

- 用`innerHTML`代替`DOM`操作，减少`DOM`操作次数，优化`javascript`性能

- 用`setTimeout`来避免页面失去响应

- 缓存DOM节点查找的结果

- 避免使用CSS Expression

- 避免全局查询

- 避免使用with(with会创建自己的作用域，会增加作用域链长度)

- 多个变量声明合并

- 避免图片和iFrame等的空Src。空Src会重新加载当前页面，影响速度和效率
- 尽量避免写在HTML标签中写Style属性

#### 移动端性能优化

- 尽量使用css3动画，开启硬件加速。
- 适当使用`touch`事件代替`click`事件。
- 避免使用`css3`渐变阴影效果。
- 可以用`transform: translateZ(0)`来开启硬件加速。
- 不滥用Float。Float在渲染时计算量比较大，尽量减少使用
- 不滥用Web字体。Web字体需要下载，解析，重绘当前页面，尽量减少使用。
- 合理使用requestAnimationFrame动画代替setTimeout
- CSS中的属性（CSS3 transitions、CSS3 3D transforms、Opacity、Canvas、WebGL、Video）会触发GPU渲染，请合理使用。过渡使用会引发手机过耗电增加
- PC端的在移动端同样适用

>相关阅读：[如何做到一秒渲染一个移动页面](https://github.com/cssmagic/blog/issues/20)
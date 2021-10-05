## a标签的用法

属性

- href ：要跳转的超链接地址
- target：指定在哪个窗口打开超链接



作用

- 跳转外部页面
- 跳转内部锚点

- 跳转到邮箱或电话



### a标签的href取值

- 网址

​      		https://google.com

​     		 http://google.com

​    		 //google.com（浏览器会自动发起请求，最终还是跳转到https://www.google.com/）

- 路径 

​       		/a/b/c 以及a/b/c      

​					（html中的/a/不是指根目录a盘，而是指发起访问网站请求所在文件的目录）

​      		index.html以及./index.html

- 伪协议

​       		1.javascript代码

​						<a href="javascript:;">查看</a> 点击a标签运行写在：和；之间的js代码

​      		 2.mailto:邮箱

​      		 3.tel:手机号

- id

  ​	href=#xxx 点击a标签跳转到指定的锚点所在位置



### a标签的target取值

内置名字：

- _blank  在新的空白页打开超链接窗口
- _self     在当前页面打开超链接窗口

- _top     当页面有多层iframe嵌套引用时，在最外层页面打开超链接窗口
- _parent    当页面有多层iframe嵌套引用时，在超链接所在的iframe层的父层打开超链接

- target="xxx"     

  打开超链接时如果有窗口的id为xxx，就在那个窗口打开网页，如果没有就新建一个空白窗口，并把该窗口id值设为xxx，之后如果再点击target为xxx的链接，就会在之前新建的xxx窗口打开新网页。      

  

## img标签的用法

作用：发出get请求，展示一张图片

属性：

- src
- alt：当图片加载失败时用来代替图片内容的描述性文字

- height
- width

事件：

- onload
- onerror

响应式：

`max-width:100%`  图片根据窗口大小自动调整尺寸，适配手机屏幕很方便



## table标签的用法

相关的标签

- table
- thead

- tbody
- tfoot

- tr
- td

- th



相关的样式

- table-layout

   	  auto：根据表头长度自动调整单元格宽度

  ​       fixed：单元格宽度固定

- border-collapse

  ​	   collapse：边框合并模式

  ​	   separate：边框分离模式

- border-spacing：指定相邻单元格边框之间的距离（只适用于边框分离模式）

  

## 其他感想

老师在讲如何清除table标签很丑的默认样式的时候谈到了自己常用的方法是

```css
border-collapse:collapse;
border-spacing:0;
```

我在查阅mdn border-spacing文档的时候发现文档说border-spacing属性只适用于边框分离模式，也就是border-collapse：separate的时候，如果已经设置了border-collapse：collapse，也就是把表格相邻单元格的两条边框合并，就不需要再把border-spacing设置为0了。

```css
border-collapse:collapse;
```


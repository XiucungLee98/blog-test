### 1.HTML是谁发明的

是李爵士（Berners-Lee）于1990年发明的

### 2.HTML起手应该写什么

 ```html
<!DOCTYPE html> 
<html lang="zh-CN">    
  <head>
    <meta charset="UTF-8" />         
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />  
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body></body>
</html>
 ```

`<!DOCTYPE html>`说明文件的类型是html

`<html lang="zh-CN">`说明页面语言是中国地区的中文

`<meta charset="UTF-8" />` 说明页面为UTF8编码

`<meta content="IE=edge" /> ` 说明要用最新版本的IE浏览

`<meta name="viewport" content="width=device-width, initial-scale=1.0" />` 禁止页面缩放

### 3.常用的表章节的标签

* h1~h6：一到六级标题
* section：表示一个含有主题的独立部分，表示一个章节
* article：表示一篇文章或者一个帖子
* main：表示页面的主题内容，一个页面只能有一个main
* aside：表示与网页主要内容间接相关的部分，非主要的内容
* header：表示页面的头部，通常放导航栏或者搜索栏等
* footer：表示页面的尾部，通常放版权信息等。



### 4.全局属性有哪些

- class  （类选择器）
- contenteditable  （设置元素可编辑，可以与display:block配合，

​       将隐藏的style{ }显示，达到让用户自己编辑样式的效果）

- hidden （隐藏元素）
- id（不到万不得已不要用id属性，因为不能保证元素的唯一性，尽量用class）

- style（HTML的属性style优先级比css高，Javascript中设置的style优先级最高）
- tabindex（控制按tab键时选中元素的顺序，tabindex=0时最后一个访问，tabindex=-1时永不访问）

- title （鼠标悬停显示文字内容）



### 5. 常用的内容标签

* ol+li

  ol：ordered list 有序列表

  标有数字顺序

* ul+li

  ul：unordered list 无序列表

  标有圆点

* dl+dt+dd

  * dl：description list 描述列表

  * dt：description term 描述对象

  * dd：description data 描述的数据

* pre

  保留多个空格，回车或者tab，如果不用pre标签包裹的文字，

  输入再多空格也不会对格式造成影响。

* code

  用来包裹代码（这样写出的代码每个字母是等宽的，便于观看和修改）。

* hr

  分割线

* em

  表示语气上的强调

* strong

  表示内容本身的重要性

* quote

  内联引用

* blockquote

  块级引用

* a
  
  超链接
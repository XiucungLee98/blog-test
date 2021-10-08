# 浏览器渲染原理

## 渲染过程

1. 构建HTML树（DOM）
2. 构建CSS树（CSSOM）

1. 将两棵树合并成一棵渲染树（render tree）
2. Layout布局（文档流、盒模型、计算大小和位置）

1. Paint绘制（边框颜色、文字颜色、阴影）

2. Composite合成（根据层叠关系展示画面）

   

## 三种像素管道更新样式方式

- JS->Style->布局Layout->绘制Paint->合成Composite
- JS->Style->绘制Paint->合成Composite

- JS->Style->合成Composite

要查询不同内核浏览器对CSS属性修改后对layout/paint/Composite属性的影响情况，帮助在编程中判断哪个方法对浏览器渲染性能提升更大，上这个网站查看：

https://csstriggers.com/



# CSS动画的两种做法 

## transition

过渡

### 作用

补充中间帧

### 语法

- transition：属性名 时长 过渡方式 延迟
- 过渡方式：linear线性|ease| 不重要的属性需要时自查文档



### 注意

不是所有属性都能过渡

- display:none => block 不能过渡
- 要实现让一个东西从能被看见到消失的过渡动画一般用visibility:hidden => visible

- background颜色可以过渡
- opacity透明度可以过渡不过不推荐



## animation

### 声明关键帧

```css
@keyframes identifier{
  0% {top:0;left:0;}
  30%{top:50px;}
  68%,72%{left:50px;}
  100%{top:100px;left:100%;}
}
```

### 添加动画

在需要添加动画的选择器中添加

```css
animation:时长|过渡方式|延迟|次数|方向|填充模式|是否暂停|动画名;
```

- 时长：s或ms
- 过渡方式：跟transition取值一样

- 次数：数字或infinite无限次
- 方向：reverse反方向|alternate来回

- 填充模式：none|forwards保持最后一个属性值|backwards应用开始属性值|both向前和向后填充模式都被应用。

- 是否暂停：paused|running

  

# visibility和display的区别 

1. 是否继承：

   ​	display不继承，visibility继承。父元素visibility值为hidden，子元素不可见，如果子元素单独给visibility赋值为visible则可见；元素的display属性设为none则整棵子树不可见。

2. 是否占据空间：`display:none` 渲染时如同不存在，`visibility:hidden` 虽然看不见，但是其占据的空间会被白色占位。

3. 属性值变化后是否重新渲染：display:none渲染，visibility :hidden不渲染；。
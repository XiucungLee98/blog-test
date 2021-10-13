# 表达式和语句

语句（statement）是为了完成某个任务进行的操作，可以看成是将要执行的某个动作，一般不需要返回值，语句的结束标志为分号。表达式（expression）是为了得到返回值，一定会返回一个值。

# 标识符的规则

标识符是用来识别各种值的名称，最常见的标识符有变量名、函数名等。JS的变量名对大小写敏感，标识符的第一个字符可以是Unicode字母（中文也行）、$或者_，第一个除外的其他字符还可以用阿拉伯数字。

# if else语句
当指定条件为真，if 语句会执行一段语句。如果条件为假，则执行另一段语句。
多层 if...else 语句可使用 else if 从句。注意：在 Javascript 中没有 elseif （一个单词）关键字。
```javascript
if (判断条件) {
  // 满足条件时，执行的语句
} else {
  // 不满足条件时，执行的语句
}
```

# while for语句

While语句包括一个循环条件和一段代码块，只要条件为真，就不断循环执行代码块。

```javascript
while (条件) {
  语句;
}

// 或者
while (条件) 语句;
```

for语句是循环命令的另一种形式，可以指定循环的起点、终点和终止条件。它的格式如下。

```javascript
for (初始化表达式; 条件; 递增表达式)
  语句

// 或者

for (初始化表达式; 条件; 递增表达式) {
  语句
}
```

for语句后面的括号里面，有三个表达式。

- 初始化表达式（initialize）：确定循环变量的初始值，只在循环开始时执行一次。
- 条件表达式（test）：每轮循环开始时，都要执行这个条件表达式，只有值为真，才继续进行循环。

- 递增表达式（increment）：每轮循环的最后一个操作，通常用来递增循环变量。

## 死循环陷阱

```javascript
while(a!==1){
console.log(a)
a=a+0.1
}
//Q：是不是死循环？
/*A：是。原本的逻辑是循环9次之后a等于1就跳出循环，但是因为浮点数不精确，a不精确等于1，一直执行下去。*/
```

## for循环递增表达式的执行时间

```javascript
for (var i=0;i<5;i++){
	setTimeout(()=>{console.log(i)})
}
//Q:输出什么
/*A:输出5，5，5，5，5。可以看作是先写5句console.log()，但是里面的值暂时不填，因为setTimeout意思是过一会儿再执行，等for循环运行完毕，再把i的值填进这5句console.log()里面，这时i的值为5，所以输出5次5。*/
```

# break continue

break语句和continue语句都具有跳转作用，可以用来跳出循环。break结束循环，continue跳出本轮循环，返回循环结构头部继续执行下一轮循环。

# label

标签也就是定位符，用于跳转到程序的任意位置，有点类似HTML里面的锚点。格式如下：

```javascript
label:
	语句
```

标签通常与break语句和continue语句配合使用，跳出特定的循环。

## 通过标签跳出循环

### 配合break

```javascript
top:
  for (var i = 0; i < 3; i++){
    for (var j = 0; j < 3; j++){
      if (i === 1 && j === 1) break top;
      console.log('i=' + i + ', j=' + j);
    }
  }
```

在上面的双循环代码块中，break命令后面加上了top标签，判断条件为真时直接跳出双重循环，跳出top这个代码块。如果不加上top标签，就只能跳出内层循环，进入下一次的外层循环。

### 配合continue

```javascript
top:
  for (var i = 0; i < 3; i++){
    for (var j = 0; j < 3; j++){
      if (i === 1 && j === 1) continue top;
      console.log('i=' + i + ', j=' + j);
    }
  }
```

在上面的双循环代码块中，continue命令后面加上了top标签，判断条件为真时跳出当前循环，进入下一轮外层循环。如果不加上top标签，就只能进入下一轮内层循环。

## 通过标签跳出代码块

```javascript
foo:{
  console.log(1);
  break foo;
  console.log('本行不会输出');
}
console.log(2);
```

输出结果为

```javascript
1
2
```

标签配合break可以跳出代码块，跳过代码块中某些代码。



# 短路逻辑

### &&短路逻辑

```javascript
A&&B&&C&&D
```

&& 短路逻辑会取第一个假值或者D，并不会取 true 或者 false 。

### ||短路逻辑

```javascript
A||B||C||D
```

|| 短路逻辑会取其中一个真值或者D，并不会取 true 或者 false 。

# JS的设计缺陷

Javascript有一个自动修复机制——在程序可能有缺陷的时候，自动插入分号补全。

```javascript
return
{
    hello:"world"
};
在自动补齐时就会变成
return;
{
    hello:"world"
};
```

本意是返回一个对象，实际上返回了undefined。

所以return后面不能加回车。

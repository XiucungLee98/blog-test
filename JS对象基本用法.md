# 定义

键值对的集合，键是属性名，值是属性值。

# 声明对象的两种语法

```javascript
let obj = {'name':'lee','age':18} //简便写法
或者
let obj = new Object('name':'lee','age':18) //标准写法
```

# 细节

- 键名可以包括任何字符
- 引号可以省略，省略之后键名只能是标识符（不能以数字开头，不能是特殊字符）

- 就算引号省略了，键名也还是字符串
- Object.keys(obj)可以得到obj的所有key

- 变量名作属性名：

let p1='name'

let obj = {p1:lee}属性名为"p1"

let obj = {[p1]:lee}属性名为p1变量值，也就是"name"

- 除了字符串，Symbol也能当属性名

# 删除对象属性

- 仅删除属性值：`obj.name=undefined`
- 彻底删除属性：`delete obj.name`或者`delete obj.['name']`

- 检查是否删除成功：`'name' in obj`返回true则删除失败，false则删除成功

obj.xxx===undefined不能断定'xxx'是否为obj的属性，因为无论是obj没有xxx属性，还是obj有xxx属性但没赋值，obj.xxx都===undefined。

# 查看对象属性

- 查看自身所有属性 `Object.keys(obj)`
- 查看自身所有属性值`Object.values(obj)`

- 查看自身所有键值对`Object.entries(obj)`
- 查看自身+共有属性`console.dir(obj)`

- 判断对象是否拥有某个属性`'name' in obj`或`obj.hasOwnProperty('name')`

### 'name' in obj 和obj.hasOwnProperty('name')的区别

'name' in obj 查询包含原型的共有属性，而hasOwnProperty查询自有的属性

### 中括号语法和点语法的区别

- obj['key']是根据key这一字符串键查询值 
- obj[key]是根据key这个变量查询值，而变量对应的字符串不一定是我们想查询的键，容易出错

-  obj.key里面的key其实是字符串，不是变量，一定要注意 \

所以obj.name===obj['name'] 

obj.name!==obj[name] 

let name = 'lee'则obj[name]===obj['lee']

# 修改或增加对象属性

### 直接赋值

let obj = {name: 'lee'} // name 是字符串

obj.name = 'lee'  //name是字符串

obj['name'] = 'lee'

obj[name] = 'lee'   //name是变量，值不确定

obj['na'+'me'] = 'lee'

let key = 'name'; obj[key] =  'lee'

let key ='name'; obj.key = 'lee' //obj.key里面的key是字符串不是变量

### 批量赋值

Object.assign(obj, {age:18, gender:'man'})

### 修改共有属性

obj.__proto__['toString'] = 'xxx'   //不推荐

Object.prototype['toString'] = 'xxx'  

### 修改原型

不推荐使用__proto__

推荐使用Object.create

```javascript
let common = {kind: 'human'}
let obj = Object.create(common)
obj.name = 'lee'
```

![img](https://cdn.nlark.com/yuque/0/2021/png/22863141/1634197369207-c49a0937-a2a4-4c66-8da6-d64ee3b044db.png)

obj既有自身拥有的name属性，又有修改后的原型common的共有kind属性。
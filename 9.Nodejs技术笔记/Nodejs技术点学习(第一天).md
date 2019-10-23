# Nodejs技术点学习

## 第一天

### 1.nodejs的重点

- 了解后台开发干的事情
- 能够写出简单的接口，基本的增删改查
- 能够npm装包，引包，用包
- MySQL的学习增删改查

### 2.node.js的基本概念

- 基于Chrome v8引擎的JavaScript运行环境
- 服务端的js
- Chrome的js解析器叫v8引擎

### 3.运行环境

- 通过node.js也可以直接运行js代码，不需要通过浏览器运行，直接敲命令即可。

### 4.js的组成

- 浏览器端

	- ECMAScript：js语法，for循环/if/esle,var
	- DOM文档对象模型

		- 约定了操纵dome元素的语法

	- BOM浏览器对象模型

		- 操纵浏览器的语法
		- window.alert(); 打印弹出框
		- window.location.href设置浏览器地址
		- window.setTimeout一次性定时器

- 服务器端

	- ECMAScript：js基础语法，for循环，ifelse var
	- BOM语法中的一些常用api

		- 定时器，console。。。

	- 模块 （类似于之前用的jQuery、swiper轮播图插件）模块就是各种插件
下载才可以使用
node.js也有自带的模块，但是开发中一般用第三方中的多一些

### 5.node.js的基本使用
REPL read(读取)eval(解析)print(打印)loop(循环)

- lowB写法

	- 打开黑窗
	- 输入node回车
	- 写js代码回车运行
	- 循环步骤

- 工作用法

	- 创建一个.js文件
	- 内部有node.js支持的代码
	- 打开黑窗输入node 文件名 回车
	- 运行

- 注意：node 文件名  不允许写错
          node	文件名  文件名不需要全部手打，直接Tab就可以啦。
- 在vscode中也可以打开，Ctrl+~号，就可以打开终端

### 6.ES6基本概念

- ECMAScript 2015
- 2015年推出的新的语法规范
- 简称ES6
- ES6变化最大，新功能最多

### 7.声明变量的改变

- var关键字的缺点

	- 变量的提升：会把变量的声明提升到当前作用域的最顶端
	- 没有块级作用域
{
  var name = '张三'
}
console.log(name);//张三
在大括号的外部依然能访问到变量，也就是说使用var声明的变量没有块级作用域。
	- var声明的变量可以重复声明
var name = '张三';
var name = '李四';
var name = '王五';
console.log(name);--->王五
下面声明的同名变量会把上面声明的同名变量的值给覆盖掉。

- let  常量

	- 可以理解为var的替代者，学了let之后可以和var说拜拜了。。
	- let name = ‘Jack’；
console.log(name);
	- 没有变量的提升了。
	- 有块级作用域

		- {
   let skill = '不如跳舞';
}
console.log(skill);--->undefined

	- let声明的变量不能重复声明
	- let声明的变量可以改变值
例如：let name = '周杰伦';
          name = '杜国章';
console.log(name);--->杜国章

- const  变量

	- const  常量名 = xxx
	- 变量名在当前作用域不会提升
	- 有块级作用域
{
  const name = '周杰伦''
}
console.log(name);-->同样访问不到块级作用域中const声明的变量
	- 也不能重复声明同名变量
const name = '周杰伦';
const name = '杜国章';
这种方法是不对的。
	- 必须在声明时就要给变量赋值

- const和let的选择

	- 能用const不用let，能用let不用var
	- const是常量声明之后，不能重复修改，性能更高
	- 能用let不用const，能用const不用var
	- 工作中基本上是用const比较多的
let用的很少
var基本不用

### 8.终端命令

- cls  清屏  clear

### 9.ES6对象的简化写法

- 属性名要和键名一致才能简写
- const name = 'jack';
const age = 18;
const skill = '跳舞';
const person = {
  name：name,可以写成name
  name,
  age,
  skill,
  平时写法：
  jump:function(){
      console.log('扑通。。跳');
   }
  在ES6中是将function去除了
  jump() {
    console.log('扑通。。吧唧。。');
  }
}

### 10.ES6的模板字符串

- 格式：`${}`
- const smoke = '黑岩'
const data = {
  name: '李白',
  chaodai: '唐朝',
}
const temStr = `
        ${data.name}来自于${data.chaodai}
        疑是银河落${smoke}
        疑是银河落九天
        疑是银河落九天
        疑是银河落九天`;
console.log(temStr);
- 模板字符串可以换行，简单的内容可以直接使用模板字符串

### 11.函数默认值

- 早期使用的是短路运算来实现默认值的设置

	- // function hello(name, skill) {
//   // 早期对参数 的判断
//   // ||逻辑或，任何一个为真，就为真
//   // 
//   name = name || 'jack',
//     skill = skill || '跳水',
//     console.log(name + '你好！', skill);
// }
// hello();

- // es6中的默认值
// 参数=参数值

	- function hello(name = '路飞', skil = '橡胶果实') {
  console.log(name, skil);
}
hello('我爱罗', '后又跟');

### 12.ES6中的对象解构

- // 定义对象
const person = {
    name: '食欲之灵',
    desc: '教你做饭',
    spec: '事物越好吃，衣服越少',
  }
//   ES6中可以简写成
  //   快速获取对象的属性
  // 需要和对象中的属性名要同名
  // 没有想要的值的时候，会出现undefined
const { name, desc, spec } = person;
console.log(name, desc, spec);
- 对象的解构，使用频率挺高的。
- // 形参传一个对象类型
// 结合默认值，如果调用方法的时候不给方法传参，那么就使用默认值
function eat({ food1 = '黄瓜', food2 = '萝卜', food3 = '炒肝儿', food4 = '豆汁' }) {
  console.log(food1, food2, food3, food4);
}
// eat({
//   food1: '肉',
//   food2: '西蓝花',
//   food3: '蛋',
//   food4: '面条'
// });
eat({});

### 13.数组的解构

- 语法：
 const arr = ['喜洋洋', '灰太狼'];
// 数组的解构，获取的顺序，和数组的元素的对应关系是一致的
// 数组大部分时候都是通过下标来获取的
// 数组的解构用的不多，了解即可
const [c1, c2] = arr;
console.log(c1, c2);
- 用到的不多，了解即可

### 14.ES6-对象展开运算符  ...三个点儿

- // 对象
const person = {
  skill: '跳水',
  habbit: '抗冻',
}
const student = {
  sleep: '呼噜',
}
const son = {
  // 写到前面的同名属性会被下边儿的覆盖掉
  //   可以对多个对象进行赋值
  ...person,
  ...student,
  skill: '游泳',
}
console.log(son);

### 15.ES6-数组展开符

- // 直接将...数组放到新数组中即可         数组不会出现覆盖的问题，索引会依次向后增加，一直在后面追加
- const arr = ['跑步', '游泳', '跳水', '玩儿板', '滑板'];
const arr1 = ['长跑', '跑马拉松', '跑全马', '跑半马']
const sport = [...arr, ...arr1];
console.log(sport);

### 16.箭头函数
今天的重点

- 省略function，变为'=>' 
如果形参只有一个，可以省略小括号，
如果函数体，只有一行，可以省略大括号，
如果函数体只有一行，并且有返回值，省略大括号的同时，必须省略return
- 普通函数无法用箭头函数的方式化简
- 箭头函数只能化简匿名函数
- a=>a
const exam = function(a){
  return a;
}

### 17.箭头中的this

- 箭头函数中的this，在创建箭头函数的时候就确定了，
this指向的是上下文(和他平级的环境中)中的this
- // 箭头函数中的this指向的是谁
  const person = {
    name: '海尔兄弟',
    skill: '抗冻',
    jump() {
      // 指向的是对象person
      //   console.log(this);
      //   定时器中函数中的this指向的是window
      //   如果想要获取到person对象的话，需要在外边将this保存一下
      //   var that = this;
      //   window.setTimeout(function() {
      //     console.log(that);
      //   }, 1000)
      //   简写成箭头函数
      //   箭头函数中的this指向的是和它平级的环境中this，那么怎么理解这个平级环境呢，可以这么理解，就是在箭头函数上一行打印一下console.log(this)，这个this指向的谁，那么箭头函数中的this指向的就是谁
      //   所以，在这里，console.log(this)指向的是person，所以，箭头函数中的this指向的就是person
      console.log(this);
      window.setTimeout(() => console.log(this), 100);
    }
  }
  person.jump();

### 18.ES6中的内置模块

- fs模块

	- // 声明一个常量fs
// require('fs')意思：导入fs模块，赋值给常量fs
const fs = require('fs');
// 声明一个常量fs
// require('fs')意思：导入fs模块，赋值给常量fs
// data:是读取的结果
// err：如果读取失败，保存的是错误信息
	- 读文件
// 声明一个常量fs
// require('fs')意思：导入fs模块，赋值给常量fs
// data:是读取的结果
// err：如果读取失败，保存的是错误信息
const fs = require('fs');
fs.readFile('./lai.txt', 'utf-8', (err, data) => {
  console.log(err);
  console.log(data);
})
	- 写文件
const noval = `
    静夜思
锄禾日当午
汗滴禾下土
谁知盘中餐
粒粒皆辛苦
`;
const fs = require('fs');
// writeFile()中的参数 1：地址 2:写入的内容  3.选项，可选的参数  4.回调函数
fs.writeFile('./go.txt', noval, err => {
  console.log(err);
});

### 19.node.js第三方模块

-  npm 官方下包网站
- 找包
- 下包
- 引包
- 用包

## 第二天

## 第三天

## 第六天

## 第五天

## 第四天

*XMind: ZEN - Trial Version*
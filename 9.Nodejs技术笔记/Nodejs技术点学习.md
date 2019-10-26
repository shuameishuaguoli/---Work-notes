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
	- 没有块级作用域概念
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

- let  变量

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

- const  常量

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
	- 必须在声明变量是就要给变量赋值

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
// });--->传了形参打印的就是传入的实参的值。
eat({});--->不传实参的话，输出的就是默认值

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
数组展开符中若有对个数组的话，并且数组中的元素会有重复元素的话，相同的元素并不会覆盖掉，而是依次向后添加。

### 16.箭头函数
今天的重点

- 普通函数简化箭头函数的规则：
省略function，变为'=>' 
如果形参只有一个，可以省略小括号，
如果函数体，只有一行，可以省略大括号，
如果函数体只有一行，并且有返回值，省略大括号的同时，必须省略return
- 普通函数无法用箭头函数的方式化简
- 箭头函数只能化简匿名函数
- const exam =a=>a这种写法其实是这种写法的语法糖
const exam = function(a){
  return a;
}

### 17.箭头中的this

- 箭头函数中的this，在创建箭头函数的时候就确定了，
this指向的是上下文(和他平级的环境中)中的this
箭头函数在创建的时候就已经确定了。
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
      console.log(this);---->this指向的是person
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
 参数1：是需要写入的文件
    参数2：是需要写入的内容
    参数3：默认值是utf-8
    参数4：回调函数
fs.writeFile('./go.txt', noval, err => {
  console.log(err);
});

### 19.node.js第三方模块

-  npm 官方下包网站
- 找包
- 下包
- 引包
- 用包
- fivicon错误是浏览器再找图标

## 第二天

### 1.补充的终端的命令： cd ../  跳出当前文件夹
cd ./文件夹  进入文件夹
mkdir 文件名
这是一个命令，创建文件夹的命令

### 2.nodejs读取文件：
node.js中的相对路径是相对的是： 终端中的路径或者小黑窗中所处的路径

### 3.为了避免终端找不到路径，我们可以使用绝对路径来解决这个问题，但是不提倡使用绝对路径。

### 4.nodejs中的绝对路径中的全局变量，这里是两个下划线_ _
__dirname--->定义到当前这个js文件所处的文件夹的绝对路径
__filename--->定义到当前这个js文件的绝对路径

### 5.Path模块基本使用（也是内置模块）

- path.join([...paths])--->括号中必须是字符串
把多个路径拼接到一起，保证正确
const filepath = path.join('info','novel','01.txt');
info\novel\01.txt
- const filepath = path.join(__dirname,'./novel/01.txt');
- path与文件fs模块结合使用

	- // 导入路径包
const path = require('path');
// 导入文件包
const file = require('fs');
// 生成路径
const fallpath = path.join(__dirname, './files/01.du.txt');
// 读取文件
file.readFile(fallpath, 'utf-8', (erro, data) => {
  if (erro == null) {
    console.log(data);
  } else {
    console.log(erro);
  }
});

- 路径拼写的时候不要写错，一定是这种/斜杠，多个路径之间的拼接用逗号“，”分割

### 6.http模块--创建服务器
也是内置模块
关闭服务器是Ctrl+c
这种服务器统一叫静态资源服务器

- 导包
const http = require('http');
- 创建服务器对象
const server = http.createServer(function(request,response){
    //  content-type内容类型
    //  text/plain 普通文本
    //  text/html  HTML结构
    //  charset=utf-8编码格式
    response.setHeader('content-type','text/plain;charset=utf-8');
   //返回内容
   response.end('how old are you!');--->响应英文的话直接写就行
   response.end('在你面前他平时总是乐乐呵呵');
});
- 开启服务器  开启监听
参数1：端口号
参数2：监听地址，省略的话就是本机
参数3：开启之后的回调函数
server.listen(8848,function(err){
   if(err==null){
      console.log('服务已开启!');
   }else{
      console.log('哎呀失败了');
    }
});
- 概念解释

	- 端口

		- 物理端口

			- usb口
			- 网线口
			- 耳机口
			- hdmi显示器，投影仪接口

		- 虚拟端口

			- 电脑中的软件和外部通讯的通道
			- 只要和外部通讯的软件，都会使用某一个虚拟端口
			- 一个号而已，0开始递增
			- 虚拟端口很多
			- 前10000端口号一般有很多被占用了

	- 子主题 2

### 7.http模块获取用户请求的url地址

- 创建服务器对象
const server = http.createServer(function(request,response){
    //content-type内容类型
    //text/plain 普通文本
    //charset=utf-8编码格式
    response.setHeader('content-type','text/plain;charset=utf-8');
   //返回内容
   response.end('how old are you!');--->响应英文的话直接写就行
   response.end('在你面前他平时总是乐乐呵呵');
   console.log(request.url);--->可以获取用户请求的地址后面的请求参数英文
   console.log(decodeURI(request.url));--->可以获取请求参数中的汉字
});

### 8.根据不同的url来做不一样的逻辑

### 9.http模块--读取HTML文件并返回

- 导入模块http开启服务器
导入模块 fs 读取服务
导入模块 path 生成路径 
- 开启服务
http.createServer(request,response)=>{

})
- 开启监听

### 10.如果静态资源中图片格式的话，那么就不要设置编码格式了utf-8了

### 11.http://localhost
     http://127.0.0.1
这两种方式都是访问的是自己电脑，只能是自己访问自己电脑的时候可以简写这种ip地址

### 12.用户发送的请求时git还是post请求

- request：请求
request.method--->获取用户的请求方式GET/POST
request.url--->获取用户的请求参数

### 13.第三方模块使用步骤

- 第一步：新建文件夹(不要中文)，
第二步初始化，打开终端输入：npm init -y或者npm init自行输入
第三部：npm网站找包，下包，导包，用包  npm i express

### 14.express模块框架

- 第二天会讲

### 15.补充  nodemon这是一个自动启动服务器的小工具，只要保存文档就会自动开启服务器，比较方便。
直接 npm i nodemon 安装

### 16.readFile()中的utf-8为什么可以省略？
     HTML页面中有utf-8这个字段，浏览器可以识别到
     对于非文本类的文件，浏览器绝大多数都可以自动的推断出类型，
     使用对应的方式去解析，所有当页面中图片格式的文件的时候，readFile()这个方法中的utf-8就不用写了。
     学名叫嗅探，加载之前先嗅嗅。。

## 第三天

### 1.express基本使用

- 1.// 导包
const express = require('express');
// 创建服务器对象
const app = express();

//路由
app.get('/', function(req, res) {
  res.send('Hello World 你好世界')
});
// 开启服务器
app.listen(3000, err => {
  if (!err) {
    console.log('服务已开启');
  }
});

### 2.运行在小黑窗中
nodemon 文件名
nodemon这个功能只能是在gitbash环境下运行

### 3.实现静态资源服务器的功能

- // 导包
const express = require('express');
// 创建服务器对象
const app = express();

// 实现静态资源服务器功能
app.use(express.static('public'));
// 开启服务器
app.listen(3000, err => {
  if (!err) {
    console.log('服务已启动');
  }
});
- app.use(express.static('public'));
这个public也是可以动态改变的，但是一般是比较建议在代码的同级目录下边儿
添加public这个文件夹，这样是方便管理的。

### 4.路由的概念

- get请求

	- 语法

		- 路由是url和后台逻辑/函数的对应关系
app.get()是注册路由的步骤
app.post()
		- // get方式的请求接口书写
app.get('/login', (request, response) => {
  const arr = ['西红柿', '菜花炒肉', '花菜炒豆角'];
  response.send(arr);
});
		- 获取随机笑话
// get方式的请求接口书写
app.get('/joke', (req, res) => {
  const arr = ['我是笑话1', '我是笑话2', '我是笑话3', '我是笑话4', '我是笑话5'];
  const suiji = parseInt(Math.random() * 5);

  console.log(suiji);
  res.send(arr[suiji]);
});

	- 读取外部的一个文件

		- JSON.parse();--->JSON字符串转数组类型。
		- JSON.strfiy();--->数组类型转字符串
		- // 导包
const express = require('express');
// 导包
const fs = require('fs');
// 导包
const path = require('path');
// 创建服务器对象
const app = express();

// get方式的请求接口书写
app.get('/joke', (req, res) => {
  //   声明一个数组
  const arr = ['笑话1', '笑话2', '笑话3', '笑话4', '看着路世界真滴大', '于是啥子人都有'];
  // 获取一个随机数
  var suiji = parseInt(Math.random() * arr.length);
  //   响应一个随机笑话
  res.send(arr[suiji]);
});


// 获取随机的笑话
app.get('/suijixiaohua', (req, res) => {
  // 获取路径
  var all_path = path.join(__dirname, './data/jokes.json');
  // 读取文件
  fs.readFile(all_path, 'utf-8', (erro, data) => {
    if (erro == null) {
      // 读取成功
      // 读取出来的data的默认类型是JSON类型的字符串，我们要将这个字符串转成数组
      var arr = JSON.parse(data);
      //   获取一下随机数
      var suiji = parseInt(Math.random() * arr.length);
      //   响应请求
      res.send(arr[suiji]);
    } else {
      // 读取失败
      console.log(erro);
    }
  });
});

// 实现静态资源服务器功能
app.use(express.static('public'));
// 开启服务器
app.listen(3000, err => {
  console.log(err);
  if (!err) {
    console.log('服务已启动');
  }
});

	- get请求参数的获取

		- get请求的数据都存到了在query属性中
request.query.属性名进行获取响应的数据
并且是以对象的方式进行了存储
		- 注意：

			- 1.当涉及到参数传递时，
后台接口在实现的时候需要
接收数据
处理数据
返回数据

- post请求

	- post请求方式

		- post路由的注册方法和get类似，就是将get改成post即可
请求方式默认接不到请求数据
		- 测试的时候：
可以通过postman这个软件发送post请求
		- 默认注册的post路由中无法获取到提交过来的参数（数据）
		- 中间件是一个特殊的第三方模块
必须结合express才能可以使用
类似和jQuery插件必须要结合jQueryjs使用
		- 中间件 body-parser  的使用步骤

			- 下包  npm i body-parser
			- 引包    // 导入中间件包
const bodyParser = require('body-parser');
			- 用包    // 解析post请求中的数据
app.use(bodyParser.urlencoded({ extended: false }))

	- 通过中间件获取到上传文件

		- 也是使用中间件来获取
express-fileupload中间件叫这个
下包：npm i express-fileupload
		- 导包
const fileUpload = require('express-fileupload');
		- 使用中间件 接收文件
app.use(fileUpload());
		- 使用postman软件来测试的时候，需要选择body下的第二个form-data
		- 使用了中间件之后可以使用request.files获取到文件的信息
files中使用对象属性的方式，保存了上传的文件信息
		- 把文件移动到某个文件夹中
request.files.xxx.mv(路径)

## 第六天

## 第五天

## 第四天

### 数据库

*XMind: ZEN - Trial Version*
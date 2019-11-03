# Vue.JS基础部分学习

## 第一天

### 1.初识Vue

- 1.Vue是什么

	-  构建用户界面的JavaScript框架
	- 模仿angular框架开发的
类似于angular
	-  可以用来构建SPA应用程序
SPA （Single web application） 
单页面应用程序
	- CDN：加速  缓存技术

- 2.Vue的特点

	- MVVM

		- 特点：数据驱动视图
		- Model
		- View
		- ViewModel
		- 面向数据

	- 组件化

- 3.Vue的优缺点

	- 上手简单
	- 简单的API
	- 轻量高效
	- 灵活的组件系统
	- 强大的生态系统 

		-  Vue Router
		- Vues
		- 等等一系列的系统

	- 开源
	- 号称屌丝福音

- 4.可以做什么

	-  一切和Web用户界面相关的都可以使用Vue来做
	- 对SEO没要求的应用
	- 更加侧重于单页面应用程序(SPA)开发
	- 单产品型的应用程序
	-  桌面应用程序
和其他技术想配合
纯Vue是写不出来的
	-  管理系统
	- 混合APP
	- 移动APP

- 5.一些资源

	- 官方文档
	- 官方仓库
	- 不要买书
	- 分支主题

- 6.Vue可以和jQuery库和其他类库使用

### 2.安装Vue

- 下包
npm  i  vue
在用 Vue 构建大型应用时推荐使用 NPM 安装
Vue的核心只关注视图层 el部分就是视图层，视图层也叫模板层
data叫数据或者叫模板
- 初识Vue

	- 第一步：npm i  Vue

		- 第二步：script标签引进来
<script src="../node_modules/vue/dist/vue.js"></script>
		- 第三步：每一个Vue程序都是以new Vue()开始的
<div id="app">
    <h1>{{ 1 + 1 }}</h1>
    <h1>{{ foo }}</h1>
  </div>
<script>
     new Vue({
	    //   el告诉Vue的启动入口节点在哪里或者理解成哪一部分归Vue管
	    el: '#app',
	    data: {
	       foo: 'bar',
	      }
      })
</script>
		- 第四步：每一个Vue实例都是接收一个选项对象用来配置Vue应用
		- 第五步：选项的el属性，用来告诉Vue的启动入口节点
凡是入口节点中的所有节点就可以使用Vue的语法了可以理解成Vue是高级的模板引擎
		- 第六步：Vue中的模板对象数据是通过data选项来指定
		- 注意：el不能挂载到html和body元素，只能是挂载一个普通元素，所以一般我们的页面一开始就来一个div#app  el的值可以是CSS选择器，但是建议选择id选择器，如果选中了多个标签，那么只对第一个生效，el的值也可以是DOM节点，例如：
el:document.querySelectorAll('div')[1];
只不过这种方式很少用

	- Vue中的属性值如果是布尔值时，一般如果不写的话，那么默认为true，但是v-show这个属性有些特殊，v-show的默认值是false
例如：<p v-show/v-show="">看着路世界真滴大</p>--->默认值是false
所以一般在工作中，我们不应该过渡依赖默认值，所以我们使用属性的时候都要给定值。
	- 要想将数据展示到标签内部我们可以使用v-text和{{mag}}这两种方式都可以
v-text其实封装的是js中的innertext属性，v-text是专门对文本进行绑定的
<p v-text="msg"></p>--->浏览器不闪，为什么这么写不闪呢，因为这个v-text是写到标签中的属性，所以浏览器不会闪一下。
或者
<p id="pp">{{msg}}</p>--->加载的时候浏览器会闪烁一下，因为浏览器是从上到下记性加载的，先指向HTML标签中的内容，在执行Vue中的逻辑代码。所以才会浏览器加载的时候会闪一下。
js：
new Vue = ({
   el:'#dd',---视图
   data:{
       msg:'我是一个p标签',
   }
})
标签中的属性值是通过Vue对象中的data属性进行操作的。

### 3.数据绑定

- 生么是数据绑定：
模型中的数据与视图的对应关系就是数据绑定。
- v-bind是专门对属性进行绑定的
v-text是专门对文本进行绑定的
- Vue只关注v-开头的属性，不是以v-开头的就默认是标准属性，不归Vue管理
- v-bind:title='title'--->v-bind是对属性的绑定
例如：<p v-bind:title="title">{{title}}</p>
new Vue({
    el: '#app',
    data: {
      title: '我是一只小青龙',
    }
  })
F12中显示的是：
<p title="我是一只小青龙">我是一只小青龙</p>
title起到的作用是鼠标放上去显示对内容的解释
- v-bind:style = "{}"--->v-bind：style这个数据绑定比较特殊，接收的是一个  对象类型
<p v-bind:style="{color:'red,height:123px,'}">这是一段带文字的段落</p>
属性和属性之间用逗号分开，但是我们很少使用这种方式写
- 我们一般使用这种方式
<p v-bind:style="styleObject">这是一段带文字的段落</p>  
new Vue({
   data:{
        styleObject:{  --->一定要写到data中，因为data是管理数据的
                      color:'red',
                      background：'blue',
              }
    }
})
- v-bind:class 语法也是比较特殊的，同样接收一个   对象类型   ，对象的属性为真实存在的类名，对象的值为布尔类型 如果为true则添加属性对应的类名，如果为false，则不添加属性。这里的这个dome就是一个真实存在的一个类名例如：                              style中写.dome{color:pink}
<p v-bind:class="{dome:false/true}">这是一段带文字的段落</p>
<p :class="{dome:false/true}">这是一段带文字的段落</p>--->还可以简写
将v-bind省略掉
- 总结：
:class
:style
这两个属性后面接收的都是一个对象类型  ：冒号表示属性
- p{{list[0]}}p
data:{
   list:[html,css,js]
}
- p{{user.name}}{{user.age}}p或者p{{user['my-sex']}}p
data:{
  user:{
    name:'小明',
    age:18,
    my-sex:'男'
  }
}

### 4.事件的绑定

- 语法：v-on:click="回调函数"
v-on：click、change、blur、fouce
- new Vue({
  //Vue提供的专门定义方法的参数  methods
  //也可以定义事件函数的回调
  methods:{
      clicked：function(){},
   },--->方法和方法之间用逗号隔开
   in:function(){}
})
- v-on可以删掉用@符号代替
@事件名称=“回调函数”
-  // 回调函数写到methods里面，里面还是可以传参数的，js中参数怎样传，这里面就怎样传
<input type="text" @focus="fac" @blur='blu' />
methods: {
      fac: function() {
        console.log('获取到了焦点');
      },
      blu: function(me) {
        console.log(me + '失去了焦点');
      }
    }
- 当事件被触发时，可以将事件对象以参数形式传递，$event在vue中是具有特殊函数的内容，在这里表示事件对象$event表示事件对象
<input type="text" @focus="fac($event)" />

	- <div id="app">
    <input type="text" @focus="click(a,$event)">
    <a href="#" @click="clicks(b,$event)">来吧点我一下</a>
  </div>
</body>
<script src="./js/vue.js"></script>
<script>
  new Vue({
    el: '#app',
    data: {
      a: 10,
      b: 20,
    },
    methods: {
      click: function(a, e) {
        console.log('我是一只小青龙');
        console.log(a, e);
      },
      clicks: function(b, e) {
        console.log("我被点了");
        console.log(e, b);
        // 超链接点击之后，改变当前被点击的DOM节点的颜色
        e.target.style.background = 'blue';
        e.target.style.color = 'yellow';
      }
    }
  });
</script>

- Vue中的冒泡机制

	- 在vue中通过修饰符来解决事件执行时的一些特殊逻辑问题，如组织冒泡
如获取按键信息，这些都是通过事件修饰符来获取；
	- 语法是：
在事件名称后添加一个   .    点，即为修饰符
v-on:事件名. 修饰符=“函数”;
@click.stop = "函数";--->阻止冒泡机制的语法
	- @keyup.13 = "send"/@keyup.shift.enter = "send"
回车的keycode是13   .shift.enter是回车+shift同时按下

### 5.响应式的数据绑定

- 实例化对象  可以直接访问模型中的数据
var vm  = new Vue({
  data:{
    msg:'数据初始化',
   }
});
console.log(vm.msg);
- methods:中的this指向的是vm实例（实例对象）
- 实例对象vm不但可以直接访问模型(data)中的数据，还可以访问methods中的方法

### 6.双向数据绑定(比较重要)

- 要实现数据双向绑定，必须要有form表单元素相结合
- <input type="text" v-model="text">
v-model就能获取到用户输入的信息

	- <div id="app">
    <input type="text" v-model="text">
    <h1>{{text}}</h1>
  </div>
</body>
<script src="./js/vue.js"></script>
<script>
  var vm = new Vue({
    el: '#app',
    data: {
      text: '',
    },
  });
</script>

- data中定义了属性，methods中就不能定义与data中的属性相同的方法
- methods中定义的方法不允许使用箭头函数
- v-model是将视图的数据流向模型
v-text，v-html是将模型中的数据流向视图

### 7.结构

- v-if  先写
v-else-if  再写
v-else  最后写

	- <p v-if="age<18">我小于18</p>
    <p v-else-if="age>18">我大于18</p>
    <p v-else>我等于18</p>  --->最后这个v-else不需要再写值了

- 工作中使用v-show而不使用v-if
如果使用频率一直是显示隐藏显示隐藏，那么我们就使用v-show 这个方法是在标签中加了属性 display=none  所以节点还是在的
如果将dom节点删掉再也不出现，那么我们就使用v-if
- 遍历数组
v-for=“key in arr”
<li v-for="key in arr">key</li>
<li v-for="（item,index） in arr">{{index}}-{{item}}</li>

### 8.input事件

- 只要一输入内容的时候就触发了这个事件，输入内容的过程中就是一直在触发这个事件

### 9.关键字

- in
- delete

## 第二天

## 第三天

## 第四天

*XMind: ZEN - Trial Version*
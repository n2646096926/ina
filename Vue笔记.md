# **Vue笔记**

## 一、vue安装

**命令行工具**

```
1.查看版本 npm
	npm -v
2.升级npm版本
	cnpm install npm -g
3.升级或安装cnpm
	npm install cnpm -g
4.全局安装
	cnpm install --global vue-cli
5.创建一个基于webpack模板的新项目
	vue init webpack 项目名
6.运行项目
	cd 项目名    //进入项目
	npm install //安装
	npm run dev //运行项目  或者npm start
7.访问项目
	localhost:8080
```

## 二、vue起步

### **1，实例化vue**

> 每个 Vue 应用都需要通过实例化 Vue 来实现。
>
> 语法格式如下：

```
const vm = new Vue({
  // 选项
})
```

> vue中的参数：
>
> ​	el ：是DOM元素中的ID 
>
> ​	data ：定义数值属性
>
> ​	methods ：用于定义函数，可以通过return返回函数值
>
> ​	computed ：计算属性，处理复杂逻辑
>
> ​	{{ }} ：用于输出对象属性和函数返回值

### **2，实例属性与方法**

> ​	实例属性与数据属性的区别在于  **实例属性前有前缀$**
>
> ```
> document.write(vm.$data==data)
> ```

### **3，计算属性**computed

> 关键词：computed

computed 提供的函数用作属性vm.messagefunction的**getter**,依赖于vm.message

```
computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
```



> **computed  vs methods**
>
> 效果是一样的，但是computed是基于依赖缓存，只有相关依赖发生改变时才会重新取值，methods则是在重新渲染时，函数会重新调用执行。

### **4，监听属性watch**

watch  -----响应数据的变化

```
watch : {
        kilometers:function(val) {
            this.kilometers = val;
            this.meters = this.kilometers * 1000
        },
        meters : function (val) {
            this.kilometers = val/ 1000;
            this.meters = val;
        }
    }
```



### **5，事件处理器**methods

**v-on**直接接受方法调用

```
<button v-on:click="greet">Greet</button>
```

```
methods: {
    greet: function (event) {
      // `this` 在方法里指当前 Vue 实例
      alert('Hello ' + this.name + '!')
      // `event` 是原生 DOM 事件
      if (event) {
          alert(event.target.tagName)
      }
    }
```

内联javaScript语句

```
<div id="app">
  <button v-on:click="say('hi')">Say hi</button>
  <button v-on:click="say('what')">Say what</button>
</div>
 
<script>
new Vue({
  el: '#app',
  methods: {
    say: function (message) {
      alert(message)
    }
  }
})
</script>
```

#### **a.事件修饰符**

|         v-on:click.stop         |                  阻止单击事件冒泡                  |
| :-----------------------------: | :------------------------------------------------: |
|     **v-on:submit.preven**      |                提交事件不再重载页面                |
|   **v-on:click.stop.prevent**   |                   修饰符可以串联                   |
| **v-on:click.capture**="doThis" |          添加事件侦听器时使用事件捕获模式          |
|  **v-on:click.self**="doThat"   | 只当事件在该元素本身（而不是子元素）触发时触发回调 |
|  **v-on:click.once**="doThis"   |                  事件只能点击一次                  |

#### **b.按键修饰符**

v-on：click可以简写为@click

按键别名：

- `.enter`
- `.tab`
- `.delete` (捕获 "删除" 和 "退格" 键)
- `.esc`
- `.space`
- `.up`
- `.down`
- `.left`
- `.right`
- `.ctrl`
- `.alt`
- `.shift`
- `.meta`

```
//示例
<p><!-- Alt + C -->
<input @keyup.alt.67="clear">
<!-- Ctrl + Click -->
<div @click.ctrl="doSomething">Do something</div>
```

### 6，样式绑定

 **v-bind** 来设置样式属性 class与style

>  v-bind:class 设置一个对象，从而动态的切换 class: 
>
> ```
> <div v-bind:class="{对象：属性}"></div>
> ```
>
> 绑定返回对象的计算属性 
>
> ```
> <div id="app">
>   <div v-bind:class="classObject"></div>
> </div>
> --------------------------------------------------
> new Vue({
>   el: '#app',
>   data: {
>     isActive: true,
>     error: {
>       value: true,
>       type: 'fatal'
>     }
>   },
>   computed: {
>     classObject: function () {
>       return {
>       	base: true,
>         active: this.isActive && !this.error.value,
>         'text-danger': this.error.value && this.error.type === 'fatal',
>       }
>     }
>   }
> })
> ```
>
>  **v-bind:style** 直接设置样式 
>
> ```
> <div id="app">
>     <div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }">菜鸟教程</div>
> </div>
> ```
>
> 直接绑定到一个样式对象 
>
> ```
> <div id="app">
>   <div v-bind:style="styleObject">菜鸟教程</div>
> </div>
> ```
>
> 

## 三、传值


























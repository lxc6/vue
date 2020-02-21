## Vuejs

* 目前就是Vuejs的天下, 这是目前三大框架中最简单的 最容易上手的一个框架

半个月 大一个月的时间  完全的control

* 安装   本地引用/ npm  ,目前 先用本地安装的形式

* hello world   1 创建视图 2  引入vuejs  3  实例化 vue 4  设置选项 el /data 5 在视图上写data中的变量

* Vue实例的选项 

  * el => vue实例所管理的视图  id选择器/class选择器/
  * data  =>  响应式数据 => 数据变化  => 视图就会变化  => vm.属性  = 值 等价于 vm.$data.属性
  * methods =>  所有的方法 都在methods中定义, methods 方法的this指向vm实例  this.属性 this.方法
  * methods中 方法 不能以箭头形式出现例如

      ```js
  methods: {
      fn: () => {
          // this就不再是 vm实例
      },
      fn () {
         // this 指向vm实例
      }
  }
      ```

  > 插值表达式 =>  {{  表达式 }}  => 纯变量  / 运算 / 方法调用 / 三元  => 不能写关键字 if /else/var 

  * 如果在插值表达式中 对 list进行操作 可能会造成 死循环, 通过摆脱对原数组的引用

  >指令 => 在标签里 带 v-前缀的属性 就是指令

  v-text  =>  将表达式内容赋值给 元素的innerText

  v-html => 将表达式的值 赋值给元素的innerHTML属性

* 条件渲染 v-if / v-show   => 有何区别 ? 

* v-if   都是通过对表达式的布尔值 判断 决定元素的显示或者隐藏

* v-show 都是通过对表达式的布尔值 判断 决定元素的显示或者隐藏

v-if 决定一个元素 是删除 还是增加 

v-show 决定一个元素的css的样式 是否隐藏

## vuejs 的指令 v-on

* v-on 可以注册事件 

 v-on:事件名.修饰符 = '方法名'

> 简写  @事件名="方法名"

**修饰**符可以不写  once /prevent

事件参数    @事件名="方法名"  => 第一个参数 就是event 

@事件名="方法名($event)"  => 传值的方式传入event 

## v-for 循环列表/对象

* 循环数组

v-for= "item in items "

> 循环生成谁就在谁的标签上写v-for

v-for= "(item,index) in items "

* 循环对象

v-for= "item in items "  =>item指的是 {  key:value } => value

v-for="(value,key, index) in items"

* v-for 养成写key的习惯 

更新数组 => vuejs需要比较前后的节点 => 每个节点一个标记 => 每个循环项 需要一个key属性

key属性在当前的列表中需要唯一, 一般可以用index 下标 或者id

## v-bind 和 v-model



v-bind 动态绑定属性用的 

v-bind:属性="表达式" => 简写 :属性="表达式"

v-bind:class =>  对象 / 数组数组

v-bind:class=" { class名称: 布尔值  }" => 布尔值true => class名称就会被应用 false,就不用

v-bind: style =>  对象/数组 =>  font-size => fontSize(小驼峰)



v-model => 双向绑定 =>  数 => 视图  视图  => 数据 

v-model="data中的变量"

v-model =>v-bind 和 v-on 组合得出的效果

v-model =>  input/textarea/checkbox

checkbox (布尔值) => 单个用法   多个checkbox => (数组) => 每个checkbox一个value值 标明每个input的标记

radio => 给每个input一个value值 ,标明所代表的意思

以上在实战中,用得比较少,因为项目 中都是用 成熟的框架 =>  elementUI

多个

## vue基础选项/指令

* v-cloak => 闪烁

* v-once => 首次渲染

* v-pre  => 跳过渲染

  

 ## Vue的过滤器

  vue过滤器 是为了改变数据的显示格式 

  并不会对**`原数据`**进行修改  日期/货币/大小写

  全局  => Vue.filter(名称, function(value){})

  局部 =>  filters: {  过滤器名称: function(){} }

  全局  => 所有实例都可用

  局部 => 只有当前实例可用

  {{ 表达式 | 过滤器 | 过滤器2(123)  }}

  串联 /传参

## 自定义指令 /ref操作dom

自己定义指令

全局  Vue.directive(指令名: {})

局部  dirtectives: {  指令名: {} }

{

// 会在指令作用的元素创建之后执行 执行一次

inserted(dom, option){

},

//  是指令对应的表达式发生变化的时候执行

update (dom, option) {

}

 }

ref  操作dom 

可以给你标签一个ref属性 

this.$refs.属性名 获取dom对象

## 计算属性

* 当我们遇到复杂 的运算结果要显示在页面上的时候 
* 可以用计算属性来封装 
* 计算属性 不用写 () 调用形式
* 计算属性有缓存机制 => 智能更新 (vuejs内部实现) => 性能优于方法



